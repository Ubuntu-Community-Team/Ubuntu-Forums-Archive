---
title: "Writing to serial port"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by Blatm on 2011-07-18
Hi,

I'm new to linux, running ubuntu 11.04 64bit, and I have an external hardware device* I'd like to communicate with through a serial port connection (through a usb/serial converter) using c code. However, it seems like I'm having trouble writing to it. The code I'm using was downloaded from [here]("http://www.astro.louisville.edu/software/xmccd/index.html") (./optec/setifw.c and ./optec/getifw.c) and is written specifically for what I want it to do.

The first time I tried the code (without modifying anything), the code seemed to hang. By adding in some printf statements I found that the problem was in opening the connection. I changed the port from /dev/ttyUSB0 to /dev/ttyS0 and fixed that problem, but had problems writing (which is what this post is asking about).

I tried again a few days later, and after some fiddling I got the programs to work pretty much as intended, but oddly enough the fresh download (the one I talk about above which would hang) would also work.

I tried again the next day, and I was back to my original problem (I always kept an unmodified version of the code handy, and on days 1 and 3 it didn't work, but on day 2 it did).

The relevant part of the original code is (and it's a lot to go through, so feel free to skip over it, but I include it here for completeness. I point out what I think are the specific problem lines in just a bit):

```
int ConnectOptecFilter(void)
{
  struct termios tty;
  char sendstr[32]; 
  char returnstr[32];
  char filterport[32];
  int numRead;
  
  DisconnectOptecFilter();
  
  /* Make the connection */

  strcpy(filterport,FILTERPORT);
  FilterPortFD = open(filterport,O_RDWR); //filterport = "/dev/ttyUSB0"
  if(FilterPortFD == -1)
  {
    fprintf(stderr,"The filter wheel serial port not available ... \n");
    return(0) ;
  }
  
  /* Set the port attributes for 1900 baud, 8 bits, no parity */
  
  tcgetattr(FilterPortFD,&tty);
  cfsetospeed(&tty, (speed_t) B19200);
  cfsetispeed(&tty, (speed_t) B19200);
  tty.c_cflag = (tty.c_cflag & ~CSIZE) | CS8;
  tty.c_iflag =  IGNBRK;
  tty.c_lflag = 0;
  tty.c_oflag = 0;
  tty.c_cflag |= CLOCAL | CREAD;
  tty.c_cc[VMIN] = 1;
  tty.c_cc[VTIME] = 5;
  tty.c_iflag &= ~(IXON|IXOFF|IXANY);
  tty.c_cflag &= ~(PARENB | PARODD);
  tcsetattr(FilterPortFD, TCSANOW, &tty);

  /* Flush the input (read) buffer */

  tcflush(FilterPortFD,TCIOFLUSH);
  
  /* Send WSMODE command to establish communications */
  
  strcpy(sendstr,"WSMODE\r");
  writen(FilterPortFD,sendstr,7);
  usleep(1000000);
  numRead=readn(FilterPortFD,returnstr,1,2);
  
  if ( returnstr[0]!='!' )
  {
    writen(FilterPortFD,sendstr,7);
    usleep(1000000);
    numRead=readn(FilterPortFD,returnstr,1,2);
    if ( returnstr[0]!='!' )
    {
      return(0);
    } 
  }
             
  FilterConnectFlag = TRUE;
      
  /* Flush the input buffer in case there is something left from startup */

  tcflush(FilterPortFD,TCIOFLUSH);

  return(1);
}

static int writen(fd, ptr, nbytes)
int fd;
char *ptr;
int nbytes;
{
  int nleft, nwritten;
  nleft = nbytes;
  while (nleft > 0) 
  {
    nwritten = write (fd, ptr, nleft);
    if (nwritten <=0 ) break;
    nleft -= nwritten;
    ptr += nwritten;
  }
  return (nbytes - nleft);
}

static int readn(fd, ptr, nbytes, sec)
int fd;
char *ptr;
int nbytes;
int sec;
{
  int stat;
  int nleft, nread;
  nleft = nbytes;
  while (nleft > 0) 
  {
    stat = telstat(fd,sec,0);
    if (stat <=  0 ) break;
    nread  = read (fd, ptr, nleft);

/*  Diagnostic */    
    
/*    printf("readn: %d read\n", nread);  */

    if (nread <= 0)  break;
    nleft -= nread;
    ptr += nread;
  }
  return (nbytes - nleft);
}

```The original problem was with the line

```

  FilterPortFD = open(filterport,O_RDWR); //filterport = "/dev/ttyUSB0"

```But it doesn't hang anymore after changing filterport to "/dev/ttyS0".

The device is configured so that when it is sent "WSMODE" it returns "!". However, changing the code so that it prints the returned string, I got nonsense every time (stuff like P&#65533;R*&#65533; ). I commented the bit of code that would break if the return wasn't "!", and later commands which are supposed to get a response of "*" get the same returned string (e.g. P&#65533;R*&#65533; again).

I changed the writen command   writen(FilterPortFD,sendstr,7);  (here sendstr is "WSMODE\r") to

```

  nwrite = write (FilterPortFD, sendstr, 7);
  printf("nwrite = %d \n", nwrite);

```and found that nwrite = -1, which corresponds to "nothing was written".

I also made a file with just "WSMODE\r" in it (called WSMODE), and tried

```

blatm@Bob:~$ cat WSMODE > /dev/ttyS0
cat: write error: Input/output error
blatm@Bob:~$ cat WSMODE > /dev/ttyUSB0
^C

```ttyS1, ttyS2, ttyS3, and ttyS4 all behave the same way ttyS0 does, and the ^C indicates that I wasn't getting any response.


So, does anyone know what the problem might be, and how to fix it?



*The device I'm trying to get working is the controller for an [optec IFW](http://www.optecinc.com/astronomy/catalog/ifw/ifw.htm).

---

### Post by lkraemer on 2011-07-18
For more information on your USB to Serial Converter:

**DETECT THE DEVICE - USB**
Open a Linux Terminal window and cut/paste the following commands with
the USB to Serial Adapter unplugged from a USB port.
```

dmesg | tail
lsusb

```

larry@ubuntu:~$ dmesg | tail
[10797.964432] domain 0: span 03
[10797.964434] groups: 01 02
[10797.964436] domain 1: span 03
[10797.964438] groups: 03
[10797.964440] CPU1 attaching sched-domain:
[10797.964441] domain 0: span 03
[10797.964443] groups: 02 01
[10797.964446] domain 1: span 03
[10797.964447] groups: 03
[12071.044928] usb 6-1: USB disconnect, address 3

larry@ubuntu:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Then plug in the USB-Serial Port adaptor to one of your USB ports. (REMEMBER to ALWAYS use this same port for when using your ODBII Scanner)
Wait for about 15 seconds, then cut and paste the following command in our Linux Terminal Window:
```

dmesg | tail
lsusb

```

You should see these messages.
larry@ubuntu:~$ dmesg | tail
[10797.964440] CPU1 attaching sched-domain:
[10797.964441] domain 0: span 03
[10797.964443] groups: 02 01
[10797.964446] domain 1: span 03
[10797.964447] groups: 03
[12071.044928] usb 6-1: USB disconnect, address 3
[12091.200574] usb 6-1: new full speed USB device using uhci_hcd and address 4
[12091.358706] usb 6-1: configuration #1 chosen from 1 choice
[12091.363887] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: This device cannot do calls on its own. It is no modem.
[12091.363914] cdc_acm 6-1:1.0: ttyACM0: USB ACM device

My device is /dev/ttyACM0

larry@ubuntu:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Now, cut and paste the following command in your Linux Terminal Window:
```

lsusb -v -d 058f:9720

```

Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 2 Communications
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 8
idVendor 0x058f Alcor Micro Corp.
idProduct 0x9720 USB-Serial Adapter
bcdDevice 0.00



**LINKING the COMM PORT: SYMBOLIC vs HARD**
To locate the possible COMM PORTS in Ubuntu, cut and paste the following commands with the USB to RS-232C Adapter plugged in.:
```

ls -l /dev/ttyS*
ls -l /dev/ttyU*

```

Notice that ttyS0 through ttyS3 are detected as shown. You may have
/dev/ttyUSB0 if it was properly detected. Mine was NOT, because it
was a Sabrent SBT-USC1M USB to Serial Converter..

crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3

I couldn't make a symbolic link work, so I decided to create a
hard link, replacing /dev/ttyS3. First remove /dev/ttyS3.
I'd suggest you try a Symbolic link first, then a Hard link if
the Symbolic doesn't work.
```

sudo rm /dev/ttyS3
sudo ln -s /dev/ttyACM0 /dev/ttyS3

```

For a Hard Link use:   sudo ln /dev/ttyACM0 /dev/ttyS3
REMEMBER to REMOVE the Symbolic Link first.

Running the command again:
```

ls -l /dev/ttyS*

```
gives:
crw-rw---- 1 root dialout 4, 64 2010-11-10 11:59 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2010-11-10 11:59 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2010-11-10 11:59 /dev/ttyS2
crw-rw---- 2 root dialout 166, 0 2010-11-10 12:59 /dev/ttyS3
If you don't have rw priviledges remove /dev/ttyS3 and create it again.

We can determine the Baud rate of the Port.  Use
```

man stty

```
for more information.

Find the Baud Rate:
```

stty -F /dev/ttyS3 -a

```

and to change it to 9600:
```

stty -F /dev/ttyS3 9600
stty -F /dev/ttyS3 -a

```

If you connect to a modem for testing you can transmit out an "ATZ"
causing the Modem to flash the lights and reset with:
```

echo ATZ > /dev/ttyS3

```

Which proves characters routed to /dev/ttyS3 get sent to /dev/ttyACM0,
the USB to Serial Converter.  Or if the Serial Adapter is a DTE Type
(Pin 2 = TX) you can jump Pin 2 to Pin 3 and have the characters echo
back on the RX Pin.

Maybe this information will help.  Once you get it transmitting out the Serial Port just change
your C Code to use the linked /dev/ttySx port.

Let me know how it goes.................

lk

---

### Post by Blatm on 2011-07-20
Thanks for the long reply and sorry for the delay.

As far as I can tell, the device should be working fine through the ttyUSB0 port. Here are the outputs of all the stuff you suggested, with just the converter plugged in (not the device at the other end):

Nothing plugged in:

```

blatm@Bob:~$ dmesg | tail
[  271.428456] usbcore: registered new interface driver usbserial_generic
[  271.428463] usbserial: USB Serial Driver core
[  271.452029] USB Serial support registered for pl2303
[  271.452694] pl2303 2-1.1:1.0: pl2303 converter detected
[  271.454468] usb 2-1.1: pl2303 converter now attached to ttyUSB0
[  271.454494] usbcore: registered new interface driver pl2303
[  271.454497] pl2303: Prolific PL2303 USB to serial adaptor driver
[  350.403087] usb 2-1.1: USB disconnect, address 4
[  350.403323] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[  350.403348] pl2303 2-1.1:1.0: device disconnected
blatm@Bob:~$ lsusb
Bus 002 Device 003: ID 04f2:b18d Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Converter plugged in:

```

blatm@Bob:~$ dmesg | tail
[  271.452694] pl2303 2-1.1:1.0: pl2303 converter detected
[  271.454468] usb 2-1.1: pl2303 converter now attached to ttyUSB0
[  271.454494] usbcore: registered new interface driver pl2303
[  271.454497] pl2303: Prolific PL2303 USB to serial adaptor driver
[  350.403087] usb 2-1.1: USB disconnect, address 4
[  350.403323] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[  350.403348] pl2303 2-1.1:1.0: device disconnected
[  452.887917] usb 2-1.1: new full speed USB device using ehci_hcd and address 5
[  452.999797] pl2303 2-1.1:1.0: pl2303 converter detected
[  453.001861] usb 2-1.1: pl2303 converter now attached to ttyUSB0
blatm@Bob:~$ lsusb
Bus 002 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 003: ID 04f2:b18d Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```

blatm@Bob:~$ lsusb -v -d 067b:2303

Bus 002 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2303 PL2303 Serial Port
  bcdDevice            3.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)

```
```

blatm@Bob:~$ ls -l /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 2011-07-20 10:57 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2011-07-20 10:57 /dev/ttyS1
crw-rw---- 1 root dialout 4, 74 2011-07-20 10:57 /dev/ttyS10
crw-rw---- 1 root dialout 4, 75 2011-07-20 10:57 /dev/ttyS11
crw-rw---- 1 root dialout 4, 76 2011-07-20 10:57 /dev/ttyS12
crw-rw---- 1 root dialout 4, 77 2011-07-20 10:57 /dev/ttyS13
crw-rw---- 1 root dialout 4, 78 2011-07-20 10:57 /dev/ttyS14
crw-rw---- 1 root dialout 4, 79 2011-07-20 10:57 /dev/ttyS15
crw-rw---- 1 root dialout 4, 80 2011-07-20 10:57 /dev/ttyS16
crw-rw---- 1 root dialout 4, 81 2011-07-20 10:57 /dev/ttyS17
crw-rw---- 1 root dialout 4, 82 2011-07-20 10:57 /dev/ttyS18
crw-rw---- 1 root dialout 4, 83 2011-07-20 10:57 /dev/ttyS19
crw-rw---- 1 root dialout 4, 66 2011-07-20 10:57 /dev/ttyS2
crw-rw---- 1 root dialout 4, 84 2011-07-20 10:57 /dev/ttyS20
crw-rw---- 1 root dialout 4, 85 2011-07-20 10:57 /dev/ttyS21
crw-rw---- 1 root dialout 4, 86 2011-07-20 10:57 /dev/ttyS22
crw-rw---- 1 root dialout 4, 87 2011-07-20 10:57 /dev/ttyS23
crw-rw---- 1 root dialout 4, 88 2011-07-20 10:57 /dev/ttyS24
crw-rw---- 1 root dialout 4, 89 2011-07-20 10:57 /dev/ttyS25
crw-rw---- 1 root dialout 4, 90 2011-07-20 10:57 /dev/ttyS26
crw-rw---- 1 root dialout 4, 91 2011-07-20 10:57 /dev/ttyS27
crw-rw---- 1 root dialout 4, 92 2011-07-20 10:57 /dev/ttyS28
crw-rw---- 1 root dialout 4, 93 2011-07-20 10:57 /dev/ttyS29
crw-rw---- 1 root dialout 4, 67 2011-07-20 10:57 /dev/ttyS3
crw-rw---- 1 root dialout 4, 94 2011-07-20 10:57 /dev/ttyS30
crw-rw---- 1 root dialout 4, 95 2011-07-20 10:57 /dev/ttyS31
crw-rw---- 1 root dialout 4, 68 2011-07-20 10:57 /dev/ttyS4
crw-rw---- 1 root dialout 4, 69 2011-07-20 10:57 /dev/ttyS5
crw-rw---- 1 root dialout 4, 70 2011-07-20 10:57 /dev/ttyS6
crw-rw---- 1 root dialout 4, 71 2011-07-20 10:57 /dev/ttyS7
crw-rw---- 1 root dialout 4, 72 2011-07-20 10:57 /dev/ttyS8
crw-rw---- 1 root dialout 4, 73 2011-07-20 10:57 /dev/ttyS9
blatm@Bob:~$ ls -l /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2011-07-20 11:04 /dev/ttyUSB0

```
/dev/ttyUSB0 seems to be acting properly. I then made a symbolic link between /dev/ttyUSB0 and /dev/ttyS3 (I mv'd /dev/ttyS3 instead of rm'ing it):

```

blatm@Bob:~$ sudo mv /dev/ttyS3 ~
blatm@Bob:~$ sudo ln -s /dev/ttyUSB0 /dev/ttyS3
blatm@Bob:~$ ls -l /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 2011-07-20 10:57 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2011-07-20 10:57 /dev/ttyS1
crw-rw---- 1 root dialout 4, 74 2011-07-20 10:57 /dev/ttyS10
crw-rw---- 1 root dialout 4, 75 2011-07-20 10:57 /dev/ttyS11
crw-rw---- 1 root dialout 4, 76 2011-07-20 10:57 /dev/ttyS12
crw-rw---- 1 root dialout 4, 77 2011-07-20 10:57 /dev/ttyS13
crw-rw---- 1 root dialout 4, 78 2011-07-20 10:57 /dev/ttyS14
crw-rw---- 1 root dialout 4, 79 2011-07-20 10:57 /dev/ttyS15
crw-rw---- 1 root dialout 4, 80 2011-07-20 10:57 /dev/ttyS16
crw-rw---- 1 root dialout 4, 81 2011-07-20 10:57 /dev/ttyS17
crw-rw---- 1 root dialout 4, 82 2011-07-20 10:57 /dev/ttyS18
crw-rw---- 1 root dialout 4, 83 2011-07-20 10:57 /dev/ttyS19
crw-rw---- 1 root dialout 4, 66 2011-07-20 10:57 /dev/ttyS2
crw-rw---- 1 root dialout 4, 84 2011-07-20 10:57 /dev/ttyS20
crw-rw---- 1 root dialout 4, 85 2011-07-20 10:57 /dev/ttyS21
crw-rw---- 1 root dialout 4, 86 2011-07-20 10:57 /dev/ttyS22
crw-rw---- 1 root dialout 4, 87 2011-07-20 10:57 /dev/ttyS23
crw-rw---- 1 root dialout 4, 88 2011-07-20 10:57 /dev/ttyS24
crw-rw---- 1 root dialout 4, 89 2011-07-20 10:57 /dev/ttyS25
crw-rw---- 1 root dialout 4, 90 2011-07-20 10:57 /dev/ttyS26
crw-rw---- 1 root dialout 4, 91 2011-07-20 10:57 /dev/ttyS27
crw-rw---- 1 root dialout 4, 92 2011-07-20 10:57 /dev/ttyS28
crw-rw---- 1 root dialout 4, 93 2011-07-20 10:57 /dev/ttyS29
lrwxrwxrwx 1 root root       12 2011-07-20 11:31 /dev/ttyS3 -> /dev/ttyUSB0
crw-rw---- 1 root dialout 4, 94 2011-07-20 10:57 /dev/ttyS30
crw-rw---- 1 root dialout 4, 95 2011-07-20 10:57 /dev/ttyS31
crw-rw---- 1 root dialout 4, 68 2011-07-20 10:57 /dev/ttyS4
crw-rw---- 1 root dialout 4, 69 2011-07-20 10:57 /dev/ttyS5
crw-rw---- 1 root dialout 4, 70 2011-07-20 10:57 /dev/ttyS6
crw-rw---- 1 root dialout 4, 71 2011-07-20 10:57 /dev/ttyS7
crw-rw---- 1 root dialout 4, 72 2011-07-20 10:57 /dev/ttyS8
crw-rw---- 1 root dialout 4, 73 2011-07-20 10:57 /dev/ttyS9

```
I set the baud rate to 19200 because that's what my device calls for (though my code does this anyway)

```

blatm@Bob:~$ stty -F /dev/ttyS3 -a
speed 19200 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^A; eol = <undef>;
eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread -clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr -icrnl -ixon -ixoff
-iuclc -ixany -imaxbel -iutf8
-opost -olcuc -ocrnl -onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
-isig -icanon -iexten -echo -echoe -echok -echonl -noflsh -xcase -tostop -echoprt
-echoctl -echoke

```When I try and run my code, with either filterport = /dev/ttyUSB0 or /dev/ttyS3, it can't open the device, i.e. it can't get past the line

```

FilterPortFD = open(filterport, O_RDWR);

```Which was my initial problem. Maybe since then I've been trying to write to serial devices that don't exist.

Again, thanks for the help, but I'm still having problems unfortunately.

---

### Post by wep940 on 2011-07-20
Just a crazy idea, but.....since really you are communicating with a converter through a USB port, perhaps you should be using the calls from libusb.  This lib gives everything needed to open, close, read from, write to and status a USB device.  It's possible that the character strings you are seeing are binary being returned through the USB interface.  I have some sample code for libusb calls if you'd like to peruse, and if you install libusb-dev there should be documentation there as well.

---

### Post by Blatm on 2011-07-20
Sure, I'm happy to try libusb. I've installed libusb-dev. I think seeing your code would be more useful to me than looking through the manual, so I'd very much appreciate if you could post/send me some of your code.

---

### Post by lkraemer on 2011-07-20
Since /dev/ttyUSB0 is detected you shouldn't have to make a symbolic link
or hard link.  So, I'd remove them.  Next I'd suggest, as I did previously,
to connect an External Serial Modem and see if you can RESET the Modem.
another thing you could do is to install wvdial, and use it to send characters
out the serial port to verify that works.  By using wvdial you can connect the TX
Pin to the RX pin and loop the TX characters back to wvdial to prove it is functional. 

When that all is functional, then I'd look at the debug info in the
source.tar.gz.......:
```

To compile and save errors:

make 2>&1 > errors.txt

or just to see the errors

make 2 > errors.txt

```
Do you have any compile errors?
Are you using Mono, Eclipse, or just gcc?

I assume you did a cd /path/to/source for the make, with the Linux Headers and build-essential installed,
along with any other library's you need included.
```

pwd
cd ~/xmccd-3.1.0
make clean
make
sudo make install

```

lk

---

### Post by Blatm on 2011-07-20
> **lkraemer said:**
> Since /dev/ttyUSB0 is detected you shouldn't have to make a symbolic link
or hard link.  So, I'd remove them.  Next I'd suggest, as I did previously,
to connect an External Serial Modem and see if you can RESET the Modem.
another thing you could do is to install wvdial, and use it to send characters
out the serial port to verify that works.  By using wvdial you can connect the TX
Pin to the RX pin and loop the TX characters back to wvdial to prove it is functional. 


I know very little about serial cables, so I don't understand what you're suggesting I do with wvdial. I'll go look into it right now.

I don't know of any modems around, but I'll ask people who would know when I get the chance and let you know if that works.

> 
When that all is functional, then I'd look at the debug info in the
source.tar.gz.......:
```

To compile and save errors:

make 2>&1 > errors.txt

or just to see the errors

make 2 > errors.txt

```Do you have any compile errors?
Are you using Mono, Eclipse, or just gcc?

I assume you did a cd /path/to/source for the make, with the Linux Headers and build-essential installed,
along with any other library's you need included.
```

pwd
cd ~/xmccd-3.1.0
make clean
make
sudo make install

```lk

I have no compile errors. I'm using gcc. I made clean, etc., but I still have the same problem. I'll try some more stuff (including the debug stuff) in a little bit.

Again thanks for being so helpful.

---

### Post by lkraemer on 2011-07-20
Your Serial cable is most likely a DB25 or DB9 connector.

The DB25 Pinout is as follows:
[http://pinouts.ru/SerialPorts/Serial25_pinout.shtml](http://pinouts.ru/SerialPorts/Serial25_pinout.shtml)
On the DB25 is you jump TX Pin to RX Pin everything you send out the Serial
Port will be echoed back.  So, if you are in wvdial you should see the
characters echo back.

If you have a DB9 the Pinout is as follows:
[http://pinouts.ru/SerialPorts/Serial9_pinout.shtml](http://pinouts.ru/SerialPorts/Serial9_pinout.shtml)
In wvdial you should see also the characters echo back.

That proves the RS-232 Port is functional and you just need to debug
the C code after this.

If you get no compile errors, don't worry about the debug messages.

lk

---

### Post by Blatm on 2011-07-22
I don't have any modems available, but I managed to control a different device from a different computer with the same cable, so the cable is not broken.

It might be a problem with how my computer deals with the cable, but I can use USB keys just fine. Right now I'm trying to see if I can control the device I'm interested in with another computer, but I don't have many permissions with that computer, so the code isn't working there right now, returning a "The filter wheel serial port not available ...", which corresponds to open("/dev/ttyUSB0", O_RDWR) == -1.

I'll try and find another computer to run the code, but the cable isn't broken.

I installed wvdial but I couldn't figure out how to use it to check whether or not my adapter was working despite googling both that specific example and more general things about wvdial. I likely just missed something, of course.

---

### Post by spegru on 2011-07-25
Hi I just tried this for the first time (mint10 - based on Ubuntu 10.10)
Maybe beginners luck but it worked almost first time

1. Plugged in the usb/serial adaptor
2. checked lsusb - sure enough there it was
Bus 002 Device 009: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
3. checked dmesg and got
usb 2-4.3: pl2303 converter now attached to ttyUSB0
So it was clear that it's connected as port named ttyUSB0
4. fired up gtkterm and selected Configuration>Port
5. Selected ttyUSB0 from the list and chose the correct paramaters for the box I was connecting to (usually 8bit, 1 stop bit and no parity). I was surprised with garbage at first but then discovered the preferred bit rate/ baud (for the L2 switch router I was interested in) was 115200 rather than the default 9600. 
All working fine now!

---

### Post by Blatm on 2011-07-28
The cable I'm using works on other computers for different purposes, but this code still doesn't work on other computers with the same cable.

When I try gtkterm, I get
```

Control signals read: Input/output error

```repeating two or three times a second in the terminal and nothing displayed on gtkterm.

I've contacted the author of the code I'm using, and he tells me he uses the code without problems and that perhaps my USB to serial converter is incompatible with the hardware. I don't know why at some point it was working then.

---

### Post by lkraemer on 2011-07-28
To help you.....we need information returned.....and so far you haven't
told us a thing about your hardware.

You have a DB9 or DB25 Connector on your Cable.  I'm assuming the
USB to Serial has a DB9 connector with Male Pins.  If you install gtkterm
and then then remove the symbolic links you previously made, because your
/dev/ttyUSB0 device was actually detected as such, you can setup gtkterm
for /dev/ttyUSB0 and then set the proper Baud, Parity, etc.

Then try jumpering Pin 2 to Pin 3 on the DB9 and type some characters on
your keyboard.  You should see them echo.  That proves everything is working
through to the DB9 RS-232C Connector.  The remaining cable to your device is
the only thing you need to verify along with the Receiving port connector's
wiring.  That should be in your documentation.

The DB25 Pinout is as follows:
[http://pinouts.ru/SerialPorts/Serial25_pinout.shtml](http://pinouts.ru/SerialPorts/Serial25_pinout.shtml)


The DB9 the Pinout is as follows:
[http://pinouts.ru/SerialPorts/Serial9_pinout.shtml](http://pinouts.ru/SerialPorts/Serial9_pinout.shtml)

lk

---

### Post by spegru on 2011-10-06
In fact I don't even bother with dmesg or lsusb any more. I just plug in the adaptor and start gtkterm. Since the usb is the only one called anything like that in the port list, I just select it and it works. Job done!

---


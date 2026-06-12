---
title: "Mini-Howto: Using your HTC Touch phone as a USB Wireless Modem in Ubuntu"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by ariel on 2008-05-03
**Mini-Howto: using your  HTC Touch (CDMA - EVDO, P3050) cellular phone or PDA as a wireless modem via USB**

This guide has been written for Ubuntu 8.04 but should work in all variants and other distros as well (you may need to install the wvdial package though, which ubuntu installs by default).  The main source of information for this post is [this guide for ASUS eee / xandros]("http://forum.eeeuser.com/viewtopic.php?pid=53155").

[B]
> [/B]Before connecting the USB cable, turn on the mobile phone and set it in "Wireless Modem" mode (don't forget to hit "Start"); you can do this from the "Cube" > "Comm Manager" or by navigating the phone menus: Start > Programs > then scrolling down to the "**WModem**" app icon and launching it, and then clicking "Start" from the menu.

**> **Now, connect the device with the USB cable

**> **Wait for a few seconds and then run:
   ```
sudo lsusb -v 
```  and look for the "[COLOR=Blue]Generic Serial[/COLOR]" device; note down the Vendor and ProdID info.

```
T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
[COLOR=Blue]P:  Vendor=0bb4 ProdID=0b03 Rev= 0.00[/COLOR]
S:  Manufacturer=Generic Manufacturer (PROTOTYPE--Remember to change idVendor)
S:  Product=[COLOR=Blue]Generic Serial[/COLOR]
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 3 Cls=02(comm.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=  64 Ivl=32ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=02(comm.) Sub=ff Prot=ff Driver=(none)
E:  Ad=84(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=05(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

```> In my case, the key information is: Vendor=0bb4 ProdID=0b03

**> **Now let's load the module that will make the device appear as a serial port to the kernel
   ```
sudo /sbin/modprobe ipaq vendor=0x0bb4 product=0x0b03
```   If you now check dmesg, you will see a line that looks like:```
 [ 3161.461769] usb 4-1: PocketPC PDA converter now [COLOR=Blue]attached to ttyUSB0[/COLOR]
```   Which means you are OK up to this point.


   Note: to have this_ done automatically on boot_, edit /etc/rc.local and add in it  (don't forget to replace the Vendor and Product IDs with your own):
    /sbin/modprobe ipaq vendor=0x0bb4 product=0x0b03
```
sudo gedit /etc/rc.local
```Which should then look like:
```
joe@doe:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/sbin/modprobe ipaq vendor=0x0bb4 product=0x0b03

exit 0
```**> **Edit the ppp configuration file:
  ```
sudo gedit /etc/ppp/options
```  In this file, comment out  the lines starting with 'lcp-echo-interval 30' and 'lcp-echo-failure 4'  to prevent ppp from disconnecting; you do this by adding a "#" character in the beginning of the line.


**> **Edit the dialer configuration:

   ```
sudo gedit /etc/wvdial.conf
```   Replace the contents with the following, noting first:
      - Phone: this line contains the access phone number, and varies from provider to provider. In Canada, NZ, and some US operators use #777
      - Username and Password: you need to get this from your provider; however, some operators do not use this information (mine, for example), they control access at the radio access layer;  
                               which means that you can use something any string as username and password, such as test / test.
      - Modem: this line has to match the the /dev/xxxxx device that you see showing up in dmesg after you plugged in your phone in wireless modem mode

```
   [Dialer Defaults]
   Init1 = ATZ
   Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
   Modem Type = USB Modem
   Phone = #777
   Modem = /dev/ttyUSB0
   Username = test
   Password = test
   Baud = 460800
   Idle Seconds = 0
   Carrier Check = no
   Stupid Mode = on
   FlowControl = NOFLOW
   Compuserve = 0
   Auto DNS = 1
```> To start using your wireless modem, open a terminal and launch [COLOR=Blue]wvdial[/COLOR], you should see something like the below (you must leave the terminal window open for the connection to stay up):

```
joe@doelaptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat May  3 12:14:58 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 11142
--> Using interface ppp0
```> Finally, if you are using networkmanager, you may have a default IP route pointing to your wlan or your wired ethernet (sometimes, if you were using wlan and then turn the wifi switch off, networkmanager does not remove the installed default route). If this is your case, you will notice that you can not ping google.ca (because your linux can't reach the DNS servers). The fix is very easy; open a terminal and type:

```
sudo ip route add default dev ppp0
```**> **That's it! now you should be able to browse the internet, connect your VPN, etc. My connection is quite good BTW, speetest.net shows me: 
   ```
Download: 1503 Kbps
   Upload: 103 Kbps
   Latency: 305 ms
```

---

### Post by surrendered on 2008-05-03
hi, thanks for the post, it's exactly what I've been looking for.
i'm pretty new to ubuntu, and i cant seem to get it to work.

the dmesg says PocketPC PDA converter now attached to ttyUSB0.

i followed the rest of the steps, but when i type wvdial at the terminal prompt, it says:

WvDial: Internet dialer version 1.60
Cannot open /dev/ttyUSB0: Device or resource busy

any ideas? thanks.

---

### Post by ariel on 2008-05-05
> **surrendered said:**
> hi, thanks for the post, it's exactly what I've been looking for.
i'm pretty new to ubuntu, and i cant seem to get it to work.

the dmesg says PocketPC PDA converter now attached to ttyUSB0.

i followed the rest of the steps, but when i type wvdial at the terminal prompt, it says:

WvDial: Internet dialer version 1.60
Cannot open /dev/ttyUSB0: Device or resource busy

any ideas? thanks.

Hi, please check your /etc/fstab

```
cat /etc/fstab
```

If you don't see a line like this one:

```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

(referring to /proc/bus/usb, the mode may change), then I suggest you to try adding that line at the bottom of your /etc/fstab. Be very careful because [COLOR=Red]this is a delicate configuration file[/COLOR], changing other stuff there can easily hose your system.

```
sudo gedit /etc/fstab
```

and then add at the bottom of the file:

```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

Then, reboot and try the steps above again.

Let me know if this fixes your issue, if so I will modify the howto.

---

### Post by surrendered on 2008-05-07
thanks for responding. 

when i used that code, and tried wvdial, i get
sending ATZ 
sending ATQ
re-sending ATZ
Modem not responding

also, when i did sudo lsusb, the device didn't show up, only my camera was listed.

---

### Post by ariel on 2008-05-08
> **surrendered said:**
> thanks for responding. 

when i used that code, and tried wvdial, i get
sending ATZ 
sending ATQ
re-sending ATZ
Modem not responding

also, when i did sudo lsusb, the device didn't show up, only my camera was listed.

The problem starts in lsusb. If you are not seeing the "Generic Serial" section in the lsusb output, then you can't possibly be finding the VendorID, ProdID numbers that you need to feed the ipaq kernel module with. Then wvdial can't send the modem commands out to the wireless modem.

Exactly what device are you using? Are you running the Wireless Modem application and starting it before you connect it to the pc?

---

### Post by surrendered on 2008-05-08
sorry I wasn't clear.
the device shows up in lsusb following your first set of instructions, but when i insert the code:
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
and i check lsusb again, the device is not there.

i have an HTC touch, and i set "phone as modem" although it just says "check usb cable", so i dont think it's actually connected, like how it works when i'm in xp.

---

### Post by ariel on 2008-05-09
> **surrendered said:**
> 
i have an HTC touch, and i set "phone as modem" although it just says "check usb cable", so i dont think it's actually connected, like how it works when i'm in xp.

two things I note:

- my phone never showed the 'check usb cable' message. Even if I hit start in the WModem app with no cable connected to the device, I get no error message. The only thing I see is that the "stop" menu option becomes available/enabled. So there might be a problem in that end.

- when checking dmesg after you plug in the device in modem mode, do you see a message like:

[ 3161.461769] usb 4-1: PocketPC PDA converter now [COLOR=Blue]attached to ttyUSB0[/COLOR]
or not?

---

### Post by DracoZA on 2008-05-16
My sudo lsusb looks nothing like yours so I am stuck at step 1.

nick@LAPTOP-NICK:~$ sudo lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 064e:a101 Suyin Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0bb4:0303 High Tech Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by ariel on 2008-05-17
> **DracoZA said:**
> My sudo lsusb looks nothing like yours so I am stuck at step 1.

nick@LAPTOP-NICK:~$ sudo lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 064e:a101 Suyin Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0bb4:0303 High Tech Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

My mistake, forgot the -v option:

```
sudo lsusb -v
```

Note that the "generic serial" usb device shows up only if you fire up the "Wireless Modem" app before connecting the HTC Touch to the computer.

---

### Post by surrendered on 2008-05-22
> **ariel said:**
> two things I note:

- my phone never showed the 'check usb cable' message. Even if I hit start in the WModem app with no cable connected to the device, I get no error message. The only thing I see is that the "stop" menu option becomes available/enabled. So there might be a problem in that end.

- when checking dmesg after you plug in the device in modem mode, do you see a message like:

[ 3161.461769] usb 4-1: PocketPC PDA converter now [COLOR=Blue]attached to ttyUSB0[/COLOR]
or not?

it does say it's attached. i'm getting "modem not responding." what should the settings be in the network manager in ubuntu?

---

### Post by ariel on 2008-05-22
> **surrendered said:**
> it does say it's attached. i'm getting "modem not responding." what should the settings be in the network manager in ubuntu?

Good! you are close now.

I'm guessing it's wvdial that says "modem not responding"... mind posting the full output of wvdial?

So the issue is possibly in wvdial.conf.

Can you also post the output of

cat /etc/wvdial.conf
and finally the full  dmesg output line that references ttyUSBxxx.

---

### Post by Newbie2000 on 2008-06-19
Sorry to drop in with an unrelated topic, but maybe you can help me with a pointer to the relevant info:

I have a HTC Touch and I want to upgrade the firmware from Linux.

Every search including HTC and Linux as keywords on Google and Yahoo brings pages about trying to install Linux on a HTC phone. Also I was not able to find what I want on xda-developers.com (maybe the info is there but I was not able to find it). Now I feel totally lost.

Do you have any ideea if it's possible to upgrade the HTC firmware from a Linux machine ?

Thanks in advance.

---

### Post by TomtheWombat on 2008-07-15
I also read that there is also a program called wm5storage that will mount your storage card as a usb device.

if you get synce working there are programs to access files, or you can install a gnomevfs extension to show your phone in nautilus.

---

### Post by rules on 2008-08-08
Hi ariel

Found your write-up but I can't get my HTC Touch to "dialup".

I get this when I try and run wvdial ...
afiq@rafiq-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

The device seems to mount without a problem ... lsusb ...
rafiq@rafiq-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0458:0066 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 0000:0000  
**Bus 001 Device 006: ID 0bb4:0b0c High Tech Computer Corp. **
Bus 001 Device 004: ID 03f0:1105 Hewlett-Packard ScanJet 5470c
Bus 001 Device 001: ID 0000:0000  


As for the first step, this is the info I found/used ... sudo lsusb -v ...
Bus 001 Device 006: ID 0bb4:0b0c High Tech Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         1 ?
  bDeviceProtocol         1 Microsoft ActiveSync
  bMaxPacketSize0        64
[B]  idVendor           0x0bb4 High Tech Computer Corp.
  idProduct          0x0b0c [/B]
  bcdDevice            0.00
  iManufacturer           1 HTC
  iProduct                2 Generic RNDIS
  iSerial                 3 3fbf5000-7351-0801-0406-c887c15c031b
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           62
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       239 Miscellaneous Device
      bInterfaceSubClass      1 ?
      bInterfaceProtocol      1 Microsoft ActiveSync
      iInterface              0 
      ** UNRECOGNIZED:  05 24 01 00 01
      ** UNRECOGNIZED:  04 24 02 00
      ** UNRECOGNIZED:  05 24 02 00 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

  


Any ideas??

Thanks.

---

### Post by ariel on 2008-08-09
Hi Rules, you don't seem to be launching thw WModem application (and then selecting "USB" and then hitting "Start") in the touch before connecting it to the PC and then starting to follow the howto.

When the WModem app is running, a few secs after connecting, doing "sudo lsusb -v" you should find the tring "Product=Generic Serial" in the entry of the HTC. 

Also when the WModem app is running properly the HTC shouldn't mount as a USB Mass Storage. 

BTW, I tested this with a new Touch w/ WM6.1 and still works fine.

---

### Post by rules on 2008-08-11
Hi ariel

I'm doing exactly what is described in your write-up.

I open "Internet Sharing" (this is a WM6 Touch), select USB click on connect and after a while I connect it to the cable. I just did this again and I still don't see anything that says "Generic Serial".

---

### Post by mentox on 2008-08-12
hi,

i have a htc kaiser and made all here wrote

but i dont get the generic serial only this one here:

```
Bus 005 Device 002: ID 0bb4:0303 High Tech Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         3 RNDIS
  bMaxPacketSize0        64
  idVendor           0x0bb4 High Tech Computer Corp.
  idProduct          0x0303 
  bcdDevice            0.00
  iManufacturer           1 HTC
  iProduct                2 Generic RNDIS

```

---

### Post by ariel on 2008-08-17
> **mentox said:**
> hi,

i have a htc kaiser and made all here wrote

but i dont get the generic serial only this one here:

```
Bus 005 Device 002: ID 0bb4:0303 High Tech Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         3 RNDIS
  bMaxPacketSize0        64
  idVendor           0x0bb4 High Tech Computer Corp.
  idProduct          0x0303 
  bcdDevice            0.00
  iManufacturer           1 HTC
  iProduct                2 Generic RNDIS

```

@mentox: the device is showing itself as RNDIS (windows activesync protocol) which may be implying that the WModem application was not "Started", RNDIS is the default connection mode (useless for us Linux users); when everything is OK (WModem app loaded and Start button hit), the computer should see the device as a USB Serial Port (and modem).

@rules: it seems that your device's firmware is different from mine and may be using a different "iProduct" string. If you post/attach the complete output of "sudo lsusb -v" we may be able to figure this out.

---

### Post by mentox on 2008-08-18
hi,

i have done in an other way :-)

similar to this here
[http://wiki.eeeuser.com/howto:install_synce_usb_rndis_lite_drivers](http://wiki.eeeuser.com/howto:install_synce_usb_rndis_lite_drivers)

with usb_rndis_lite ..

works great and stable ;-)

but thanks

greetings mentox

---

### Post by RoundTuit on 2012-07-05
ariel, Not sure if you're still on this board but wanted you to know your tutorial still ROCKS even now in 2012! I just followed it and my new oneiric server is happily talking to the Internet and world with my old HTC Mogul. A million thanks!!!:D

---

### Post by wildmanne39 on 2012-07-05
Thread is very old so it has been closed.

---


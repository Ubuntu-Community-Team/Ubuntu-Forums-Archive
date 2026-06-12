---
title: "Ubuntu 8.04.3 &amp; Crossover &amp; ScanTool.net v1.15"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by lkraemer on 2009-11-27
[B]How to enable USB-Serial Port adapter (RS-232) in Ubuntu 8.04.3 (Linux)
for the ELMSCAN5 Serial Version ODBII Code Reader.[/B]

[https://www.scantool.net](https://www.scantool.net)

[B]
REQUIRED SOFTWARE or try WINE[/B] ([http://www.winehq.org):](http://www.winehq.org):)
I started by Installing Crossover, then from the MENU, CROSSOVER -> INSTALL WINDOWS SOFTWARE
and created a Bottle in which to run SCANTOOL.NET for Windows v1.15
SCANTOOL.NET was installed and an ICON was placed on my Ubuntu 8.04.3 LTS (Long Term Support) Desktop

My Version was Crossover professional version 8.0.0 by Codeweavers
[http://www.codeweavers.com/](http://www.codeweavers.com/)

[B]
SERIAL PORT NAMES:[/B]
If you are wondering how the ttyUSB0 (ttyACM0) is related to a com port or how to set?

Dos/Windows use the COM name while the messages from the serial driver use ttyS00, ttyS01, etc.
Older serial drivers (2001 ?) used just tty00, tty01, etc.

The tables below shows some examples of serial device names. The IO addresses are the default addresses
for the old ISA bus (not for the newer PCI and USB buses).

    dos     common                  IO       USB-BUS ( ACM => acm modem )
    name     name     major minor address || common name      common name
    COM1   /dev/ttyS0  4,  64;   3F8      || /dev/ttyUSB0  |  /dev/ttyACM0
    COM2   /dev/ttyS1  4,  65;   2F8      || /dev/ttyUSB1  |  /dev/ttyACM1
    COM3   /dev/ttyS2  4,  66;   3E8      || /dev/ttyUSB2  |  /dev/ttyACM2
    COM4   /dev/ttyS3  4,  67;   2E8      || /dev/ttyUSB3  |  /dev/ttyACM3
     -     /dev/ttyS4  4,  68;   various

[B]
SERIAL PORT or USB Converter:[/B]
If you don't have a serial port on your Laptop, or want to use a USB port Converter
check out the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, modems, and the Serial ELMSCAN5.
[B]

SETUP UBUNTU (LINUX):[/B]
Open a Linux Terminal window and cut/paste the following commands with the
USB to Serial Adapter unplugged from a USB port.
```

dmesg | tail
lsusb

```
larry@ubuntu:~$ dmesg | tail
[10797.964432]  domain 0: span 03
[10797.964434]   groups: 01 02
[10797.964436]   domain 1: span 03
[10797.964438]    groups: 03
[10797.964440] CPU1 attaching sched-domain:
[10797.964441]  domain 0: span 03
[10797.964443]   groups: 02 01
[10797.964446]   domain 1: span 03
[10797.964447]    groups: 03
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

Then plug in the USB-Serial Port adaptor to one of your USB ports. (REMEMBER to ALWAYS
use this same port for when using your ODBII Scanner)  Wait for about 15 seconds,
then cut and paste the following command in your Linux Terminal Window:
```

dmesg | tail
lsusb

```
You should see these messages.
larry@ubuntu:~$ dmesg | tail
[10797.964440] CPU1 attaching sched-domain:
[10797.964441]  domain 0: span 03
[10797.964443]   groups: 02 01
[10797.964446]   domain 1: span 03
[10797.964447]    groups: 03
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
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x9720 USB-Serial Adapter
  bcdDevice            0.00
  .
  .
  .
  .
# I SKIPPED this next section, but included it for future reference...........
# Now we know the vendor id and the product id of the USB-Serial Port converter, this will enable us to
# load the linux kernel module &#8220;usbserial&#8221; to activate the device, like this :
#
# sudo modprobe usbserial vendor=0x4348 product=0x5523
#
# Run &#8220;dmesg&#8221; again and you shall see lines similar like this :
#
# usbserial_generic 1-1:1.0: generic converter detected
# usb 1-1: generic converter now attached to ttyUSB0
# usbcore: registered new interface driver usbserial_generic
#
# As you can see, the new serial port device is mapped to /dev/ttyUSB0. You can instruct Ubuntu to load this module
# automatically by include the line : &#8220;usbserial vendor=0×4348 product=0×5523&#8243; inside &#8220;/etc/modules&#8221; file.
#
#
#
# **EXTRA INFORMATION:** ( Found by searching with Google)
# NOTE:  ([http://ubuntuforums.org/archive/index.php/t-322770.html](http://ubuntuforums.org/archive/index.php/t-322770.html))
# I installed ubuntu to use a tool not included in windows, and linux is much better the last time I installed linux.
# I'm trying to work with a PL-2303X serial adaptar too, and came to this thread.
#
# Found this link [http://koti.mbnet.fi/lonnberg/pl2303x.html](http://koti.mbnet.fi/lonnberg/pl2303x.html), but my problem was not to link to /dev/ttyS0
# with the command ln -b /dev/ttyUSB0 /dev/ttyS0 The following patch modifies the driver for the Prolific
# PL-2303 USB-serial adapter to add support for the highly similar but incompatible PL-2303X adapter.
# The PL-2303X has the same vendor ID and product ID as the older PL-2303, which means that it will
# be incorrectly detected as a PL-2303 by the driver currently in the Linux kernel.
#
# Attempting to use a PL-2303X as a PL-2303 simply results in an inability to transfer data through the
# serial port.  In other words, nothing happens. This patch autodetects whether a PL-2303 or a PL-2303X
# is used and changes the initialization sequence accordingly.
#
# The PL-2303X can be distinguished from a PL-2303 by checking bMaxPacketSize0 for the device using
# lsusb -v -d 067b:2303 (as root). If bMaxPacketSize0 is 64, you probably have a PL-2303X and need this
# patch.The main kernel tree includes PL-2303X support starting from 2.6.8 (I can confirm that PL-2303X
# works on 2.6.11rc2 without my patch), making this patch unnecessary.
#
#
[B]

SYMBOLIC LINKING the COMM PORT:[/B]
To locate the possible used COMM PORTS in Ubuntu, cut and paste the following command:
```

ls -l /dev/ttyS*

```
Notice that ttyS0 through ttyS3 are defined as shown

crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3

So, I picked /dev/ttyS5 (COM 6) to use, and linked this to COMM PORT 6 (also selected in the SCANTOOL Software at the 9600 Baud rate) with the following command:
```

sudo ln -s /dev/ttyACM0 /dev/ttyS5

```

Running the command again:
```

ls -l /dev/ttyS*

```
gives:

crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3
lrwxrwxrwx 1 root root       12 2009-11-27 18:24 /dev/ttyS5 -> /dev/ttyACM0

We can determine the Baud rate of the Port:
```

stty -F /dev/ttyS5 -a

```
and to change it to 9600:
```

stty -F /dev/ttyS5 9600
stty -F /dev/ttyS5 -a

```

If you connect to a modem for testing you can transmit out an "ATZ"
causing the Modem to flash the lights and reset with:
```

echo ATZ > /dev/ttyS5

```
Which proves characters routed to /dev/ttyS5 get sent to /dev/ttyACM0, the USB to Serial Converter.

(I couldn't get Scantool 1.20 or 1.21 to detect the Serial ports.  I guess I need to compare the code to see what
has been changed.)

All that remains is to connect the ODBII Cable to the Vehicle, Connect the Serial cable to the ELMSCAN5, plug into the USB Port, and configure the Scantool Software for COMM 6 at 9600 baud.

[B]
ADDITIONAL Extra Misc Info:[/B]
[http://wiki.debian.org/Modem/3G/Vodafone](http://wiki.debian.org/Modem/3G/Vodafone)

Does the /dev/ttyS0 device exist? If not, try 'ln -s /dev/ttyUSB0 /dev/ttyS0'

Do you have read access to /dev/ttyUSB0? Depending on the config of your box, it may only be accessible by root.
```

id
ls -l /dev/ttyUSB0

```


REF:
[http://ubuntuforums.org/showthread.php?p=10099438#post10099438](http://ubuntuforums.org/showthread.php?p=10099438#post10099438)

LK

---


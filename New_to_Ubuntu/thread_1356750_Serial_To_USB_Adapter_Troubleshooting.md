---
title: "Serial To USB Adapter Troubleshooting"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by onezone on 2009-12-16
Let me start by saying that I am just getting started in the Linux world.

I am attempting to connect to a solar thermal controller using a usb to serial adapter.  I was able to successfully connect to a windows machine and pull data so I know the controller is functioning correctly.

I am not seeing any data from the controller.  I am trying to determine if I set everything up correctly on Linux and I am struggling to troubleshoot.  I am looking for tips/tricks to determine if the setup is correct.  Here is what I have done so far:

1) Ran "lsusb" and see my device:
"Bus 004 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port"

2) Ran "sudo modprobe usbserial vendor=0×067b product=0×2303"

3) Ran "dmesg" after plugging in the device.  I see my device: "usb 4-2: pl2303 converter now attached to ttyUSB0"

4) Ran minicom -s and set parameters on /dev/ttyUSB0 to 96008N1.  I also set Hardware and Software Flow Control to "No".  The controller requires 9600 baud, 1 start, 8 data and 1 stop bit, no parity and no handshake.

5)Ran "cat /dev/ttyUSB0" and a blinking cursor remained on the screen till I killed the line.  I also ran "cat /dev/ttyUSB0 > trace.log" and the file was empty.

Any help would be appreciated.

---

### Post by Chesamo on 2009-12-16
This may seem like an inane question, but are you absolutely sure that your adapter is supported on Ubuntu?

---

### Post by onezone on 2009-12-16
No...I am not sure at all.  Is there a way to determine this?

---

### Post by Dark_Stang on 2009-12-16
So what program did you use to work with that in Windows? Most serial adapters just use a Serial Port Terminal. Try installing one (I use gtkterm) and working with that.


Site note: And here I thought Cisco was the only company that still required the use of those stupid adapters.

---

### Post by onezone on 2009-12-16
I installed gtkterm and was able to configure the port correctly.  Thank you very much for your suggestion.

---

### Post by lkraemer on 2009-12-18
This information may be of help to you.  If you use a symbolic link
to link the USB port to the serial software it should all work.


SERIAL PORT NAMES:
If you are wondering how the ttyUSB0 (ttyACM0) is related to a com port or how to set it up?

Dos/Windows use the COM name while the messages from the serial driver use ttyS00, ttyS01, etc.
Older serial drivers (2001 ?) used just tty00, tty01, etc.

The tables below shows some examples of serial device names. The IO addresses are the default addresses
for the old ISA bus (not for the newer PCI and USB buses).

dos common IO USB-BUS ( ACM => acm modem )
name name major minor address || common name common name
COM1 /dev/ttyS0 4, 64; 3F8 || /dev/ttyUSB0 | /dev/ttyACM0
COM2 /dev/ttyS1 4, 65; 2F8 || /dev/ttyUSB1 | /dev/ttyACM1
COM3 /dev/ttyS2 4, 66; 3E8 || /dev/ttyUSB2 | /dev/ttyACM2
COM4 /dev/ttyS3 4, 67; 2E8 || /dev/ttyUSB3 | /dev/ttyACM3
- /dev/ttyS4 4, 68; various


SERIAL PORT or USB Converter:
If you don't have a serial port on your Laptop, or want to use a USB port Converter check out the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008 SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, modems, and the Serial ELMSCAN5.


SETUP UBUNTU (LINUX):
Open a Linux Terminal window and cut/paste the following commands with the
USB to Serial Adapter unplugged from a USB port.
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

Then plug in the USB-Serial Port adaptor to one of your USB ports. (REMEMBER to ALWAYS use this same port for when using your ODBII
Scanner) Wait for about 15 seconds, then cut and paste the following command in your Linux Terminal Window:
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
# EXTRA INFORMATION: ( Found by searching with Google)
# NOTE: ([http://ubuntuforums.org/archive/index.php/t-322770.html](http://ubuntuforums.org/archive/index.php/t-322770.html))
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
# serial port. In other words, nothing happens. This patch autodetects whether a PL-2303 or a PL-2303X
# is used and changes the initialization sequence accordingly.
#
# The PL-2303X can be distinguished from a PL-2303 by checking bMaxPacketSize0 for the device using
# lsusb -v -d 067b:2303 (as root). If bMaxPacketSize0 is 64, you probably have a PL-2303X and need this
# patch.The main kernel tree includes PL-2303X support starting from 2.6.8 (I can confirm that PL-2303X
# works on 2.6.11rc2 without my patch), making this patch unnecessary.
#
#


SYMBOLIC LINKING the COMM PORT:
To locate the possible used COMM PORTS in Ubuntu, cut and paste the following command:
```

ls -l /dev/ttyS*

```
Notice that ttyS0 through ttyS3 are defined as shown, along with the symbolic link
we will create in a minute.

crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3
lrwxrwxrwx 1 root root 12 2009-11-27 18:24 /dev/ttyS5 -> /dev/ttyACM0

So, I picked /dev/ttyS5 to use, and linked this to COMM PORT 6 (also selected in the SCANTOOL Software
at the 9600 Baud rate) with the following command.
Code:

ln -s /dev/ttyACM0 /dev/ttyS5

All that remains is to connect the ODBII Cable to the Vehicle, Connect the Serial cable to the ELMSCAN5, plug into the USB Port, and configure the ELMSCAN 5 Software for COMM 6 at 9600 baud.


ADDITIONAL Extra Misc Info:
[http://wiki.debian.org/Modem/3G/Vodafone](http://wiki.debian.org/Modem/3G/Vodafone)

Does the /dev/ttyS0 device exist? If not, try 'ln -s /dev/ttyUSB0 /dev/ttyS0'

Do you have read access to /dev/ttyUSB0? Depending on the config of your box, it may only be accessible by root.
```

id
ls -l /dev/ttyUSB0

```

lk

---

### Post by lavinog on 2009-12-18
I think the adapter is supported.

What program do you use in windows?
The problem may not be the converter, but the device you are trying to get data from.
You might need to send an initialization string to the device while in minicom

---

### Post by ihussain on 2012-09-20
Hello lkraemer,

I followed your instructions for registering usb-serial device. The USB-serial adapter is exactly the same as shown in the example.

Output from lsusb:-
imtiyaz@conquistador:~$ lsusb
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="DarkGreen"]Bus 006 Device 008: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter[/COLOR]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Last lines of dmesg:-
[ 7357.377069] usb 6-2: new full speed USB device using uhci_hcd and address 8
[ 7357.535371] usb 6-2: configuration #1 chosen from 1 choice
[ 7357.538255] cdc_acm 6-2:1.0: This device cannot do calls on its own. It is not a modem.
[ 7357.538305] cdc_acm 6-2:1.0: ttyACM0: USB ACM device

Below step did not give any error messages:-
sudo modprobe usbserial vendor=0x058f product=0x9720

But output of dmesg is the same. It does not display something like -
# usbserial_generic 1-1:1.0: generic converter detected
# usb 1-1: generic converter now attached to ttyUSB0
# usbcore: registered new interface driver usbserial_generic

Also, I have a doubt with your post. Your explanation's  vendorId : productId is 058f:9720 but you mentioned different values in the modprobe command - "sudo modprobe usbserial vendor=0x4348 product=0x5523" 

I am just beginning to learn about drivers and thinking whether this is related or a different matter altogether. I would appreciate your help. Please let me know if you need any inputs.

Thanks,
Immi

---

### Post by overdrank on 2012-09-20
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


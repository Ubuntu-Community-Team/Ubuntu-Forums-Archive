---
title: "USB Modem how to install?"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Raymond Day on 2008-05-18
I have Ubuntu server installed on a small Mini-ITX. I want it to record caller ID. So I got a USRobotics USR5637 56K V.92 USB modem. It's small so I can just use it on a USB port.

I can never get the green power LED to go on it. Or minicom to see it. Here are some commands I did.

```
root@small:~/modem# lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 047e:2892 Agere Systems, Inc. (Lucent)
Bus 001 Device 003: ID 0557:2008 ATEN International Co., Ltd UC-232A Serial Port [pl2303]
Bus 001 Device 001: ID 0000:0000
```

It's the Agere Systems, Inc. (Lucent) I know because if I unplug the it from the USB and do lsusb again it's not there. The other one is a RS232 to USB. The 232A Serial one.

A ./scanModem in part of the text said:

> Predictive diagnostics for card in bus 001:
	Modem chipset  detected on
SLOT="Bus 001 Device 004:"
NAME="Agere Systems, Inc. (Lucent) "
bus=001
USBmodemID=047e:2892
IDENT=agrsm
Driver=agrsm

 For candidate modem in:  001
    Agere Systems, Inc. (Lucent) 
      Primary device ID:  047e:2892
 Support type needed or chipset:	agrsm

When I do a **modprobe cdc_acm** command it looks like it does nothing. **lsmod** command shows this cdc_acm in it like this:

> Module                  Size  Used by
cdc_acm                17184  0

A long with a lot of other things.

What /dev would this be on? Or do I need to install some driver?

I am using:

**uname -a**
> Linux small 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686 GNU/Linux

I hope some one can help.

-Raymond Day

---

### Post by Raymond Day on 2008-06-11
Here is a link to the USB modem I have:

[http://www.usr.com/support/product-template.asp?prod=5637]("http://www.usr.com/support/product-template.asp?prod=5637")

Looks like it will not work with Linux. It's been a wile from me posting this and looking on how to get it to work. So I give up. It works on Windows XP just plug it in and the Green Power LED goes on. I never got it to go on in my Ubuntu server.

So does any one know of a small USB modem I can get that works with Ubuntu server? I mostly just want to use it to display caller ID on things I have.

-Raymond Day

---

### Post by Raymond Day on 2008-06-15
This my help. I read at:

[http://www.usr.com/support/5637/5637-ug/install.html#linux]("http://www.usr.com/support/5637/5637-ug/install.html#linux")

This:

> Linux Kernel 2.4.20 and Higher 
You need a USB modem driver (CDC ACM) compiled into a Linux kernel 2.4.20 or higher or as a loadable module for your kernel. Installation of the modem under these kernels is fully automatic provided your kernel has the Plug and Play module enabled (default). You do not need to install any drivers off the USRobotics installation CD-ROM.

Can any one tell me what to do by what this quoted text says?

-Raymond Day

I been working on this for so long. I rebooted my Ubuntu server because I did so many things to get the USB modem to work. After a reboot it still did not work.

It did not come back on a reboot till I hooked a screen to it. Then it said something like change the network. I could only say yes or no and I said yes and it booted up then. I think that's because all the things I have done to get this USB modem to work. But have not yet.

I went in minicom and did the port for /dev/ttyS1 but I don't think that's the USB modem. Looked on the web my USB modem should be on /dev/ttyACM0 but minicom says:

```
minicom: cannot open /dev/ttyACM0: No such file or directory
```

I think this my help. If I do a **tail /var/log/messages** after I reboot is shows this:

```
Jun 15 10:09:48 small kernel: [  577.668796] device eth0 entered promiscuous mode
Jun 15 10:09:48 small kernel: [  577.668812] audit(1213538988.394:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
Jun 15 10:10:29 small kernel: [  618.455213] tun: Universal TUN/TAP device driver, 1.6
Jun 15 10:10:29 small kernel: [  618.455220] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 15 10:11:58 small kernel: [  707.686848] ttyS1: LSR safety check engaged!
Jun 15 10:14:46 small kernel: [  876.133932] usbcore: registered new interface driver cdc_acm
Jun 15 10:14:46 small kernel: [  876.133941] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
Jun 15 10:29:34 small -- MARK --
Jun 15 10:37:06 small kernel: [ 2215.137054] ttyS1: LSR safety check engaged!
Jun 15 10:37:38 small kernel: [ 2247.272440] ttyS1: LSR safety check engaged!
```

The 2 last ones are when I did minicom as /dev/ttyS1 but it comes back saying:

> Minicom: Device disappeared, aborting!

I think that's the one RS232 port on the mini-itx motherboard I am running it on.

I hope some one can help. It's been a long time from posting this and no one can help.

Is this the right place to post this?

-Raymond Day

---

### Post by lswb on 2008-06-15
I can't give you the complete solution but this may help. The agere modem chipset is not a "hardware modem" that will respond directly to AT commands; it is a what is sometimes called a "soft modem" or winmodem. It uses the computer processor to help it function. The lucent/agere modems need some drivers & modules to work under linux. If you google "US Robotics modem linux drivers" one of the 1st results will be the USR web site where they have some drivers available for downloading.

I had a lucent modem in an older system not available to me right now. I can't remember the names of the modules it loaded, but I do recall that the system recognized it as /dev/ttyLTM0. When I ran dapper on that system, I had to obtain the drivers and install them myself, but IIRC, they were included with Hardy and installed out of the box. You may want to see if the /dev/LTM0 or a similar device node is created when you plug in the modem.

---

### Post by Raymond Day on 2008-06-16
After I rebooted and unplugged the USB modem and plugged it back in and did a **tail /var/log/messages** command I get this back now.

```
Jun 16 04:16:57 small kernel: [65781.371826] usb 4-4: USB disconnect, address 2
Jun 16 04:17:05 small kernel: [65789.715574] usb 4-4: new high speed USB device using ehci_hcd and address 4
Jun 16 04:17:05 small kernel: [65789.866509] usb 4-4: configuration #2 chosen from 1 choice
root@small:~#
```

Looks to me that it's using ehci_hcd and not cdc-acm like it should. Is this right? If so how would I fix it?

-Raymond Day

On another PC I booted Ubuntu live desktop 8.04 same as I have only the server type.

I booted with the USB modem plugged in and did the command **sudo modprobe cdc_acm** then unplugged the USB modem and plugged it back in. Here is the **tail /var/log/messages**:

```
Jun 16 06:47:33 ubuntu kernel: [  261.058628] lo: Disabled Privacy Extensions
Jun 16 10:51:53 ubuntu kernel: [  543.194330] usbcore: registered new interface driver cdc_acm
Jun 16 10:51:53 ubuntu kernel: [  543.197271] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
Jun 16 11:06:39 ubuntu -- MARK --
Jun 16 11:18:04 ubuntu kernel: [ 2113.871134] usb 1-1: USB disconnect, address 2
Jun 16 11:18:15 ubuntu kernel: [ 2124.722887] usb 1-1: new full speed USB device using uhci_hcd and address 3
Jun 16 11:18:15 ubuntu kernel: [ 2124.887261] usb 1-1: configuration #1 chosen from 1 choice
ubuntu@ubuntu:~$
```

Looks like on boot it seen it right as **cdc-acm.c** but then when I unplugged it and plugged it back in it thinks it's a **uhci_hcd**. I think that uhci_hcd is for hard drivers right?

I can never get it to be a /dev I hope with time can find out what's wrong.

-Raymond Day

From looking all over Google for help. My /ver/log/messages should say:

> cdc_acm 5-6.3:1.0: ttyACM0: USB ACM device

But that never comes up. What could be wrong?

-Raymond Day

---

### Post by lswb on 2008-06-16
I believe the ehci-cid module is a lower level driver that would be necessary to use this modem as well as another module. Did you check out the linmodems.org website? Its a good place to start. 

Most systems will recognize when they need the cdc-acm module and load it when a device requiring it is plugged in. From what I've sen, this USR modem is not such a device. You will need to find the correct drivers/modules for it, if they are available. If you find and install those, it may or may not also required the cdc-acm module. 

If it's possible, the smallest headache way to deal with this would be to get a modem that is known to work with linux. IMO for an low cost external device like a modem, it's the easiset way to go.

---

### Post by Raymond Day on 2008-06-17
Google finds nothing for "ehci-cid".

Yes I looked at [linmodems.org]("http://linmodems.org") website. But it don't look like it's for USB modems.

I put a USB keyboard on it and rebooted it. It works with the USB keyboard. In the /var/log/messages it says this:

```
Jun 17 04:59:24 small kernel: [  150.886230] input: Microsoft Internet Keyboard Pro as /devices/pci0000:00/0000:00:03.1/usb2/2-1/2-1.1/2-1.1:1.0/input/input4
Jun 17 04:59:24 small kernel: [  150.950822] input,hidraw0: USB HID v1.10 Keyboard [Microsoft Internet Keyboard Pro] on usb-0000:00:03.1-1.1
Jun 17 04:59:24 small kernel: [  150.963017] input: Microsoft Internet Keyboard Pro as /devices/pci0000:00/0000:00:03.1/usb2/2-1/2-1.1/2-1.1:1.1/input/input5
Jun 17 04:59:24 small kernel: [  151.030785] input,hidraw1: USB HID v1.10 Device [Microsoft Internet Keyboard Pro] on usb-0000:00:03.1-1.1
```

But after I do a command of **modprobe cdc_acm** all the /var/log/messages say about it is:

```
Jun 17 05:10:54 small kernel: [  876.588804] usbcore: registered new interface driver cdc_acm
Jun 17 05:10:54 small kernel: [  876.588813] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
```

It does not show any /dev that's it's on. It should show something like:

**cdc_acm ttyACM0: USB ACM device**

Then I could use it on /dev/ttyACM0 but it never shows up!

Any one know why?

-Raymond Day

I still have not got this working. I messed up my Ubuntu server so much that I restored it from a backup.

On USRobotics web page a PDF says for Linux:

> Linux Kernel 2.4.20 or Higher

You need a USB modem driver (CDC ACM) compiled into a Linux kernel 2.4.20 or higher or as a loadable module for your kernel. Installation of the modem under these kernels is fully automatic provided your kernel has the Plug and Play module enabled (default). You do not need to install any drivers off the USRobotics installation CD-ROM

A **uname -a** now comes back with:

Linux small 2.6.24-19-server #1 SMP Wed Aug 20 23:54:28 UTC 2008 i686 GNU/Linux

So I do have a kernel higher then what they say. How would I compile a CDC ACM modem driver? If that's right were would I download it? Or is there a apt-get?

-Raymond Day

---

### Post by KageKaze on 2008-09-12
Hi, on Ubuntu 8.04  this 5637 us robotics modem works. I checked with lsusb and it was recognized as us robotics. Then I configured my connection with kppp and chose  /dev/ttyACM0 in the modem tab. I don't know if you can install kpp (or any similar tool) though on ubuntu server (don't laugh, I'm a noob ...).
Also maybe that thread can help [http://www.linux-archive.org/kubuntu-user/150052-modem-usr-5637-a-2.html]("http://www.linux-archive.org/kubuntu-user/150052-modem-usr-5637-a-2.html").
There's this link also [http://www.linux-usb.org/USB-guide/x332.html]("http://www.linux-usb.org/USB-guide/x332.html").

---

### Post by Raymond Day on 2008-10-01
Tested it on a Ubuntu desktop.

Installed the kppp but it still don't work. A pic is worth a 1000 words:

[IMG]http://i93.photobucket.com/albums/l41/RaymondDay/Ubuntu/Still_dont_see.png[/IMG]

[IMG]http://i93.photobucket.com/albums/l41/RaymondDay/Ubuntu/set-to-ttyACM0.png[/IMG]

I had this for mounth now and still can't get it to work in Ubnutu. It works in Windows. Plug and play!

-Raymond Day

---

### Post by Raymond Day on 2009-07-09
Well I had this for 9 months now. Still can't get it working! It's been sitting in my USB port all this time hoping it would work on day.

So any one know of a small USB modem that does caller ID that I will work with Ubuntu server? I would buy one if it was small and worked.

I got this one talked about here because it said it works with Linux.

-Raymond Day

---

### Post by three_jeeps on 2009-09-30
I don't know if you got it working yet, but I had similar problems when a Dell USB modem would not be recognized in 8.04 Server LTS.
I am running it on a VIA pico-itx platform.  
lusb reported the following:
I did the following:Bus 001 Device 002: ID 0572:1324 Conexant Systems (Rockwell), Inc.
uname reported the following: 2.6.24-19-server 

1. Ran scanModem available from: [http://132.68.73.235/linmodems/first.html](http://132.68.73.235/linmodems/first.html)
In part, the report said:
Predictive  diagnostics for card in bus 001:
	Modem chipset  detected on
SLOT="Bus 001 Device 003:"
NAME="Conexant Systems (Rockwell), Inc. "
bus=001
USBmodemID=0572:1324
IDENT=dgcmodem
Driver=dgcmodem

 For candidate modem in:  001
    Conexant Systems (Rockwell), Inc. 
      Primary device ID:  0572:1324
 Support type needed or chipset:	dgcmodem

2) So for my application I found out that I had to do this:
Compiling is necessary packages must be installed, providing:
        linux-headers-2.6.24-19-server
[The package    linux-headers-2.6.24-19-server  will be installed to
/usr/src/ and is a general resource needed for compiling. IT will be
accessed by the modem specific dgcmodem code package.   With your
install Ubuntu CD in place, try
$ sudo apt-get install linux-headers-2.6.24-19-server

if it is not found go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  use the search
engine, directing you to:
[http://packages.ubuntu.com/hardy-updates/linux-headers-2.6.24-19-server](http://packages.ubuntu.com/hardy-updates/linux-headers-2.6.24-19-server)
You will also need at least the dependent linux-headers-2.6.24-19
package.  Under Linux they will coinstall with
# sudo dpkg -i linux*.deb]

 Then the modem requires a dgcmodem package.
 From  [http://www.linuxant.com/drivers/dgc/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/dgc/downloads-ubuntu-x86.php)
 download dgcmodem-7.68.00.12full_k2.6.24_19_server_ubuntu_i386.deb.zip
 Under Linux unpack with:
 $ unzip dgcmodem*.zip
 Then install with:
 $ sudo dpkg -i dgcmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.

 Read DOCs/Conexant.txt

Further searching found that:
File: 7.68.00.12full_k2.6.24_19_server_ubuntu_i386.deb.zip
is not in the list....
The closest one matching your spec
is:     dgcmodem_1.08_k2.6.24_19_server_ubuntu_i386.deb.zip
That is the one to use....

3) I did the above and when I plugged in the modem it worked OK.

Perhaps you need to do something similar? e.g. scanModem, update the Linux headers via /hardy updates??  
Perhaps when you installed cdc_ACM it was the equivalent of me installing dcgmodem.  Maybe you needed to update the headers?

I got the most help from this ng:discuss@linmodems.org
At the risk of being presumptuous, perhaps this fellow can help....(he replied from the discussion group, and for me, he is a bloody genius)
Marvin Stodolsky <marvin.stodolsky@gmail.com>

After reading what all you went through, I am thinking your install was somehow corrupted?  or that perhaps some IRQ settings in your bios need to be changed/enabled for chaining or or just plain enabled?  Did you check the BIOS?
Hope you had good luck...
John

---


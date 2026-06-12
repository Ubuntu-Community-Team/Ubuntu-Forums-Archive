---
title: "Hey I got a Zydas based USB connector working!!!"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by crispy_420 on 2007-06-08
Off and on for several months I've been trying to get my Zydas USB dongle to work. And finally got it working late last night. Keep in mind I'm using Gutsy Gibbon Tribe One but it should work in Feisty.

First get the deb and install as you would normally here is the link:

[http://ftp.debian.org/debian/pool/no...1211-firmware/](http://ftp.debian.org/debian/pool/no...1211-firmware/)

Next is load the module:

sudo modprobe -v zd1211rw

Go to network-manager in panel and disable wireless by right clicking. Then enable it again. Now you should see your wireless connections by left clicking panel icon. Give one a test run.

If it works now add to /etc/modules as root with your favorite text editor by adding modprobe zd1211rw at end of file.

Hope that helps someone out.

If something looks wrong about my procedure, please point it out.

---

### Post by rubengs on 2007-07-02
What is the URL? it appears crippled. I have the same USB card.

---

### Post by ugm6hr on 2007-07-02
Presumably this:
[ftp://ftp.debian.org/debian/pool/non-free/z/zd1211-firmware](ftp://ftp.debian.org/debian/pool/non-free/z/zd1211-firmware)

---

### Post by gorby on 2008-01-07
No joy for me

I get this msg when i inserting

[ 2001.409043] usbcore: deregistering interface driver zd1211rw
[ 2009.572045] usb 2-6: reset high speed USB device using ehci_hcd and address 5
[COLOR="Red"][ 2009.744310] zd1211rw 2-6:1.0: RF UNKNOWN_A_RF 0xa is not supported[/COLOR]
[ 2009.855803] usb 2-6: reset high speed USB device using ehci_hcd and address 5
[ 2009.988858] usbcore: registered new interface driver zd1211rw

No new interface is created or anuthing =(

what version of ubuntu are you useing, im on 7.10 the 64 bit flavour.

---

### Post by m.capurso on 2008-01-25
I have a different Zydas usb adapter that failed in a different way:

If you connect a ZyDAS 802.11b WiFi usb, it is seen in the usb list

admin@sassuxp:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 0ace:1201 ZyDAS 802.11b WiFi

the module is loaded

admin@sassuxp:~$ lsmod
Module Size Used by
zd1201 23812 0
zd1201 23812 0
...
usbcore 138632 3 zd1201,uhci_hcd
...
but dmesg gives the following messages:

[11781.580000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[11796.692000] usb 1-1: device descriptor read/64, error -110
[11811.908000] usb 1-1: device descriptor read/64, error -110
[11812.124000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[11828.452000] usb 1-1: new full speed USB device using uhci_hcd and address 5
[11828.616000] usb 1-1: configuration #1 chosen from 1 choice
[11829.200000] usb 1-1: Failed to load zd1201.fw firmware file!
[11829.200000] usb 1-1: Make sure the hotplug firmware loader is installed.
[11829.200000] usb 1-1: Goto [http://linux-lc100020.sourceforge.net](http://linux-lc100020.sourceforge.net) for more info.
[11829.200000] usb 1-1: zd1201 firmware upload failed: -2
[11829.200000] zd1201: probe of 1-1:1.0 failed with error -2
[11829.200000] usbcore: registered new interface driver zd1201

I solved in this way



I spent the whole afternoon and I solved the problem.
You included the Zd1201 module BUT NOT the firmware.

I went to

[http://sourceforge.net/projects/linux-lc100020/](http://sourceforge.net/projects/linux-lc100020/)

and I got the firmware as a tar.gz

[http://downloads.sourceforge.net/linux-lc100020/zd1201-0.14-fw.tar.gz?modtime=1107218895&big_mirror=0](http://downloads.sourceforge.net/linux-lc100020/zd1201-0.14-fw.tar.gz?modtime=1107218895&big_mirror=0)

Next I gunzipped zd1201.fw and I copied in /lib/firmware/2.6.22-14-generic/ working as a root.

cp zd1201.fw /lib/firmware/2.6.22-14-generic/

Finally I extracted and reattached the usb wifi adapter.

and dmesg gives :

[18589.160000] usb 1-1: new full speed USB device using uhci_hcd and address 7
[18632.704000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[18632.868000] usb 1-1: configuration #1 chosen from 1 choice
[18633.448000] usb 1-1: wlan0: ZD1201 USB Wireless interface
[18635.540000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

And now it becomes visible in the network manager

---


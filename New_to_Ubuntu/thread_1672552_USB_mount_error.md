---
title: "USB mount error"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by tikitikimaji on 2011-01-21
I have a flash drive that was working fine, then one day, Ubuntu started having trouble recognizing it.  It shows up just fine on my friend's windows computer, but not at all on mine any more.  When I restart the computer with it plugged in, I get messages like 

"USB 1-2 device descriptor read/64, error 71" 

a bunch of times before ubuntu starts up.

I don't know if this has anything to do it, but this started after I transferred files from ubuntu to my virtual box Windows...but my virtual windows expired so I'm just using ubuntu now...

Thanks for any ideas

---

### Post by corncob on 2011-01-21
I don't know why it would be working and then suddenly stop.  Do you have 'NTFS Configuration Tool' and 'MountManager' installed.  They're in the Software Center.  See if they help.

---

### Post by tikitikimaji on 2011-01-24
I can't figure it out.  The USB device doesn't show up in Mount manager either.  It really was strange that if would be working one day and not the next, yet still work on windows computer.  Might it be a virus?  Is there a way to force Ubuntu to recognize that it's at least plugged in?

When I open virtual box and try to get it to be recognized there, it recognizes that the device is plugged in, but can't mount it because "the host OS cannot mount it"

...not sure what to do...

---

### Post by nomko on 2011-01-24
Plug your device in your computer and open a terminal.
Type in the command : **lsusb** and place the output here.

---

### Post by tikitikimaji on 2011-01-24
after Lsusb command:


Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 002: ID 10f1:1a13  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by tikitikimaji on 2011-01-24
I also got this after a tip from another thread, I entered dmesg |tail:


nik@nik-laptop:~$ dmesg | tail
[ 7981.712177] usb 2-2: device descriptor read/64, error -71
[ 7986.936148] usb 2-2: device descriptor read/64, error -71
[ 7987.153155] usb 2-2: new full speed USB device using uhci_hcd and address 6
[ 7992.273155] usb 2-2: device descriptor read/64, error -71
[ 7997.496168] usb 2-2: device descriptor read/64, error -71
[ 7997.713159] usb 2-2: new full speed USB device using uhci_hcd and address 7
[ 8003.125133] usb 2-2: device not accepting address 7, error -71
[ 8003.237164] usb 2-2: new full speed USB device using uhci_hcd and address 8
[ 8008.645073] usb 2-2: device not accepting address 8, error -71
[ 8008.645105] hub 2-0:1.0: unable to enumerate USB device on port 2

---

### Post by tikitikimaji on 2011-02-09
Does any of that info help?  I figured out that if I restart with the USB plugged in, then unplug and replug it in, it will be recognized.  But then after a few minutes of working, the window and icon will just disappear (?!?).  It still works fine on any Mac or Windows comp I plug it into...

Any Ideas?  Please?

---

### Post by dgposey on 2011-02-17
Anybody have any ideas?  I'm interested to see the resolution to this problem.

---


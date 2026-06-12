---
title: "D-Link WUA-2340 Wireless Setup"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by Double D on 2007-07-17
ive followed the instructions on this thread

[http://ubuntuforums.org/showthread.php?p=2200725](http://ubuntuforums.org/showthread.php?p=2200725)  

and installed everything properly, but when i execute sudo modprobe ndiswrapper i get no response (blinking light). 

ndiswrapper -l shows driver and device present but iwconfig comes up with no eth0 or lo connections

can anyone help me on this one?

---

### Post by Double D on 2007-07-17
bump

---

### Post by Double D on 2007-07-18
someone help me please

---

### Post by Double D on 2007-07-18
with dmesg i get

[ 541.928508] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[ 542.098619] usbcore: registered new interface driver ndiswrapper
[62912.943364] usb 1-2: new full speed USB device using uhci_hcd and address 2
[62913.111678] usb 1-2: configuration #1 chosen from 1 choice
[62913.311302] usb 1-2: reset full speed USB device using uhci_hcd and address 2
[62913.636732] ndiswrapper: driver neta5agu (D-Link,05/08/2006,1.5.202.2) loaded
[62913.642416] ndiswrapper (ZwQueryValueKey:2568): not fully implemented (yet)
[62913.642619] ndiswrapper (NdisWriteErrorLogEntry:231): log: C0001389, count: 4, return_address: c8b1b9fb
[62913.642634] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0xc4af27c8
[62913.642645] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0x28
[62913.642656] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0xc8a2c000
[62913.642668] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0xc8a2c000
[62913.642822] ndiswrapper (miniport_init:275): couldn't initialize device: C0000001
[62913.642849] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[62913.642897] unregister_netdevice: device eth%d/c4af2000 never was registered
[62913.642926] ndiswrapper (miniport_halt:339): device c4af2400 is not initialized - not halting
[62913.642939] ndiswrapper: device eth%d removed
[62913.643027] ndiswrapper: probe of 1-2:1.0 failed with error -22
[62913.643294] usb 1-2: device_add(1-2:1.0) --> -22


also

tail /var/log/messages
Jul 18 14:20:11 Ubuntu kernel: [62913.642939] ndiswrapper: device eth%%d removed
Jul 18 14:20:11 Ubuntu kernel: [62913.643027] ndiswrapper: probe of 1-2:1.0 failed with error -22

---

### Post by Double D on 2007-07-31
ok i finally got the driver working and setup, but it still wont connect to my wireless
im using mac address filtering and ive added all mac addresses that ifconfig and iwconfig gives me to my router's allow list

when i run dmesg | grep ndiswrapper the only error i encounter is 

[ 41.184690] ndiswrapper (ZwQueryValueKey:2568): not fully implemented (yet)

is this to any significance?

---

### Post by buddaman on 2007-09-12
Did you ever get this working?  Or did you give up due to no response.  I'm having a similar issue and trying to make some head way.

---

### Post by Jeremy Jackins on 2007-09-12
I found it fairly easy. from the cd, copy the Drivers folder to your home folder, then on the command line use

sudo ndiswrapper -i ~/Drivers/NetA5AGU.inf

assuming you have ndiswrapper set up correctly.
then add ndiswrapper to you /etc/modules. you will need to reboot before it will kick in, so you have to have ndiswrapper listed in /etc/modules.

---

### Post by Jeremy Jackins on 2007-09-12
oh and mine shows up as wlan0, not eth0

---

### Post by Double D on 2007-09-12
> **buddaman said:**
> Did you ever get this working?  Or did you give up due to no response.  I'm having a similar issue and trying to make some head way.

i actually got it working with the latest ndiswrapper version on ubuntu
i gave up on trying to make it work on xubuntu

---


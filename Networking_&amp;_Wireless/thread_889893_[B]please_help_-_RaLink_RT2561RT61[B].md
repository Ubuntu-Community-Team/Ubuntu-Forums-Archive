---
title: "[B]please help - RaLink RT2561/RT61[/B]"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by chriswhiteoak on 2008-08-14
Hi, I have just installed Ubuntu for the first time, i'm new to anything linux but it all looks goood so far. Only thing is I'm having a lot of difficulty trying to work out how to connect to my wifi. I think it has something to do with enabling my wlan or a driver or something but i really don't have a clue, Ubunutu is scaring me!! lol.

While reading other threads trying to work it out i noticed people were posting these, so if any of this helps anbody:
[COLOR="Red"]
chris@chris-ubuntu:~$ sudo lshw -C network
*-network:0 DISABLED
description: Wireless interface
product: RT2561/RT61 802.11g PCI
vendor: RaLink
physical id: 6
bus info: pci@0000:00:06.0
logical name: wmaster0
version: 00
serial: 00:10:60:67:44:4a
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
*-network:1
description: Ethernet interface
product: VT6102 [Rhine-II]
vendor: VIA Technologies, Inc.
physical id: 12
bus info: pci@0000:00:12.0
logical name: eth0
version: 74
serial: 00:40:d0:96:69:3b
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=128 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s


chris@chris-ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11g ESSID:""
Mode:Managed Channel:0 Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit:7 RTS thr:off Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


chris@chris-ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:40:d0:96:69:3b
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:11 Base address:0x2000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:94 errors:0 dropped:0 overruns:0 frame:0
TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:4700 (4.5 KB) TX bytes:4700 (4.5 KB)[/COLOR]



If anyone can help me it would be much appreciated if you can give step by step instructions, as i have only been using linux for a day. I'm sure the problem is probably something really simple, but with not using linux before i don't have a clue!

Many thanks

---

### Post by chili555 on 2008-08-14
> *-network:0 DISABLED
description: Wireless interface
product: RT2561/RT61 802.11g PCII wonder why it's disabled. Is this a laptop with a switch on the front or a key combination that turns the wireless on and off? Is it a desktop where the wireless may be enabled or disabled in the BIOS? Can you shed any light on this?> enabling my wlan or a driver or somethingYou have a driver associated now.> module=rt61pciPlease help us understand why it's disabled.

---

### Post by chriswhiteoak on 2008-08-15
I'm on a laptop, and there's no switch to turn on the wireless, it's just on all the time in windows. i do have a "Fn" key very bottom left on keyboard, and the F keys double up as wireless on/off, vol up/down, brightness up/down etc, but i tried pressing this and it doesn't seem to do anything in ubuntu.

So i just need to figure out how to enable wireless?? any other ideas?? i have a Packard Bell EasyNote R1935 if that helps anyone.

---

### Post by chili555 on 2008-08-15
Open a terminal and do:```
sudo tail -f /var/log/messages
```Now press the key combination to activate wireless. Watch the terminal window and see if the kernel has any recognition of the key presses. Post back the outcome and let's see if we can coax this one to life.

---

### Post by chriswhiteoak on 2008-08-15
ok i did what you said and this is the outcome i got:

Aug 15 21:11:50 chris-ubuntu kernel: [  218.366513] atkbd.c: Unknown key pressed (translated set 2, code 0x6a on isa0060/serio0).
Aug 15 21:11:50 chris-ubuntu kernel: [  218.366523] atkbd.c: Use 'setkeycodes 6a <keycode>' to make it known.
Aug 15 21:11:50 chris-ubuntu kernel: [  218.487175] atkbd.c: Unknown key released (translated set 2, code 0x6a on isa0060/serio0).
Aug 15 21:11:50 chris-ubuntu kernel: [  218.487180] atkbd.c: Use 'setkeycodes 6a <keycode>' to make it known.

---

### Post by chili555 on 2008-08-15
This just gets curioser and  curioser! Let's see if the firmware is getting loaded. Please post:```
dmesg | grep firmware
```Thanks.

---

### Post by chriswhiteoak on 2008-08-17
I'm not sure I'm doing this right, i typed in what you put, but it did nothing. If i did just the "dmesg" part it comes up with a load of code that's like 100 lines long, should i just post that??

---

### Post by tibormade on 2009-05-12
I have the exact same problem with the exact same machine running jaunty. Does anyone know how to get over this problem?

Packard Bell Easynote R1935 / RaLink RT2561/RT61 card network: Disabled

I'm pretty sure it's the function key issue, but there just doesn't seem to be any way around it!

Help!

---


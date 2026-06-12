---
title: "cant find wireless device model"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by Houman on 2008-09-28
Hello everyone;

I have installed linux on my new HP m8525f desktop, however the wireless card has problems, it disconnects when the network load is heavy, and there are a bunch of weird lines in my /var/log/messages, it is full of this:

```

 Please file bug report to http://rt2x00.serialmonkey.com

```

also dmesg is flooded with this line:

```

[ 2324.349030] phy0 -> rt2x00usb_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
[ 2324.349033] Please file bug report to http://rt2x00.serialmonkey.com.

```

and the speed of my wireless network is pretty low;

I would like to find a fix for this, but i cant even find the hardware device for my wireless card, when I read the manual for the desktop, it just says this under the wireless section:

```

Wireless
Wireless LAN 802.11 b/g

```

output of lspci just shows what I believe to be my wired connection:

```

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

can anyone please point me in the right direction? how do I find the actual wireless device model so I can start googling for a fix?

regards

Houman

---

### Post by Houman on 2008-09-28
ops I think I solved the problem, Its a usb device not a pci device, so i should have done lsusb rather than lspci, the output of lsusb is: 

```

Bus 008 Device 003: ID 03f0:0517 Hewlett-Packard LaserJet 1000
Bus 008 Device 002: ID 0471:060c Philips 
Bus 008 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 15a9:0004  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

```

I think its the last device, I Still have no clue as how to fix this problem if anyone is aware of a fix please let me know;

thanks

H

---

### Post by Houman on 2008-09-28
ok seems like this problem has been around for a while:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/133486](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/133486)

---

### Post by Houman on 2008-09-28
OK i got th problem fixed, the solution is right here:

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

now my internet works perfect, fast as lightening :guitar:

---


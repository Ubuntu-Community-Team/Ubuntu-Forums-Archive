---
title: "Problems Setting Up Netgear N600 Wireless USB Adapter"
date: 2015-11-22
forum: Networking &amp; Wireless
---

### Post by Tris2006 on 2015-11-22
I installed Lubuntu 15.10 on my brothers computer yesterday and now im trying to install his wireless USB adapter to get online.
Maybe someone can help me out because I cant seem to get it working, I always seem to have issues when it comes to wireless networking on Linux.  :frown:

The adapter is a Netgear Wireless N Adapter N600 Dual Band
Model number:WNDA3100

I can see it listed when I use lsusb
```

jerry@JerrysGaragePC:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 046d:c225 Logitech, Inc. G11/G15 Keyboard / G keys
Bus 006 Device 004: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 006 Device 003: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 006 Device 002: ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="#0000CD"]**Bus 001 Device 002: ID 0846:9014 NetGear, Inc.**[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

ifconfig is not showing any wireless connections. 

And iwconfig shows nothing ether.

```

jerry@JerrysGaragePC:~$ iwconfig
enp0s25   no wireless extensions.

lo        no wireless extensions.
```

Drivers must not be kicking in or something, can someone point me in the right direction?

---

### Post by Bucky Ball on 2015-11-22
With it plugged in, give the output of this command, please:

```
sudo lshw -C network
```

Be advised that this dongle is problematic and people have had a lot of troubles getting it up in the past. You might cut a long story short by getting a USB dongle that is known to work 'out of the box' with Ubuntu. Always pays to do some research and there's plenty to dig through [here]("https://duckduckgo.com/?q=Netgear+N600+ubuntu").

Some go down the ndiswrapper path with this dongle, often more trouble than its worth, and not always guaranteed of success (and ndiswrapper is largely superseded). I wouldn't advise it. (One person installed ndiswrapper and Wine just to get this thing working, a clumsy workaround and a whole lot of stuff you probably don't want or need for anything other than the wireless card, particularly when you can buy one that you can just plug in and it works for a few bucks.)

---

### Post by Tris2006 on 2015-11-22
lshw -C network
**Output:**
```
  *-network               
       description: Ethernet interface
       product: 82567V-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 00
       serial: 00:1c:c0:b2:16:fc
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k duplex=full firmware=1.8-5 ip=192.168.0.43 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:27 memory:d3300000-d331ffff memory:d3324000-d3324fff ioport:f0c0(size=32)

```

---

### Post by Bucky Ball on 2015-11-22
Nope. No sign of it.

> **Tris2006 said:**
> 

Drivers must not be kicking in or something ...

And nor will they. You will need to put on a massive jackboot and do the kicking yourself in an attempt to get this working, if you can. Most people admit defeat and buy a cheapie that 'just works'. You might get lucky and someone might chime in with a 'miracle cure', but I have never heard of one and only ever see problems with this card and little to no solutions. 

Good luck whatever you decide. :)

---

### Post by Tris2006 on 2015-11-23
Ok thanks for the help, Ill keep kicking it for now. :P

---

### Post by Bucky Ball on 2015-11-23
Good luck and if you kick it in to life, please share and mark as solved (first link in my signature), as there are plenty out there who'd like to know how to do this without jumping through a million hoops with dirty workarounds and installing a heap of unwanted software. Thanks. :)

PS: A lot of folk have these in a drawer somewhere waiting until they work out of the box with Ubuntu. That day may or may not arrive. The wait has been going on for a considerable while now.

---

### Post by Tris2006 on 2015-11-24
My brother went ahead and ordered another dongle last night. It's a TP-Link Wireless N USB Adapter TL-WN722N.

Had some good reviews from Linux users, so hopefully this does the trick. :)

I'm kinda glad he did because I really don't feel like using ndiswrapper. It makes me feel dirty....

---

### Post by chili555 on 2015-11-24
Please see: [https://wikidevi.com/wiki/Netgear_WNDA3100v3](https://wikidevi.com/wiki/Netgear_WNDA3100v3) It refers to your device:> ID: 0846:9014
Windows: USB\VID_0846&PID_9014Then see: [http://ubuntuforums.org/showthread.php?t=2221251&page=3](http://ubuntuforums.org/showthread.php?t=2221251&page=3)> At this time, I know of no way to get the device working. If you can find Windows XP 64-bit driver files, that is .inf and .sys, we can try ndiswrapper again.Sorry.

---

### Post by Tris2006 on 2015-11-24
> **chili555 said:**
> Please see: [https://wikidevi.com/wiki/Netgear_WNDA3100v3](https://wikidevi.com/wiki/Netgear_WNDA3100v3) It refers to your device:Then see: [http://ubuntuforums.org/showthread.php?t=2221251&page=3](http://ubuntuforums.org/showthread.php?t=2221251&page=3)Sorry.

I checked netgears website, didn't see any xp drivers. Unless someone's got a zip file of xp drivers lying around they could send me. :P

---

### Post by Bucky Ball on 2015-11-24
I'd wait for the other dongle then as you will need to use ndiswrapper for this one. I know, it can be a grubby feeling. :)

---

### Post by Tris2006 on 2015-11-24
> **Bucky Ball said:**
> I'd wait for the other dongle then as you will need to use ndiswrapper for this one. I know, it can be a grubby feeling. :)
Ah, does anyone happen to know which driver works best? Could save me some trial and error time. :)

---

### Post by chili555 on 2015-11-24
> **Tris2006 said:**
> My brother went ahead and ordered another dongle last night. It's a TP-Link Wireless N USB Adapter **TL-WN722N**.

Had some good reviews from Linux users, so hopefully this does the trick. :)

I'm kinda glad he did because I really don't feel like using ndiswrapper. It makes me feel dirty....I have and occasionally use that exact device. I plugged it in and it connected. Job done.

Mine cost me US$13.

---

### Post by Bucky Ball on 2015-11-24
With the TP-Link? Just plug it in and see what happens. There are plenty of drivers already part of the kernel.

If you can get online with a cable, plug that in so you are online, plug the dongle in. If no response (give it a second and you should see 'Wireless networks are available') then open Additional Drivers and see if there is something there for it. Failing all that, with the dongle in, open a terminal and:

```
sudo lshw -C network
```

Post the output here between code tags (last link in my signature).

(chili ninja-ed me again: Yep, looks like it should 'just work'. :)

---

### Post by Tris2006 on 2015-11-24
Ohhh I thought you ment I needed to use ndiswrapper for the TP link. :P

OK I'll report back once I test out the new dongle.

---

### Post by Bucky Ball on 2015-11-24
> **Tris2006 said:**
> Ohhh I thought you ment I needed to use ndiswrapper for the TP link. :P

Doubtful. :)

---


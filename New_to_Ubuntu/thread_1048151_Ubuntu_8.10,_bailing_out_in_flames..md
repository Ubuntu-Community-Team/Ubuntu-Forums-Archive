---
title: "Ubuntu 8.10, bailing out in flames."
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-01-23
Can I run Ubuntu 8.04.2 on Gateway MX6436 laptop?  512mb, 128 ram.  Tried 8.10 for 3 weeks, a lot jawing with well intentioned people trying to help and still no network recognition from a well established network.  Will this version work any better?  I would like to stay with Linux, but I have to get on line.

---

### Post by Kobalt on 2009-01-23
Is your problem related to your ethernet or wifi hardware? 
Newer versions of Ubuntu usually have a better hardware support, but you could still try out Ubuntu 8.04.2 from a Live CD.

---

### Post by Kevbert on 2009-01-23
When you install, you want to have ethernet to the internet connected as this may help. I see your PC supports 802.11b/g with 125 high speed (?), do you know what chipset the wireless is ? (Atheros, Broadcom, Ralink ?)

---

### Post by Yed Ied on 2009-01-23
It seems to be a recognition problem.  The laptop had XP Home before I formatted and downloaded 8.10, and with XP it recognised the verizon network. I had to give it the ESSID, & WEP, but no problems.  I just can't get 8.10 to see it.  I have this H P and a Mac on the same network.  I keep thinking the problem is with me, but I see a lot of people with the same problem.  My novice thought is that maybe a more established release might have resolved problems like this.   
Thanks for reply

---

### Post by Sealbhach on 2009-01-23
> **Yed Ied said:**
> My novice thought is that maybe a more established release might have resolved problems like this.   
Thanks for reply

I think you're better with 8.10, it's got a better Network Manager (version 0.70).

Also, just looking at your thread here:

[http://ubuntuforums.org/showthread.php?p=6549564#post6549564](http://ubuntuforums.org/showthread.php?p=6549564#post6549564)

We need you to provide us with information about your hardware so that we can help you get connected. 

So please copy and paste these commands into a terminal and paste the results you get here:

```
lspci | grep -i net
```
```

lshw -C network
```

.

---

### Post by Yed Ied on 2009-01-23
No I don't what chip set it is, and I don't know how to find out, sorry.

---

### Post by Sealbhach on 2009-01-23
> **Yed Ied said:**
> No I don't what chip set it is, and I don't know how to find out, sorry.

Those commands in my post will show that info. You can find the terminal in the menu: Applications -> Accessories -> Terminal.

Just copy and paste each command and press return. You can copy and paste the results in your reply.


.

---

### Post by Captain_tux on 2009-01-23
> **Yed Ied said:**
> Can I run Ubuntu 8.04.2 on Gateway MX6436 laptop?  512mb, 128 ram.  Tried 8.10 for 3 weeks, a lot jawing with well intentioned people trying to help and still no network recognition from a well established network.  Will this version work any better?  I would like to stay with Linux, but I have to get on line.

How old is the laptop? With those specs, it just doesn't seem like your machine has the chops to run recent versions of Ubuntu (or other recent OSs). 

Perhaps Fluxbuntu would be better? Or other light-weight Linux distros like DSL or Puppy??

---

### Post by Yed Ied on 2009-01-23
O K, but give me some time, a lot going on, I'LL BE BACK.
Thanks

---

### Post by halovivek on 2009-01-23
if you post the results. we can help you where is the problem arise and we can help you to solve.

---

### Post by linux_tech on 2009-01-23
> **Yed Ied said:**
> Can I run Ubuntu 8.04.2 on Gateway MX6436 laptop?  512mb, 128 ram.  Tried 8.10 for 3 weeks, a lot jawing with well intentioned people trying to help and still no network recognition from a well established network.  Will this version work any better?  I would like to stay with Linux, but I have to get on line.

With 128 RAM, you should install a different linux. Puppy Linux would probably be your best bet.
[http://www.puppylinux.org/index.php?q=downloads](http://www.puppylinux.org/index.php?q=downloads)

---

### Post by -kg- on 2009-01-23
> **Yed Ied said:**
> Can I run Ubuntu 8.04.2 on Gateway MX6436 laptop?  512mb, 128 ram.  Tried 8.10 for 3 weeks, a lot jawing with well intentioned people trying to help and still no network recognition from a well established network.  Will this version work any better?  I would like to stay with Linux, but I have to get on line.

[QUOTE=linux_tech]With 128 RAM, you should install a different linux. Puppy Linux would probably be your best bet.[/QUOTE]

I was wondering about that myself, but according to [this site:]("http://support.gateway.com/s/Mobile/Q106/Blade/1008822sp2.shtml")

> Memory 	512 MB DDR (1 × 512 MB) (PC2700) SODIMM
Total slots: 2 DDR2 slots | Available slots: 1 DDR2 slot
Expandable to 2 GB 

I don't know what the "128" is (possibly he was referring to the 128 K L2 Cache), but from the specs on the Gateway website for that machine, it should be well capable of running Ubuntu, though personally I would upgrade the RAM to 1 GB.

---

### Post by Yed Ied on 2009-01-24
SEALBHACH, I entered 1shw -c network
Reply- bash:  1shw: command not found
I emtered  sudo 1shw -c network
Reply- sudo: shw: command not found

I can't find the vertical line (symbol) in the other command.

---

### Post by spiderbatdad on 2009-01-24
not 1shw. instead ls (as in list) hw (as in hardware) ```
lshw -C network
```

```
lspci
```list pci connected devices.

The vertical line, or pipe symbols, is located above the enter key. It may be broken in the middle. shift+backslash, usually.

---

### Post by Yed Ied on 2009-01-24
Sealbhach,  found what I needed,(it's early)
entered- 1spci | grep -i net
reply- bash: 1spci: command not found

---

### Post by Yed Ied on 2009-01-24
Spiderbatdad, did I not enter code for the two commands properly?

---

### Post by Axelpalm on 2009-01-24
> **Yed Ied said:**
> Spiderbatdad, did I not enter code for the two commands properly?
You are correct. You did use 1 (nummeric) instead of l (character).

---

### Post by Yed Ied on 2009-01-24
Axelpalm- Yes I used the number 1.  Thought I screwed up....................Again.
Thanks

---

### Post by Coinneach on 2009-01-24
Yed Ied

It is supposed to be a l (as in **l**ist)

so just copy and paste this command in TERMINAL

lshw -c network

---

### Post by Yed Ied on 2009-01-24
MY BAD "l" it is, looks like a ONE, sorry.

---

### Post by Yed Ied on 2009-01-24
03:00.0 Ethernet Controller: Marvell Technology Group Ltd.  
88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:02.0 Network Controller: Broadcom Corporation BCM4318 
[AirForce One 54g] 802.11g Wireless Lan Controller (rev 02)

More to come, it's funny, when ya put the right stuff in the right stuff comes out.  I don't know how to cut and paste I'll have to type it.

---

### Post by llamabr on 2009-01-24
copy/paste works just like you'd expect.  You can ctrl-c and ctrl-v in firefox.  In gnome-terminal, it's shift-ctrl-c.

Also, though, usually, you can just highlight a bit with your mouse's left button, and then paste by clicking the middle button on your mouse.  I find this to be much more convenient and intuitive, than the way you've seen it elsewhere.

---

### Post by Yed Ied on 2009-01-24
I can't get on line with the laptop you need the info from.  I'm using my desk top PC to talk to you.  I have to type info from the laptop to post it on the forum on the PC.  I just typed the results of the second command, it was so long I timed out and lost the whole thing.  I'll try again later.

---

### Post by Yed Ied on 2009-01-24
*-network
description: Ethernet interface
product: 88E8036 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 10
serial: 00:e0:b8:8f:6b:6a
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet
  physical tp 10bt-fd 100bt 100bt-fd autonegotiation    
configuration: autonegotiation=on broadcast=yes driver=sky2 
   driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 
   multicast=yes port=twisted pair
*-network
description: Network Controller
prduct: BCM4318 [AirForce One 54g] 802.11g Wireless LAN 
    Controller
vendor: Broadcom Corp
physical id: 2
bus info: pci@0000:05:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
*-network: DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 26:a2:30:55:39:d9
capabilities: ethernet physical
donfiguration: broadcast=yes driver=bridge driverversion=2.3
   firmware=N/A link=yes multicast=yes

---

### Post by Yed Ied on 2009-01-24
sorry this last post took so long.  I don't type too fast.  I hope this helps to solve the problem.

---

### Post by Yed Ied on 2009-01-24
I'm sorry the [lshw -c network] posting isn't correct.  It should have 4 separate [*-networks] and there are only three.  Typing isn't something I do well.  The [Wireless interface],the one that's missing, is DISABLED, and the [Ethernet interface] is also DISABLED.  I'll go away and leave you all alone if you want, or if any of this is helpful, let me know.

---

### Post by Coinneach on 2009-01-24
Have you got the wireless switch turned on? lol

---

### Post by Yed Ied on 2009-01-24
Don't laugh, nothing would surprise me.  Rgt clk on network manag. shows checks on enable networking and enable wireless.  covering that partially is a small window saying "no network connection".  I like the program, I would like to have all of it.

---

### Post by Yed Ied on 2009-01-25
I'm trying to get these last two [*-network] descriptions in here corectly. 
*-network:0 DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:14:a5:87:f2:3d
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
*network:1 DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: ba:70:fd:f6:86:b3
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3
link=yes multicast=yes

These are the last two network descriptions and thesr are accurate, sorry for the ineptness.

---

### Post by Yed Ied on 2009-01-26
Due to a lot of mistakes I've made trying to type code from these two commands, I have started a new thread, "old problem. new new info".  I hope you can follow me over there. I think I have what you asked for there.
Thanks

---

### Post by Sealbhach on 2009-01-26
Hi, I'm at work at the moment and don't have much time to reply. Firstly, I hope you know you can copy and paste output from the terminal, no need to re-type anything.

It looks like you will need to do the steps suggested in this thread, to install the driver for your wireless connection:

[http://ubuntuforums.org/showthread.php?t=1000367](http://ubuntuforums.org/showthread.php?t=1000367)

Hopefully others can guide you through it if you get stuck.

.

---

### Post by Yed Ied on 2009-01-27
Thanks
I can't get the laptop on my network, so I input your commands, in the laptop, type them to this PC, then copy and paste on the PC, but I'll do what ever I have to.
Thanks again

---


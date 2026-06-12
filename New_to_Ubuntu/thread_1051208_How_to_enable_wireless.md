---
title: "How to enable wireless?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by oddparticle on 2009-01-26
I normally have a wired internet connection, so a couple of weeks ago, I clicked on the network thingie in my notification area, and ticked the "disable wireless" box (it never occured to me that there would be an option to disable it if it was impossible to get it back!). But it now seems I can't re-enable it. The option to enable wireless is there, but it is greyed out and I can't click it. 

How can I enable wireless again?

---

### Post by stchman on 2009-01-26
> **oddparticle said:**
> I normally have a wired internet connection, so a couple of weeks ago, I clicked on the network thingie in my notification area, and ticked the "disable wireless" box (it never occured to me that there would be an option to disable it if it was impossible to get it back!). But it now seems I can't re-enable it. The option to enable wireless is there, but it is greyed out and I can't click it. 

How can I enable wireless again?

What kind of wireless card do you have (chipset)?

---

### Post by oddparticle on 2009-01-26
Oops, double posted.

---

### Post by oddparticle on 2009-01-26
If I put "sudo lshw -C network" into the terminal, I get:

*-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:ca:5e:71
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  

Which probably tells you more about the card than I could :redface:

---

### Post by ugm6hr on 2009-01-26
Irrespective of how you solve this - you should report it as a bug on launchpad.

Network Manager should not behave like that.  I can certainly disable and enable wifi at will.  Perhaps something to do with your chipset / NM version?

---

### Post by oddparticle on 2009-01-26
In case this sheds any light on the problem, I am using Ubuntu 8.10 and have all the current updates and whatnot. So presumably I have the most recent version of NM. I don't know about the chipset.

---

### Post by oddparticle on 2009-01-26
OK, I believe my chipset is ipw3945. According to this page [http://linux-wless.passys.nl/query_part.php?brandname=Intel](http://linux-wless.passys.nl/query_part.php?brandname=Intel) my wireless card ought to work. I think. However, the link given for my wireless card ([http://intellinuxwireless.org/](http://intellinuxwireless.org/)) leads to things that I can make neither head nor tail of.

Also, lspci -v | less
gives me this:


 0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
        Subsystem: Intel Corporation Device 1021
        Flags: fast devsel, IRQ 16
        Memory at efdff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945


Also, I have filed a bug report now.

---

### Post by zerubbabel on 2009-03-04
I have the same problem exactly. But did you find a way to re-enable the wireless via the commandline?

---

### Post by Kareeser on 2009-03-04
```
ifconfig eth1 up
```

Give that a shot? Your device may not be named eth1... check ifconfig for the proper name.

---

### Post by zerubbabel on 2009-03-04
ifconfig just lists eth0 which is the wired connection.

---

### Post by zerubbabel on 2009-03-04
zerubbabel@dz:~$ lspci -nn
.
.
.
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
zerubbabel@dz:~$

---

### Post by zerubbabel on 2009-03-04
Ah ha! Found the problem. How embarrassing. There's an external switch on the edge of this laptop that I never knew was there, which turns the wireless on and off, and I must have bumped it a few days ago.

---

### Post by 3rdalbum on 2009-03-04
> **zerubbabel said:**
> Ah ha! Found the problem. How embarrassing. There's an external switch on the edge of this laptop that I never knew was there, which turns the wireless on and off, and I must have bumped it a few days ago.

Don't submit a bug report :-D

---


---
title: "b43 crashes my system"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by faldrien on 2008-04-26
I'm having a very strange problem.  My computer works fine for 10-20 mins after I turn it on and then it freezes.  The first thing that goes during a freeze is the internet, and if I can manager to get a dmesg to run before it's completely unusable i see b43 giving PHY transmission errors and multiple messages saying printk: X messages surpressed.  The highest number of messages I've seen surpressed is 90,000 and I think that's my problem.

I'm running hardy, and have a supported chipset (well bcm43xx used to work flawlessly and before it crashes so does b43)

---

### Post by Ozor Mox on 2008-05-04
I have this exact problem with the b43 driver. First the wireless internet drops, then the system load shoots up, then the system slows to a crawl and finally freezes. Only a hard reboot sorts it. Previous versions of Ubuntu using the bcm43xx driver worked fine.

---

### Post by Ayuthia on 2008-05-04
There are problems with the 14e4:4312 rev 02 and 14e4:4311 rev 02 chipsets (you can check yours by typing lspci -nn in a terminal) using the b43 driver.  If you fall under this category, ndiswrapper is most likely your option.

Here is a link for the 4312: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
Here is a link for the 4311: [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

### Post by toucher5 on 2008-10-08
I have:
 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

and I get the PHY transmission error. It hasn't caused any problems that I have noticed. In fact the computer I am on is my laptop and it is using the internet fine. I would like to know how to make that quit showing and maybe even understand what it means.

---

### Post by gargouille on 2008-11-25
I had a similar issue:

> **gargouille said:**
> HARDWARE:
Dell Latitude D600
Broadcom BCM4309 (bcm43xx)


PROBLEM:
Wireless connection disconnects.  When shutting down, or rebooting, the following error appears and keeps repeating:  b43-phy0 ERROR: PHY transmission error

kern.log entry:
Nov 25 18:25:57 coruscant kernel: [   92.216246] wlan0: no IPv6 routers present
Nov 25 18:26:02 coruscant kernel: [   96.820027] __ratelimit: 386 callbacks suppressed
Nov 25 18:26:02 coruscant kernel: [   96.820027] b43-phy0 ERROR: PHY transmission error


FIX:
found in Ubuntu help:

3.3.6.&#8195;IPv6 Not Supported

   1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
   2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
   3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
   4. Reboot Ubuntu.

---


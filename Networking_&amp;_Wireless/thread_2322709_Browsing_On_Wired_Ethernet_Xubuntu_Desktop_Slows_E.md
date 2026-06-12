---
title: "Browsing On Wired Ethernet Xubuntu Desktop Slows Entire Network To A Halt"
date: 2016-04-29
forum: Networking &amp; Wireless
---

### Post by steevven12 on 2016-04-29
Hello all!

**Description of problem:** I have a freshly installed copy of Xubuntu 16.04 running alongside Windows 7 on a Dell Inspiron desktop, connected directly to my WiFi router via ethernet cable. When I browse the Internet on this computer with Xubuntu, the Internet quickly becomes EXTREMELY, unusably slow for everyone on the entire network. Turning the computer off clears up the entire network. Previously, I was using Xubuntu 15.10 with the same setup (no dual boot), and the network connection was 100% fine. When I reboot into Windows 7, the connection is also 100% fine.

**Hardware details:** Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe (rev 01)

**Attempted solutions:** Disabled IPv6, which had no effect. Tried different browsers, which had no effect. Also, one might think that this machine is just hogging all the network bandwidth with some background process, but I find this very very unlikely, because this is a fresh install of Xubuntu.

**ANY HELP GREATLY APPRECIATED. Thanks in advance.**

---

### Post by steevven12 on 2016-05-01
I just wanted to check in and say that this problem is extremely consistent. The moment I start browsing on this desktop, everyone in the house complains that their Internet connection has stopped working. The INSTANT that I click "shut down" on the desktop, everyone's pages begin loading. I've never seen anything like it before.

Willing to try anything and report back!

---

### Post by steevven12 on 2016-05-05
One last bump...I have made no progress and don't know what to do :(

---

### Post by steevven12 on 2016-05-10
SOLVED: Surprisingly enough, this had nothing to do with software. I was routing my ethernet cable through my surge protector. When I switched it to go directly from NIC to router, the problem vanished. Still really strange...

---


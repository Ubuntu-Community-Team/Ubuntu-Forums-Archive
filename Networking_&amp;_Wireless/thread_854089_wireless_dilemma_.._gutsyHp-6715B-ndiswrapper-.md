---
title: "wireless dilemma .. gutsyHp-6715B-ndiswrapper-"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by denarced on 2008-07-09
I installed xp first
Ubuntu 7.10 gutsy second
didn't really do anything after xp installation ( no drivers none whatsoever )
got wireless working perfectly by following:
[http://www.linlap.com/wiki/Configuring+the+ndiswrapper+driver+for+wireless+controllers+without+native+Linux+drivers+in+Ubuntu+7.10]("http://www.linlap.com/wiki/Configuring+the+ndiswrapper+driver+for+wireless+controllers+without+native+Linux+drivers+in+Ubuntu+7.10")
Then I installed all the drivers and stuff for XP
after that my wireless doesn't work
re-installed gutsy and followed the same guide
doesn't work
why ?
is it possible that the installation of xp made this happen ?
sounds kind of impossible ..
how to fix it is the real question ..

some specific info to follow :

$ lcpci ( only listed the necessary )
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

that's all I can think of
I'll be checking this thread all the time
Any help and/or tips would be great

---


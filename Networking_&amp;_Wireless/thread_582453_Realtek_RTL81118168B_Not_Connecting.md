---
title: "Realtek RTL8111/8168B Not Connecting"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by MenZa on 2007-10-19
I'm having some problems with my on-board Realtek RTL 8111/8168B-based network not working - it doesn't connect at boot very often, and when it does, it quickly loses the connection, especially when doing something traffic-heavy (e.g. using aptitude, or update-manager).

I've had this issue before, under Feisty (I'm Gutsy), but it appeared to just solve itself then. It hasn't on Gutsy, and I've run it since Tribe 3 (I've re-installed twice completely, most recently with the final version).

I'm informed by lspci that my network card is:

```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet Controller (rev. 01)
```

This is on an ASRock ConRoe 945G-DVi motherboard. Relevant info from my dmesg could be, that I get "r8169: eth0: link up" at boot, and shortly after losing my connection, I get "NETDEV WATCHDOG: eth0: transmit timed out".

I am behind a 3Com switch---not a router.

I know there are some issues with dual-booting Windows and Ubuntu with this card, but for clarity, I'm running Ubuntu exclusively on this machine. Any help is highly appreciated.

**Edit:** This issue was never resolved, but I have gotten it working by installing a fresh LAN card. If anyone knows how to solve this anyway, help is highly appreciated.

---

### Post by Lusen on 2008-01-01
I have the same problem. I hade to install a new NIC.
I think it is a bug in the RTL8169 driver.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343)

---

### Post by deanfred on 2008-01-20
I have the same problem with my Gigabyte GA-G31M-S2L motherboard which uses the 8111C.    The Realtec site has an updated driver, which is not the same as the r8169 (it's an r8168 series driver).  I think this Linux kernel is using the wrong (or old) driver.  I have the driver (you can D/L it from Realtec's site.  Do you know how to correctly replace the driver in Ubuntu?  I don't.  Here's my link
[http://ubuntuforums.org/showthread.php?t=671614](http://ubuntuforums.org/showthread.php?t=671614)

If you do a search on 8168, there's another person with the same problem.

Let me know if you know how to replace the driver.  The link on the Realtec site is buried and really hard to find.  Here it is:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

Good luck!
Dean

---

### Post by Raptor Ramjet on 2008-05-31
Sadly I too am having networking problems with a Realtek RTL8111B/RTL8111C.  I've got an Asrock AliveDual-eSATA2 board which uses this for its onboard LAN and networking works under Feisty, works under Gutsy but fails under Hardy.

Whatever the problem is it's currently a network showstopper for my machine.

Even worse for some reason a UUID hasn't/doesn't get generated for one of my partitions (which contains "/home" so is needed !) so now I have to edit my "/etc/fstab" whenever I want switch between booting from either my installed Gutsy or Hardy kernels.

This is due to the device name for my first ATA drive changing  from "/dev/hda" under Gutsy to "/dev/sdb" under Hardy.  Most perplexing as running "blkid" shows UUIDs for all my other partitions apart from this one partition ?

And... after the upgrade X no longer works properly under Gutsy (which I suspect is due to me using the Nvidia driver) so I now have a "really great" choice.

1  Boot into Gutsy with an 800x600@60hz monitor resolution, and quickly get a headache as I can actually see the monitor strobing or...

2  Boot into Hardy and "enjoy" a totally network free experience.

All in all Hardy has been a total disaster for me :(

Oh well at least those kind devs will fix it sooner or later !

---

### Post by xolot1 on 2008-06-01
hi, ive been having the exact same troubles as you guys. i was going to pick up a $5 NIC off ebay, although im disappointed to hear noboby's found a fix.


you mention that networking goes ok under gutsy, but not under hardy. perhaps ill clean install gutsy, since i can live without the few new features of hardy (i use kubuntu anyways...).

let me know if i can do anything to help - send me a PM or something


edit: according to the first post, perhaps reinstalling wont be effective, but ill try anyways.

---

### Post by koshari on 2008-06-11
i was/are looking at getting one of these GA-G31M-S2L boards, however i think i may instead get an p5kpl-cm.

both seem to have network issues however so its unfortinate as they both seem very affordable linux platforms.

---

### Post by maryyeta on 2008-06-12
On last monday I bought the medion sim2120 notebook with this network card. 

I managed to compile and install the Realtek drivers for this card (RT2860STA), but although ubuntu 8.04 recognizes the interface (and iwlist scan shows my wifi network, and its features) I'm still unable to connecting to the router. 

Any ideas?

Thanks in advance...

---

### Post by kiev on 2008-07-04
I write script to fix it -> [http://sys-admin.org/files1/r8168-fix.tar.gz](http://sys-admin.org/files1/r8168-fix.tar.gz)

---


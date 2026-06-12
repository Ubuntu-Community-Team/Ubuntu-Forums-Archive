---
title: "8139 (wired) ethernet cards died with recent updates?"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by professordes on 2007-07-14
I have 2 machines - an ASUS Spresso and a Soltek Qbic - with onboard  RealTek 8139 ethernet chips which had been running Feisty quite happily. After some recent updates the ethernet on both has stopped working (i.e.  no connectivity) with "netdev watchdog:  eth0:  transmit timed out" errors. The problem appears with both
the generic and lowlatency 2.6.20-16 kernels, but I'm not sure if it was a recent kernel update or something else
which has triggered the problem.

lspci says  I have  RTL-8139/8139C/8139C+ (rev10) chips.

Adding additional 8139 PCI ethernet cards in either machine gives the same errors on the added cards and fiddling around with acpi and irq boot parameters has had no effect.

Has anyone else run into this in the past few days?

---

### Post by professordes on 2007-07-15
The following module parameter (forcing the card to half duplex) restores connectivity, albeit at 10Mbps:



modprobe 8139too media=0x01

---

### Post by professordes on 2007-07-15
The following also does the trick (at 100Mbps) :

ethtool -s eth0 speed 100 duplex half autoneg on


it looks like half duplex now needs to be forced for some reason?

---

### Post by professordes on 2007-07-15
Hmm - I spoke too soon, I can't get the cards to work reliably with either of the "fixes" - sometimes
it works, sometimes it doesn't......

---

### Post by saphyrre on 2007-09-20
Hello

I have a (somehow) related problem; after the update to the 2.6.20-16 kernel, my ethernet card stopped working. No dhcp, i even set it to static and can't ping anything else but localhost.
I have the realtek 8139too driver installed.
Funny thing is that i have traffic (tx/rx packets) on the "locahost" but no packets on eth0!!
Same pc, same ethernet card, same ethernet cable, everything works great when i boot the pc in vista.
When running dhclient eth0 i get the "no leases offered" (or something similar, i'm at work right now and don't remember the exact message).

Can't ping anything but localhost, can't ping the pc from other pc, no "activity" led on the network card.

But localhost still show packets transmitted/received..

Any help would be appreciated.

---

### Post by bollix47 on 2007-09-20
I had a similar problem recently and found a solution that worked for me.  

Basically, shutdown your computer and remove the power cord for 30 seconds.

As soon as I booted back up the connectivity light came back on.

Prior to that I had rebooted numerous times, changed cables and ports on the router, but the problem would not go away until all power was removed from the computer.

Good luck.

---

### Post by saphyrre on 2007-09-20
Thanks for the idea, will try it as soon as i get home.

---

### Post by fjames on 2007-09-20
We have this same discussion going in another thread.  No answers there either.  I didn't install an update, just a fresh install with the latest version. I have the same issue. Are you using DHCP or static?

---

### Post by saphyrre on 2007-09-20
Ok, i did turn off the pc, unplug the power cord, and turned everything back on. It freaking works!!! Have no idea why, but it does work.
I wonder what exactly is causing this, doesn't seem to be related to dhcp/static, since it didn't made any difference before. I spent about 4 hours yesterday trying to find out what the problem is. 
Is this caused by an update? If yes, which one? Unfortunately i'm no "guru", i just have the basics.

Anybody got an answer to this problem?..or maybe a explanation of what if going on? I repeat, everything was working fine until a few days ago, when i did some updates (also reinstalled faad2 with all those dependencies, but this is probably not related to this).

Here is some info:

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


eth0      Link encap:Ethernet  HWaddr 00:13: D4:C8:A1:F5  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fec8:a1f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1675509 (1.5 MiB)  TX bytes:226443 (221.1 KiB)
          Interrupt:20 Base address:0x6400 

[    3.620548] eth0: RealTek RTL8139 at 0xf8826400, 00:13:d4:c8:a1:f5, IRQ 20
[    3.620553] eth0:  Identified 8139 chip type 'RTL-8101'
[   13.146997] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   30.489355] eth0: no IPv6 routers present

iface eth0 inet dhcp
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1

---

### Post by fjames on 2007-09-20
OKay, here is anew discovery.  After working with the FS for a short while, creating TAR backups, etc, it stops working. This is probally unrelated, I'm not sure.  If I do nothing it comes back to life in about 5 minutes. During the time it's down I have tried to discover what process are running or not running that could cause this.  I found nothing so far except all process but PS seem to be getting no cpu time.  It's odd that it starts working on it's own.

---

### Post by noob12 on 2007-09-21
See this thread [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by fjames on 2007-09-21
I read the link you posted.  This is not the problem I'm having. In my case the NIC seems to go to sleep an then wake back up a few minutes later.  If I down the interface and bring it back up I'm back in business instantly. It doesn't seem to be related to any brand or model of NIC. I have tried several.  What investigation I have done leads me to believe that all network related processes stop for a short time or another process hogs the CPU time.  I have not been able to isolate it.

---

### Post by fjames on 2007-09-22
I may not have figured out what was causing this problem but I may have found the cure at least for me.  I updated my installation. It downloaded 108MB of updates. I rebooted and have been running without a problem. :)

---

### Post by deroldj on 2007-09-22
have the same issue , after installing updated Ubuntu. I also have a wired 8139 ethernet, which works in windows fine but on same machine will not work in ubuntu, I have tried all I can think of, and have posted here under internet not working.

---

### Post by saphyrre on 2007-09-27
> **deroldj said:**
> have the same issue , after installing updated Ubuntu. I also have a wired 8139 ethernet, which works in windows fine but on same machine will not work in ubuntu, I have tried all I can think of, and have posted here under internet not working.

Did you try unplugging the power cord from pc for 10 sec, then booting ubuntu again?

Note: i found this link which has some interesting details...unfortunately seems like there is no fix for this...yet.

[http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)

---

### Post by SpiritIsReality on 2007-09-29
howdy
thankyou for being here
found this thread in a search 
read this thread and noob12 thread.
thankyou  again.

[http://ubuntuforums.org/showthread.php?t=559895](http://ubuntuforums.org/showthread.php?t=559895)
:popcorn:=D>:-({|=

---

### Post by saphyrre on 2007-10-01
Thanks for the info. However, i have Vista Business, and there is no such thing as "Wake on Lan after shutdown" option in "Advanced" section of my Realtek nic.

---

### Post by SpiritIsReality on 2007-10-02
howdy
> saphyrre 	 		**Re: 8139 (wired) ethernet cards died with recent updates?**
 Thanks for the info. However, i have Vista Business, and there is no such thing as "Wake on Lan after shutdown" option in "Advanced" section of my Realtek nic.
I think it depends on what driver you have for your network card. I have an old
driver, wxp ,and I have no Wake on Lan after shutdown option in Advanced section either. I'm thinking that if the option is not there, it's not going to be a problem.
buds

---


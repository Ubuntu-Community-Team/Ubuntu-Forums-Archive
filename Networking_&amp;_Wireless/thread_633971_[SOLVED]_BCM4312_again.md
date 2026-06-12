---
title: "[SOLVED] BCM4312 again"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by Neo¹ on 2007-12-07
Hi All,

I have tried to configure my WiFi card (BCM4312 rev 2) on my laptop HP Pavilion dv9000. I have read in between many (realy many) howtos and articles but I cannot get it work.
When I use the bcm43xx module, after I start the laptop  my CPU running high and the top process is the software IRQ deamon (ksoftirqd). When I restart the network over Network Manager (switch to offline than switch to online) the CPU starts to work normal but the card still does not work. It is to see in iw(f)config but scanning give no results. Also manually configuration essid/key/etc does not help.

When I insert the bcm43xx module manually the dmesg give follwing errors:

```
[  658.220915] ieee80211_crypt: registered algorithm 'NULL'
[  658.226672] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  658.226678] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  658.248525] bcm43xx driver
[  658.248943] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 16
[  658.248953] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 16 (level, low) -> IRQ 16
[  658.248964] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  658.251679] bcm43xx: Unsupported 80211 core revision 13
[  658.252452] bcm43xx: Invalid PHY Revision 9
[  658.453228] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  658.457838] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  658.475714] bcm43xx: MAC suspend failed
[  658.491563] bcm43xx: MAC suspend failed
[  658.506726] bcm43xx: MAC suspend failed
[  658.521864] bcm43xx: MAC suspend failed
[  658.537011] bcm43xx: MAC suspend failed
[  658.552139] bcm43xx: MAC suspend failed
[  658.567350] bcm43xx: MAC suspend failed
[  658.582439] bcm43xx: MAC suspend failed
[  658.597567] bcm43xx: MAC suspend failed
[  671.109014] printk: 4 messages suppressed.
[  671.109019] bcm43xx: MAC suspend failed
[  671.124137] bcm43xx: MAC suspend failed
[  671.139278] bcm43xx: MAC suspend failed
[  671.154447] bcm43xx: MAC suspend failed
[  671.169581] bcm43xx: MAC suspend failed
[  671.184729] bcm43xx: MAC suspend failed
[  683.742635] printk: 7 messages suppressed.
[  683.742640] bcm43xx: MAC suspend failed
[  683.751024] bcm43xx: MAC suspend failed
[  683.750589] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  683.750604] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  683.750615] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  683.750625] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  685.885836] printk: 223544 messages suppressed.
[  685.885841] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  687.989141] printk: 233221 messages suppressed.
[  687.989147] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  690.102798] printk: 219713 messages suppressed.
[  690.102803] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  692.195766] printk: 214366 messages suppressed.
[  692.195773] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  694.299074] printk: 225636 messages suppressed.
[  694.299079] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  696.420696] printk: 224346 messages suppressed.
[  696.420701] bcm43xx: MAC suspend failed
[  698.556171] printk: 210612 messages suppressed.
[  698.556176] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  700.659489] printk: 204140 messages suppressed.
[  700.659494] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  702.762797] printk: 210514 messages suppressed.
[  702.762803] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  704.866125] printk: 209784 messages suppressed.
[  704.866130] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  706.969433] printk: 226568 messages suppressed.
[  706.969438] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  709.099469] printk: 201484 messages suppressed.
[  709.099474] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  711.213080] printk: 207468 messages suppressed.
[  711.213085] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  713.316377] printk: 227830 messages suppressed.
[  713.316381] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  715.419690] printk: 224525 messages suppressed.
[  715.419695] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  717.522999] printk: 222469 messages suppressed.
[  717.523004] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  719.626313] printk: 212500 messages suppressed.
[  719.626318] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  721.729628] printk: 209043 messages suppressed.
[  721.729633] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  723.832932] printk: 222439 messages suppressed.
[  723.832937] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  725.936233] printk: 241553 messages suppressed.
[  725.936238] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  728.039530] printk: 251132 messages suppressed.
[  728.039535] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR

```
I've tried also with Ndiswrapper with several Windows (vista, xp, 64 and 32 bit) drivers but it does not work at all.
BTW: This card seems to work under Vi$ta. I've raed that the bcm43xx module is deprecated and there is new driver but it seems to be included in the Kernel 2.6.24 first so I think I will be able to try it out first with the next Ubuntu version :(
Has someone any idea what the problem could be.

---

### Post by Neo¹ on 2007-12-09
I have installed Fedora 8 to test and indeed with the b43 module this card works perfectly.
Maybe I should use vanilla kernel :(

---

### Post by weblordpepe on 2007-12-11
My DMESG is full of that
I have:
> bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
 over and over again.

---

### Post by mc-rpg on 2007-12-13
I have the same problem on a HP dv2423la :(

I have a question for you, did you install the driver with restricted manager and still it doesn't work? I did so and it isn't working :(

---

### Post by weblordpepe on 2007-12-15
I installed with the restricted manager yeah :S

---

### Post by mc-rpg on 2007-12-15
It seems to be a problem with the current 43xx drivers, I think in Gutsy we use bcm43xx but there's a newer one called b43xx, the thing is that in the *.24 version of the kernel this problem seems to be solved, I'm trying another distros to see what happens.

---

### Post by Neo¹ on 2007-12-15
I have also installed the restricted "driver".
Maybe I'm wrong but I believe that the manager installing only the firmware in this case.

---

### Post by csat on 2007-12-15
I am running wireless device DI-624 router with Dell notebook 131 L and 43xx wireless card.
I followed those steps on the link below and succeeded on keep my wireless up and running without problems.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Now using Linux Mint 4 (Ubuntu) and also installed wicd as a network manager.  See it at [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Good luck

---

### Post by Neo¹ on 2007-12-16
> **csat said:**
> I am running wireless device DI-624 router with Dell notebook 131 L and 43xx wireless card.
I followed those steps on the link below and succeeded on keep my wireless up and running without problems.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Now using Linux Mint 4 (Ubuntu) and also installed wicd as a network manager.  See it at [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Good luck


I cannot believe it. It works now.
The story:

I have tried this how to before but it didn't work me. Now I know why. After the script is executed the user will request to reboot the computer. I've done it and it didn't work.

After You've posted this solution here, I though I try it again. But this time before I've booted I have checked if something has been changed. And indeed, after the installation I saw the WiFi card but after reboot it's disappeared again.   
 
The problem is, I think, that I've installed the normal ndiswrepper before and it add new file to the /etc/modprobe.d
So I comment out this (only) line: > alias wlan0 ndiswrapper in the /etc/modprobe.d/ndiswrepper rebooted and it works great now.

Many thanks.
Now I need only get the hibernate to work :)

Kind regards,
Neo

---

### Post by Cybermax on 2007-12-16
I have a Compac 6502EO laptop, and the BCM4312 Rev2 chip.. And i tried the fedora livecd to see if the card would come alive with the B43 driver, but nothing happens at all..

I also tried to compile a vanilla 2.6.24 kernel with the b43 module, but the card is not enabled at all.. When i do a modprobe b43, or anything related to this, the module gets loaded, but there is no message at all indicating anything starting up.. ie. no IRQ or nothing at all..

Very weird.. I even patched the kernel with the latest GIT patches found on kernel.org, but still nothing.. And the other part is that its just the same that happens with Fedora b43 module.. Does not look like the hardware id's are there at all tbh..

I got the ndiswrapper method to work straight away with no problems tho, but id really want to get this to work with a native linux kernel driver, and not some half-way windows driver :P (After all.. we use linux for a reason.. no? hehe).

Straight up Ubuntu install gives the exact same problem as the OP in this thread, but something weird is making the b43 driver also fail with my card.. Any hints?

C

---

### Post by Flare183 on 2007-12-16
Firmware and fwcutter files are attached.

---

### Post by csat on 2007-12-16
> **Neo¹ said:**
> I cannot believe it. It works now.


Many thanks.
Now I need only get the hibernate to work :)

Kind regards,
Neo


Great.  I am happy that you sorted out your problem.  Don't forget to assign SOLVED to it.

Regards
Csat

---


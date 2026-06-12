---
title: "Realtek 8168 not getting DHCP lease"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by prozaconstilts on 2007-03-06
Hello,

I have just installed Edgy on my Asus P5B motherboard with an integrated Realtek 8168/8111 PCI-E network card. The r1000 module loads, as evidenced by lsmod, and the card is recognized in my Network Settings. Unfortunately, I do not have any network connectivity. The output of ifconfig has no IP address or any other fields set by DHCP.

dhclient broadcasts a DHCPDISCOVER, but never gets any replies.

This machine and my laptop use a linksys WRTP54G router as their gateway to the internet, and the laptop, running Dapper, and with a Broadcom network chip (I can't remember which one at the moment) gets a DHCP lease with no problem.

My edgy machine running in Windows also gets a DHCP lease with no problem.

I did notice in Windows that auto-negotioate of the line speed failed, and I never got a DHCP lease if it was on. If I manually set the line speed at 10 or 100 Mbps, then it could get a DHCP lease fine. I figured I may need to do the same in Edgy. 

The README with the r1000.ko from Realtek has the following:

#insmod /path/to/r1000.ko speed=10 duplex=1 autoneg=0 to set the module to 10Mbps full duplex and no auto negotioation.

I removed r1000.k0 using rmmod, and then attempted to insert using the line above (with sudo), but I got an error saying the options I was attempting to pass in were unrecognized. I am not at my Edgy machine right now, but I can post the exact error once I am.

Has anyone else seen this problem? Or does anyone know another way to manually set the line speed? Or does anyone know if there is something else going on?

UPDATE: I was able to load the module at 10mbps, and it actually worked, but the bit rate fluctuates from mere bytes/sec to  several hundred kilobytes/sec...any thoughts?

Thanks!

Adam

---

### Post by prozaconstilts on 2007-03-06
I forgot to mention:

Setting everything statically didn't work either...

---

### Post by ubrox on 2007-04-24
I am having the same problem. I am able to load r1000 driver but it doesnt get IP from DHCP. I checked the DHCP server and it is handing out an IP but the system is not taking it. ANyone know whats going on?

Thanks,
Kalyan

---

### Post by r.k.maroon on 2007-05-27
I'm encountering a similar problem:

I've tried the module from realtek (the one i could find was called 8168 ), built it and can insert it into the kernel alrigt, as evidenced by lsmod.  However, only r8169 or r1000 driver will bind and give an eth0.  

I tried the r1000_v1.5 module as well, but with the same result.

dmesg has a line that says "NO LINK", so the cable isn't linking.  I've tried using a twisted cable just to be thorough. Works fine in windows, but also worked fine in a previous feisty installation that i moved from another box (ie that machine had completely different hardware but was able to detect and install when i put the harddrive in the new machine). I've tried with the modules that I suppose where running on that installation, but none of them would bind and give an eth0.

Anyone have any luck with these issues? 

I'm running on an asus barebone with a G965 intel chipset and realteks 8168/8111 PCI-E Gigabit on-chip controller.  Really weird that it was working before I reinstalled.

UPDATE:

I found the reason for my problems; an IRQ problem!

For me, the IGP and eth0 shares IRQ and the conflict causes the ethernet controller to not link.  My fix was kind of weird, since BIOS fiddling with IRQ's and ACPI and whatnot didn't help.  I installed on the old system and then moved the disk, meaning the ethernet was detected as eth2 and got IRQ 16 instead of 17.  Everything started working fine then.   A bit odd that a previous installation on an almost identical box assigned a different IRQ (Feisty Fawn 7.04, bot Alternate and Desktop).

afterthought:
I've been installing and reinstalling systems for two days now, but I might try another reinstall and see if irqbalance might solve the issue.  Not sure if irqbalance will accomplish anything on a dual-core, but on an old dual athlon mp machine it did away with all irq-woes.

---

### Post by mx-5 on 2007-05-28
Thanks for the tip on irqbalance.  I'll give that a shot tonight.

I had Feisty working with my Asrock Conroe945G-DVI onboard 8111/8168 nic.  I did a BIOS upgrade, and poof, my NIC stopped with similar symptoms as mentioned.  I reverted back to the old BIOS and still no go.  I had a hunch it was IRQ, but couldn't find a way to change that in my BIOS.  Hopefully this will fix my nic issues...

---

### Post by tualatrix on 2007-07-16
There's the same problem with my 8168 and Feisty...

I've given up to try my computer work with Feisty, I will try Gutsy.

Now downloading the ISO of the newest Gutsy images.

---

### Post by najames on 2007-08-12
I had a similar problem on a TA690G board with this onboard NIC.  I had WinXP installed temporarily and then when I installed Feisty, the network was "dead".  It didn't matter if the cable was unplugged or not.  I read something about WInXP putting the NIC to sleep.  On a hunch I unplugged the power to the computer, waited a couple minutes, plugged it back in and the router assigned the address immeditately.

---


---
title: "realtek 8185 wireless + ndiswrapper.  I missed a step or something."
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by nintennuendo on 2007-07-07
So, I installed Ubuntu before, but I couldn't get my USB hard drive to work so I went back to XP.  Now,  I got the NTFS USB to work,  but I can't get my wireless to work now.  I have a RealTek 8185 wireless card, I have the windows drivers, and I have ndiswrapper.  I go to install the drivers, but nothing happens, doesn't tell me they're invalid, doesn't tell me it worked, because it did not, just nothing.  They worked before so I KNOW I *can* get it to work, I just must've missed a step or two.  Any help would be greatly appreciated.

---

### Post by panurge77 on 2007-07-07
> **nintennuendo said:**
> So, I installed Ubuntu before, but I couldn't get my USB hard drive to work so I went back to XP.  Now,  I got the NTFS USB to work,  but I can't get my wireless to work now.  I have a RealTek 8185 wireless card, I have the windows drivers, and I have ndiswrapper.  I go to install the drivers, but nothing happens, doesn't tell me they're invalid, doesn't tell me it worked, because it did not, just nothing.  They worked before so I KNOW I *can* get it to work, I just must've missed a step or two.  Any help would be greatly appreciated.

Did this driver work WITH network manager? I had to disable network manager to use ndiswrapper with both rtl8180 and 8187

---

### Post by blegs38552 on 2008-04-12
Using this reply to bump up this problem rather then create a new one.

I have a Gateway laptop with a RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller as seen in Device Manager.

Whenever to try to connect wireess, my laptop freezes up and the Cap Lock lights blink on and off. Only cure is a hard shutodwn. Controller works fine in VISTA - this is a dual boot machine.

Tried installing drivers using NDISWRAPPER - no luck. 

I would like tohear from someone with a similar setup and to know that he/she got this to work, step by step. I am a newbie, but I did try installing some drivers only to get the same results. This is a secured (WEP) network, got same resuts with WAP. Currently, there are no drivers installed (ndiswrapper -l returns nothing).

Again, step by step, what do I have to do. What drivers should I be using, and where do I get them?

Thank you.

---

### Post by Pasto on 2008-06-30
I was trying today to guide a phone installation for the win98/me 8185 drivers with ndiswrapper. it was kinda like

sudo ndiswrapper -i net8185.inf 
sudo ndiswrapper -m
sudo modprobe ndiswrapper

ctrl+alt+backspace
relogin, and now in networkmanager the wireless are visible. 

so we put ndiswrapper in /etc/modules so the driver can be loaded at startup, and the user gets a blank screen and no boot. I have no idea what it said and the user said he couldn't see the problem. We removed it from /etc/modules, computer boots normally. install ndisgtk, remove the driver, add it again, reboot, error again, but ndiswrapper is not in /etc/modules, so had to blacklist ndiswrapper in /etc/modprobe.d/blacklist

I'm going to his house tomorrow night to check wth is going on, but i guess it COULD be the driver (98/me instead of xp?), however, why did it work running sudo modprobe ndiswrapper from gnome-terminal, but doesn't work at startup? :(

/edit

btw, this was in hardy

---


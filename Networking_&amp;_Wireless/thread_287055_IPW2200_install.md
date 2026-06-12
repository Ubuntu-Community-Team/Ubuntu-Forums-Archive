---
title: "IPW2200 install"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by Nirva on 2006-10-28
Hellow,

I have Ubuntu 5.10 on a Dell Inspiron 9300 ( 1.73 Ghz, 1 GB Ram ) and I'm trying to install ipw2200 drivers.  I am a complete noob in Linux so I tried folowing [this]("http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu") manual.
I am able to install Wireless-tools and the linux-headers ( what is there purpose actually? ) but when I run module-assistant and I click select, ieee80211 is not in the list.  I tried updating already but I didn't work.

Thank you for your help.

Ps : When you explain something, remember that I don't know shit about Linux ;-)

---

### Post by KingArthur10 on 2006-10-28
You shouldn't have to install the drivers.  They are automatically included and installed by default.  Click on your system, admin, network and it should have a wireless interface already there.  If not, fire up the live CD and check there (you may have lost it after tinkering with trying to install drivers already included, I dunno).  If the wifi card is already working, you should be able to click properties and search for a network that way, or install network-manager-gnome to have a nicer interface.  IPW2200 drivers work out of the box for me, my wife, and my brother.

---

### Post by sshyperion on 2006-11-21
I am having roughly the same problem.  Wireless access was working fine today before I tried to "update" the 2200BG drivers and now wireless access is no longer working (as in eth1 is not being detected in network manager).  How can I revert back to the setup that was working perfectly fine before I showed up and kinked things up?

---

### Post by yeehawjared on 2006-11-22
I have an inspiron 9300 built in with IPW2200.  Dapper worked perfectly out of the box.

Edgy doesn't work out of the box... the IPW2200 is detected, but the kill switch is enabled.  I can't turn off the kill switch (function + f2).  please refer to this problem:

[http://ubuntuforums.org/showthread.php?t=303135&highlight=ipw2200](http://ubuntuforums.org/showthread.php?t=303135&highlight=ipw2200)

---


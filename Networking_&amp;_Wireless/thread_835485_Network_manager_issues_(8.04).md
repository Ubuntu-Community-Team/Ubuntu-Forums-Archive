---
title: "Network manager issues (8.04)"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by draconianheart on 2008-06-20
I have a friend who owns a Compaq Presario C700T series laptop that has a Broadcom wireless card (BCM4311). I installed Ubuntu 7.10 on her computer a while ago and got the wireless working fine with ndiswrapper (though it took me a while since I have only been using Ubuntu for a year now) and there were no problems. However, I recently (two days ago) told her to upgrade to 8.04, not really thinking about her wireless card. After struggling for a few hours over instant messaging, we were able to get ndiswrapper and b43-fwcutter installed and her wireless card light is blue and the drivers show up as installed. I thought that meant I was done, but alas, it was not meant to be. Now her network manager isn't working.

She's tried reinstalling the packages (network-manager and network-manager-gnome) and checked to make sure nm-applet was in the startup programs, but it refuses to show up. I should mention that she is new to Ubuntu and not very comfortable with the command line, so it is pretty important to her that she has a wireless network manager. I don't have access to her computer, but I'll answer any questions about what I've done and she'll answer the rest. Her username on the forums is spiritsongstress.

Anyway, we'd really appreciate help. Thanks in advance.

---

### Post by werries on 2008-06-20
it is revealed by a quick search in synaptic that nm-applet is no longer a package as it was in the old repositories, as the network-manager/nm-applet duo is now network-manager and network-manager-gnome, so telling nm-applet to start will not work even though it is still technically the program. it should be starting network-manager if my guess is right. or network-manager-gnome.

---


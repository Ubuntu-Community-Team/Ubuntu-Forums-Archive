---
title: "high severity issue with NetworkManager in Gusty"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by XProgrammer on 2007-10-22
I'm observing severe issue NetworkManager in gusty. Everything works well until my AP reboots. Once AP reboots due to power disturb, NetworkManger is not connecting to same ESSID. I could see my wireless LED is keep on blinks. Sometime NetworkManager is going into 99% cpu. 

I had to restart NetworkManager and nm-applet to recover. After restart of both, nm-applet is not taking WEP key from keyring manager. It prompts again. Have any one observed similar problem out there?.

---

### Post by Lambert on 2007-10-23
> **XProgrammer said:**
> I'm observing severe issue NetworkManager in gusty. Everything works well until my AP reboots. Once AP reboots due to power disturb, NetworkManger is not connecting to same ESSID. I could see my wireless LED is keep on blinks. Sometime NetworkManager is going into 99% cpu. 

I had to restart NetworkManager and nm-applet to recover. After restart of both, nm-applet is not taking WEP key from keyring manager. It prompts again. Have any one observed similar problem out there?.

Not the exact same but similar. I've had keyring ask to access a couple times in a row before it finally connects.

Network manager still seems buggy and an incomplete program in gutsy.

---

### Post by jkchow on 2007-10-27
Hey guys,

I'm relatively new to Ubuntu but I really love the experience. Like you guys, I'm having major problems with NetworkManager. I have a Dell Vostro 1400 with a Dell 1390 Wireless card, and I used ndiswrapper to install the Windows XP driver for my wireless card. NetworkManager detects wireless access points just fine and it can even connect to open, unprotected access points. However, whenever I try to connect my home router (WEP 64-bit Hex), my computer would crash. I really don't want to run my Windows all the time to check my internet :(

---

### Post by rcatman on 2007-10-28
you should try using wicd. 

[http://wicd.sourceforge.com](http://wicd.sourceforge.com)

It has to uninstall network-manager to install wicd, but it's worth it. Wicd can connect to protected networks. I haven't used network-manager for a while now. Everytime i install a new installation, the first thing i do is install wicd and uninstall network-manager. check it out. if you dont like it, you can just reinstall network-manager and it will uninstall wicd automatically.

---

### Post by jkchow on 2007-10-28
> **rcatman said:**
> you should try using wicd. 

[http://wicd.sourceforge.com](http://wicd.sourceforge.com)

It has to uninstall network-manager to install wicd, but it's worth it. Wicd can connect to protected networks. I haven't used network-manager for a while now. Everytime i install a new installation, the first thing i do is install wicd and uninstall network-manager. check it out. if you dont like it, you can just reinstall network-manager and it will uninstall wicd automatically.

I've actually used wicd and it is a much better program than NetworkManager. However, in my case I don't think wicd is the actual culprit. I've done some research, and it seems that in my situation when my computer locks up after connecting to an encrypted network that my driver does not support encryption. I'm going to do some more research and hopefully I can find an answer.

---

### Post by iv2101 on 2007-10-28
I am running Gutsy on Dell inspiron 1420, but my problems are not as severe. NetworkManager hangs when returning from hibernation or when wireless network connection is dropped. Restarting it solves the problem every time, but it is annoying. 

Is anyone else having these symptoms?

---

### Post by XProgrammer on 2007-11-12
after reading couple of comments from various geeks,today i moved to Wicd to manage my network interfaces. So far it is working good. Hoping that it would solve issues happening with NetworkManager. Happy Networking!.

---


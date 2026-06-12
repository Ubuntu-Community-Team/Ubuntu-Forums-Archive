---
title: "F5D6050 causes something like a gnome crash"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by vartatom on 2007-04-25
First I have to say that I'm using feisty...Now I come to my problem:
If my wlan usb-adapter (atmel chip: at76c503) is plugged in, then dmesg brings this message:

ubuntu/wireless/at76/at76c503.c: 2522: /dev->istate == init failed
ubuntu/wireless/at76/at76c503.c: 2492: /dev->istate == scanning failed

Then Gnome crashes just a minute later and I only can use the console.
I've had a similar problem with a SuSE Linux 9.2. But there was no problem in edgy...
I've tried to resolve this problem, so I remove the network-manager, the avahi-daemon and the atmel firmware, but that changed nothing. Then I tried it with the ndiswrapper, but it doesn't work. After that I found this threat: [http://ubuntuforums.org/showthread.php?t=393892]("http://ubuntuforums.org/showthread.php?t=393892")
But the thing with the blacklist don't work...
I've spent so many hours about this problem, so please help me... And sorry if my english is bad ;)

---

### Post by vartatom on 2007-04-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/108850](https://bugs.launchpad.net/ubuntu/+bug/108850) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Is there nobody who could help me?

---

### Post by vartatom on 2007-05-01
Perhaps I have to compile the 0.12 beta of the atmel-driver, which is used in ubuntu 6.10 and not the new one in feisty. Could anyone explain me how to compile that driver, because it doesn't work if I only use make and make install

[atmel driver]("http://at76c503a.berlios.de/index.html")

Please help me, because I spent so much time on this problem and I want to use feisty...

---


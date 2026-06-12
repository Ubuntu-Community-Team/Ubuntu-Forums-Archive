---
title: "[SOLVED] Gateway M6750 Marvell Wireless"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by vasiliymeshko on 2008-11-11
Hello and Good Evening to everyone

Recently I installed Ubuntu on a friend's Gateway M6750. The laptop has a Marvell wireless card, which I was able to successfully install through ndiswrapper (using instructions found here -  [http://ubuntuforums.org/showthread.php?t=575785&page](http://ubuntuforums.org/showthread.php?t=575785&page) - a very big thanks to everyone!) My issue is that every time I shut down and restart, I have to repeat:

```

sudo depmode -a

sudo modprobe ndiswrapper

```

in order to be able to connect through wireless. Is there a way around this? Any help would be greatly appreciated.

---

### Post by vasiliymeshko on 2008-11-11
I feel like such an idiot. A simple forum search revealed that all I had to is add ndiswrapper to /etc/modules Problem solved.  Kudos to everyone.

---


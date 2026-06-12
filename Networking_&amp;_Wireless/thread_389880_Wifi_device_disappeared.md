---
title: "Wifi device disappeared"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by jjalocha on 2007-03-21
I had my system set-up according to [this guide]("http://ubuntuforums.org/showthread.php?t=367898") and perfectly running. But suddenly, my wireless device seems to have vanished. [FONT="Fixedsys"]sudo iwlist scanning[/FONT] simply doesn't show it anymore. There seems to be many other users with the same problem, but their conditions don't apply to my system.

I have Dell Latitude 131L with a Broadcom Corporation BCM4311, using ndiswrapper.

I can get the device temporarily working with:

```

$ sudo modprobe ndiswrapper

```

But after reboot, I'm left without wifi again. Does anybody know how to fix this definitely?

Does anybody know why this happened, and how to avoid this problem?

---

### Post by spd106 on 2007-03-21
Try appending ndiswrapper to the end of the /etc/modules file.

---

### Post by jjalocha on 2007-03-21
Thanks! That solved it. It's working perfectly after reboot now.

---


---
title: "Screen resolution not saving"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by Rob Maddison on 2009-10-03
Hi,

I've spent a fruitless evening looking at various threads about screen res and am lost.

I'm running a Toshiba Satellite L300 29w which is a laptop with an Intel GMA 4500m Graphics card. I'm using Jaunty 9.04.

Everything works fine out of the box. No real issues apart from one recurring niggle. My preferred resolution is 16:10 or 1280x800. My machine regularly starts at 4:3 or 800x600 and sometimes wont immediately give me a 1280x800 option in System>Preferences>Display.

I've read about something called xorg.conf I think. No idea how to open said file or what to do with it but would love to stop this annoyance.

Sorry to bug folks with a minor issue,

Rob

---

### Post by BinaryFeast on 2009-10-03
To open xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

In the Devices section you should find the resolutions i think, although editing this file may lead to some unexpected results. Be sure to create a backup copy of the file first:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

And if you end up with a crashed X-server upon reboot:

```
sudo rm /etc/X11/xorg.conf && mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

That's all I can help with. There may be better ways, and you may not need to mess with xorg.conf at all.

---


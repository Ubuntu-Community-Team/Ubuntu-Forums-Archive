---
title: "How do I get Network Manager back"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by matches on 2007-08-02
I am trying to get a wireless network set up. I tried setting it up with a manual connection (Network setting window). But now I can't get my regular network manager to come back. Any idea how to get it back. Thanks!

---

### Post by Mark_in_Hollywood on 2007-08-02
If you can get onto the 'net try WiFi Radar. If you can't get on the net and have a memory stick you can download it at a internet cafe onto the stick. It should open once installed on your (now 'net-less) desktop. Give that a try.

Otherwise, back up /home and reinstall. That's all I've got. Sorry.

---

### Post by ugm6hr on 2007-08-02
> **matches said:**
> I am trying to get a wireless network set up. I tried setting it up with a manual connection (Network setting window). But now I can't get my regular network manager to come back. Any idea how to get it back. Thanks!

Go back to the Network setting window and make sure the "Enable roaming" box is ticked.  It should then work again.

....unless you actually uninstalled Network Manager - if so, try:

```

sudo apt-get install network-manager network-manager-gnome
```

If this tells you that it is already installed, then you've probably just removed the System tray applet - if so, try:

```
/usr/bin/nm-applet --sm-disable
```

If that doesn't work, then I'm stuck.

---


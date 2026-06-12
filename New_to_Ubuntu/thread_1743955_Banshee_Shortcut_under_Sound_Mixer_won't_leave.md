---
title: "Banshee Shortcut under Sound Mixer won't leave"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by CajunPirate on 2011-04-29
Upgraded to 11.04 last night which installed Banshee. I'm more of a Rhythmbox user so I uninstalled Banshee using the Ubuntu Software Center. After rebooting, I still get a shortcut to Banshee when I click on my default volume icon on the taskbar. I've searched Synaptic Package Manager, but I can't find anything Banshee related installed. I know it's a tiny problem, but does anyone have an idea?
Cheers!

---

### Post by wojox on 2011-04-29
I had to go into Banshee's plugins to remove it.

---

### Post by CajunPirate on 2011-04-30
Thanks wojox!
This did the trick:
```
rm -rf ~/.gconf/apps/Banshee/
rm -rf ~/.gnome2/banshee/
```
Quick logout and voila!

---


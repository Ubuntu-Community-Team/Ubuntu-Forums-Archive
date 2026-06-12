---
title: "Old graphic interface after mounting /home"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by seymur on 2010-05-04
Hi everybody.
I've just installed Lucid on Koala. I had separate partitions for /home and / (root) on my hard disk. On first run I realized that Lucid created new /home in root and ignored my old /home. Then I changed fstab; I added old /home for mounting.
Now I have restarted and I got my old home mounted, and my old desktop and all other visuals. I want to use new Lucid interface. I don't know how to switch it. The only change to my old interface is the place of the "close-minimize" buttons, but other visuals of Lucid are missing.
I checked Appearance, there is no new themes.
How can I get rid of my old interface?
Thanks for help!!!

---

### Post by warfacegod on 2010-05-04
All of your settings are in /home. When you told Lucid to use your old /home, you also told it to use your old settings. Go into your Home Folder and hit Ctrl+H. That will show you your hidden folders. All of the settings are called ."foldername". Find the one called .themes and delete it.

---

### Post by seymur on 2010-05-04
> **warfacegod said:**
> All of your settings are in /home. When you told Lucid to use your old /home, you also told it to use your old settings. Go into your Home Folder and hit Ctrl+H. That will show you your hidden folders. All of the settings are called ."foldername". Find the one called .themes and delete it.

Thanks for prompt reply.
Yes, I know that Lucid is using my old settings, I have my old desktop and old dockbar thing which is not working now. I deleted .themes folder as you said, now everything is even more crappy :) colors and stuff, I still have old Koala menus.
On Lucid with its new /home I had human themes, now I dont have those. Is it possible to transfer those settings to my old /home (i.e. current home). Or maybe there is some command which restores all the visual settings?

---

### Post by warfacegod on 2010-05-04
Use Synaptic to reinstall your human-icon-theme as well as human-theme.

---

### Post by seymur on 2010-05-04
I got it. I just deleted old panels and other stuff. And installing Human theme from synaptic. Thanks for help. :)

---


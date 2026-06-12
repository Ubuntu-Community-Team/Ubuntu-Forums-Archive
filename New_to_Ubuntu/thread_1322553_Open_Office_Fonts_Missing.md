---
title: "Open Office Fonts Missing"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by dsanjo on 2009-11-11
I started using Ubuntu recently. It's great but for some reason the standard Open Office fonts (Arial, Times New Roman, Verdana and etc...) have disappeared. 

How can I get them back?

Or better yet, how can I do a system restore to go back to a clean version of Ubuntu? I want to start over. I think I messed a few things up by entering codes to install Japanese input (solved).

---

### Post by jnorthr on 2009-11-11
Are you trying a dual-boot setup with a windose partition ? You need to be SURE to copy off any important data before your do a re-install, just in case. Which version did you install ? 9.04 or 9.10 ? Do you have a live CD you can use to start your system ? If so, you can do a fresh install without worrying about side issues like keeping windose happy.

---

### Post by dsanjo on 2009-11-11
I installed 9.10. And I don't have any data on my Ubuntu drive yet, so I should be fine without backing up, since I have nothing to back up. 

I tried to do it with the Live CD but for some reason it won't load. The screen stays black unless I reboot and eject the CD while at the intial Vista or Ubuntu prompt.

---

### Post by luctor on 2009-11-11
> **dsanjo said:**
> I started using Ubuntu recently. It's great but for some reason the standard Open Office fonts (Arial, Times New Roman, Verdana and etc...) have disappeared. 
).

The Arial, Times ,etc ... fonts aren't Open Office fonts, they are Microsoft fonts, so they aren't installed on Ubuntu by default.
You can however install them with the package **ttf-mscorefonts-installer**

[http://packages.ubuntu.com/karmic/ttf-mscorefonts-installer](http://packages.ubuntu.com/karmic/ttf-mscorefonts-installer)

---

### Post by dsanjo on 2009-11-12
I found out how to do it through the terminal yesterday. It would have been a lot simpler to just click on that link though.
Thanks anyway! Open Office is now set up with the fonts I want.

---


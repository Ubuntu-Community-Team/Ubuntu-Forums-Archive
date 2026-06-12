---
title: "Changing Plymouth splash?"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by totalanonymity on 2011-03-16
I've looked around for this answer quite a bit. More than enough to warrant finally just posting for it myself.

Ubuntu 10.10, changing Plymouth splash. 

I've tried various tools (Zorin, Start-Up Manager) and different codes from different people's opinions. I've killed my GRUB twice by doing that! As a beginner, the second time seemed too complicated and I just went and did a clean install.

So, maybe someone can help me out on this, WITHOUT causing me to lose GRUB or anything of the such?

---

### Post by Tweak42 on 2011-03-16
> **totalanonymity said:**
> I've looked around for this answer quite a bit. More than enough to warrant finally just posting for it myself.

Ubuntu 10.10, changing Plymouth splash. 

I've tried various tools (Zorin, Start-Up Manager) and different codes from different people's opinions. I've killed my GRUB twice by doing that! As a beginner, the second time seemed too complicated and I just went and did a clean install.

So, maybe someone can help me out on this, WITHOUT causing me to lose GRUB or anything of the such?

I haven't messed with it much lately but I use [plymouth manager]("http://sourceforge.net/projects/plymouthmanager/").

---

### Post by keroman on 2011-03-16
not sure, but this may help you, hope so.


[https://ubuntugenius.wordpress.com/2010/05/24/switch-between-installed-plymouth-boot-splash-themes-in-ubuntu/](https://ubuntugenius.wordpress.com/2010/05/24/switch-between-installed-plymouth-boot-splash-themes-in-ubuntu/)

:)

---

### Post by totalanonymity on 2011-03-17
@Tweak42: Plymouth Manager didn't work for me, either.

@keroman: Thank you for that link! Very detailed and beginner-friendly. I've known of those two commands from previous searches, but one thing was mentioned that was absolutely crucial: Make sure there's a .script file in the theme in lib/plymouth/themes/X ("X" representing theme's folder name). That .script file is missing from a couple that I tried, causing the hard drive to cease its process during the boot. 

I got my new Plymouth splash up and running! Thanks so much for the replies, both of you. :)

---


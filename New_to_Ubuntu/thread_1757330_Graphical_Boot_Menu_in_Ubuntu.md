---
title: "Graphical Boot Menu in Ubuntu??"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-13
Folks, is there a graphical menu in start up menu in Ubuntu?  I would like something a little more eye pleasing on the boot menu.

---

### Post by coffeecat on 2011-05-13
I presume you mean a grub splash image. Have a look here:

[https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming)

If you are running the latest release, Natty/11.04, it couldn't be easier. Simply copy your .png, .jpg or .tga image into /boot and it will be automatically added. I'm not sure whether "automatically added" includes running 'sudo update-grub' but that wouldn't do any harm.

---

### Post by TAspr on 2011-05-13
I am sorry, I should have said on boot with windows 7 and Ubuntu in the choices.  Is there anything like that, although this is kind of nice.  I wonder if I can make the fonts bigger?

---

### Post by coffeecat on 2011-05-13
> **TAspr said:**
> I am sorry, I should have said on boot with windows 7 and Ubuntu in the choices.

You mean the grub menu? That was what I was referring to.

> **TAspr said:**
> I wonder if I can make the fonts bigger?

Have a play with the resolution figures for GRUB_GFXMODE in /etc/default/grub. See:

[https://help.ubuntu.com/community/Grub2#Changing%20Resolutions%20w/%20Splash%20Images](https://help.ubuntu.com/community/Grub2#Changing%20Resolutions%20w/%20Splash%20Images)

With my 1920x1200 screen I tried changing GRUB_GFXMODE to something near the monitor native resolution and the fonts were tiny. I now use 1024x768 and it looks OK. From my /etc/default/grub:

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1024x768
```If you need help with editing /etc/default/grub (you need admin privileges) post back. Also, after you make any changes to that file you need to run 'sudo update-grub'. I believe there is a graphical utility which makes these changes without having to fiddle with configuration files, but I haven't used it myself. Perhaps someone else can give details.

---


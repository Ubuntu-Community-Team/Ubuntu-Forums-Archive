---
title: "VGA = 789 is Depreciated"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Tholley on 2009-12-10
When grub boots up, I get a little msg at the top for about 1 sec, that says VGA = 789 is Depreciated Use Set...... It goes away too quick to get the rest so far.

Display and all seems to be fine, just want the msg to go away.

It just started after installing 9.10.

I have an older computer, with a Radeon 9200 Pro video card.
A pretty new moniter, Samsung 19" LCD 

Thanks!

---

### Post by bodhi.zazen on 2009-12-10
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2")

go to this section : [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

and scroll down just a bit ...

---

### Post by Tholley on 2009-12-10
Not sure what I should be looking for.

---

### Post by HighCommander540 on 2009-12-10
> **Tholley said:**
> Not sure what I should be looking for.

Just edit your /boot/grub/menu.lst file. And get rid of the vga=789 line. Why it was added in the first place (Ubuntu usually never adds it) IDK.

---

### Post by CharlesA on 2009-12-10
I think he's refering to this:

> #GRUB_GFXMODE=640x480

    * You can remove the # symbol to make this line active. The entry sets the resolution of the graphical menu (the menu text size). It provides resolutions supported by the user's graphics card (e.g. 640x480, 800x600, 1280x1024, etc). The setting applies only to the boot menu display, not the resolution of the operating system that boots.
          o Tip: Setting the same resolution in GRUB 2 and the operating system will decrease boot times slightly. 
    * Although not required, the user can also specify the color bitdepth by appending it to the resolution setting. An example would be 1280x1024x24 or 640x480x32.
    *      The user can also add multiple resolutions. If GRUB 2 cannot use the first entry, it will try the next setting. Settings are separated by a comma. Example: 1280x1024x16,800x600x24,640x480.
    * If using a splash image, make sure the resolution setting and the splash image size are compatible.
    *      If using an entry that produces a "not found" message when running update-grub, try adding or changing the color bitdepth.
    *      Resolutions available to GRUB 2 can be displayed by typing vbeinfo in the GRUB 2 command line. The command line is accessed by typing "c" when the main GRUB 2 menu screen is displayed.
    *      If this line is commented (#) or the resolution is unavailable GRUB 2 uses the default setting determined by /etc/grub.d/00_header.
    *      For a guide to changing resolutions when using a splash image see the Splash Images & Theming section. 

Could be wrong tho, I don't know GRUB very well.

EDIT: HighCommander540 figured it out.

---

### Post by bodhi.zazen on 2009-12-10
No, grub 2 (default with Ubuntu 9.10) does not use /boot/grub/menu.lst

In fact there is no /boot/grub/menu.lst .

You set a mode with 

#GRUB_GFXMODE=640x480

so, 

```
GRUB_GFXMODE=1280x1024x24
```, use the resolution you desire.

---

### Post by Tholley on 2009-12-10
> **HighCommander540 said:**
> Just edit your /boot/grub/menu.lst file. And get rid of the vga=789 line. Why it was added in the first place (Ubuntu usually never adds it) IDK.

I had read about changing it, which didn't work, but deleting it all together?

U sure?????

---

### Post by Tholley on 2009-12-10
> **bodhi.zazen said:**
> No, grub 2 (default with Ubuntu 9.10) does not use /boot/grub/menu.lst

In fact there is no /boot/grub/menu.lst .

You set a mode with 

#GRUB_GFXMODE=640x480

so, 

```
GRUB_GFXMODE=1280x1024x24
```, use the resolution you desire.

So do I replace the the vga=789 line with above?

---

### Post by Tholley on 2009-12-10
> **bodhi.zazen said:**
> No, grub 2 (default with Ubuntu 9.10) does not use /boot/grub/menu.lst

In fact there is no /boot/grub/menu.lst .

You set a mode with 

#GRUB_GFXMODE=640x480

so, 

```
GRUB_GFXMODE=1280x1024x24
```, use the resolution you desire.

or use terminal with the above?

---

### Post by bodhi.zazen on 2009-12-10
What version of Ubuntu are you using  and what version of grub ?

If you are using version 1 (earlier then 9.10), and your system boots without any problem, ignore the warning. Heck even if you are using Ubuntu 9.10, if your system is booting the way you want ignore that warning.

Basically, in a nutshell, Ubuntu is moving to grub 2, and that "warning" is informing you that "vga=xxx" is depreciated. Grub 2 is configured different then grub 1 so yes, in the long run you will need to learn a new syntax.

In the short run, if it is not broken don't fix it.

---

### Post by HighCommander540 on 2009-12-10
> **Tholley said:**
> So do I replace the the vga=789 line with above?

Yes, just get rid of it. You don't need it anymore. Like bodhi said, there are new packages and GRUB itself that are just handling your video setting by themselves. You don't need to add it to the grub command line anymore (at least in Ubuntu don't know about other distros).

---

### Post by Tholley on 2009-12-10
> **bodhi.zazen said:**
> What version of Ubuntu are you using  and what version of grub ?

If you are using version 1 (earlier then 9.10), and your system boots without any problem, ignore the warning. Heck even if you are using Ubuntu 9.10, if your system is booting the way you want ignore that warning.

Basically, in a nutshell, Ubuntu is moving to grub 2, and that "warning" is informing you that "vga=xxx" is depreciated. Grub 2 is configured different then grub 1 so yes, in the long run you will need to learn a new syntax.

In the short run, if it is not broken don't fix it.

Ok.. no prob.
I've been ignoring it already.. just thought might be a quick and simple fix.

I thought I was using grub2, but not sure...

Not a big deal to ignore, don't see notice unless I'm sitting watching...

---

### Post by Tholley on 2009-12-10
> **HighCommander540 said:**
> Yes, just get rid of it. You don't need it anymore. Like bodhi said, there are new packages and GRUB itself that are just handling your video setting by themselves. You don't need to add it to the grub command line anymore (at least in Ubuntu don't know about other distros).

I deleted the VGA=789 line in Grub menu, rebooted, still there...

No biggy.

thanks anyway

---

### Post by HighCommander540 on 2009-12-11
> **Tholley said:**
> I deleted the VGA=789 line in Grub menu, rebooted, still there...

No biggy.

thanks anyway

Weird it is supposed to go away if you don't set it to check...

---


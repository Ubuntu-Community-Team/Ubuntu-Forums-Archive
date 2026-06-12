---
title: "Disable GRUB"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by tb75252 on 2011-09-03
I am using Ubuntu 11.04.
Every time that I boot up I now get a GRUB screen that asks me which version of Linux I want to boot up.  

This is due to the fact that I have a second Linux distribution installed.  But I boot up to the second distro using a floppy diskette, so I really do not need GRUB's screen.  I would like to be able to boot up directly to Ubuntu and bypass GRUB.

How do I do that?

---

### Post by garvinrick4 on 2011-09-03
use:
```
gksudo gedit /etc/default/grub
```to change the time you have to choose your install from 10 seconds to 0 and save.
and then 
```
sudo update-grub 
```to apply it.
Here is grub2 instruction section from Ubuntu below.
read the section first so you know how to change it back when you find out you would
rather choose from grub menu. You can reduce to 3 seconds or so.
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")
Read section on /etc/default/grub

---

### Post by tb75252 on 2011-09-03
I was thinking about this instead of disabling GRUB:

What if I install the boot manager (LILO) of the second Linux OS (Slackware 13.37) in the root partition of that distribution?

Would it be possible to tell GRUB to link to LILO whenever I select "Linux (on /dev/sda3)" fromn GRUB's menu?  (PS:  /dev/sda3 is where Slackware resides)

As I said in my original message, I boot up Slackware using a floppy.  If I can get GRUB to link to LILO and boot up Slackware that way it would be awesome.

---

### Post by garvinrick4 on 2011-09-03
> **tb75252 said:**
> I was thinking about this instead of disabling GRUB:

What if I install the boot manager (LILO) of the second Linux OS (Slackware 13.37) in the root partition of that distribution?

Would it be possible to tell GRUB to link to LILO whenever I select "Linux (on /dev/sda3)" fromn GRUB's menu?  (PS:  /dev/sda3 is where Slackware resides)

As I said in my original message, I boot up Slackware using a floppy.  If I can get GRUB to link to LILO and boot up Slackware that way it would be awesome.
# You are not really disabling grub2 just by passing menu entries which you can see by
hitting shift key if need to see it.
#I have only used lilo for the purposes of installing a bootloader in Windows for users
whom have lost their Windows disks. So am not qualified to answer but this will bump
up for other users who are to give you that answer. Enjoy you Ubuntu and have a nice day.

#What does Slackware use as bootloader, grub-legacy, have never used it or worked with it at all. I do know grub2 will pick up any Operating System I have ever installed with its "os-prober" package.

---

### Post by andrew.46 on 2011-09-05
> **garvinrick4 said:**
> What does Slackware use as bootloader, grub-legacy, have never used it or worked with it at all. 

Default is lilo but grub 'legacy' is available in /extra and grub 2 is available on [slackbuilds.org]("http://slackbuilds.org/repository/13.37/system/grub2/").

---


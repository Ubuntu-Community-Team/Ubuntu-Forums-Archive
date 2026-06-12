---
title: "Ubuntu loading screen hangs"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-01-25
At the ubuntu loading page, the loading bar (in occasions) stops and the laptop just hangs there with no apparent cpu usage or anything. 

I noticed that it happens at the beginning of the loading bar and seems to be related with my touchpad turning on/being recognized (bar keeps going) or not (bar stops).

Did anyone had a similar problem and is there anything to fix this? Thanks!

---

### Post by Hospadar on 2009-01-25
You might try turning off or switching away from the pretty boot splash and see if there are any interesting or error-looking boot messages from linux.  At the start of the bootup (once you see the ubuntu logo) you can hit ctrl-alt-F1 to see the bootup stuff.  You might at least be able to see what it is trying to do/initialize.  This will probably help you to zero in on the problem.

I have an old tablet machine that had trouble with the boot splash causing the machine not to boot at all.  To disable it, you can edit your /boot/grub/menu.list and remove "splash" (i believe) from the boot line at the boot entry.

You can also temporarily disable it by pressing "e" at the grub menu to edit the entries, then removing splash from the kernel line of your chosen boot option.

If you monkey around with /boot/grub/menu.lst, be sure to make a backup copy, this is a very important file (your machine won't boot without it, or if it is messed up) so ```
sudo cp /boot/grub/menu.lst /boot/menu.lst.backup
```
would make a backup copy of that for you.
Also if you are less than confident about your grub boot menu editing skillz maybe keep a live cd on hand so you can actually make use of your backup when your machine won't boot.

---

### Post by sylvainrb on 2009-01-25
Ok I'll look into it. Thanks!

---


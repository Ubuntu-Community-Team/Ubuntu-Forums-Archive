---
title: "no way to reboot"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by hekastos on 2010-09-30
Hi & Nice to be read,

Prelude:
I'm not completely new to ubuntu, but had always to give up for some piece of &%$( not working with it. But now I'm trying again and I'm ready to do whatever it takes, if you tell me I have to recompile my kernel with strange compiler flags, while standing on 1 leg and praying the ascii table, I will do it...

Actually I have only a simple wish, I want to reboot.

Hardware:
Asus K50in laptop with ubuntu 10.10 
(don't suggest 10.04 because that doesn't even boot on it... but 10.10 rocks the house, in everything so far except rebooting)

The comp has no prob with a shutdown, but with a reboot it ends saying:
restarting system
-frozen-

If it is even possible to get suspend/hybernate running that would be awesome, but I need at least a reboot, which when automated does what its for aka reboots...

Thx for your patience and any hints you might have...

---

### Post by Bucky Ball on 2010-09-30
If you logout (shortcut ctrl+alt+Backspace) and THEN restart from the login window (an option there somewhere, generally bottom left of screen) rather than logging back in again, do you get the same error?

---

### Post by emoguitarist06 on 2010-09-30
What does the terminal say?

```
sudo shutdown -r now
```

---

### Post by hekastos on 2010-09-30
@Bucky Ball
yes it freezes saying "restarting system", but "restarting system" is now not written white like before, but brown ??!???

@emoguitarist06
freezes exactly at "restarting system" this time saying it in white 



Perhaps I should mention that nothing works anymore just > 5 sec pressing the power switch helps, it is really completely frozen saying "restarting system", which feels a bit like mockery
:wink:

---

### Post by wilee-nilee on 2010-09-30
hold down in this order crtl-alt-prtsc/sysrg then slowly type reisub.  b=reboot if you use a o, at the end it cyles off
[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)

Oh and do this while smiling.;)

---

### Post by hekastos on 2010-09-30
@wilee-nilee
erm how shall I say now the complete desktop is frozen without any reboot, at least I know now how to crash the whole thing ;)

---

### Post by hekastos on 2010-10-01
I found this:
[http://blogs.koolwal.net/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/](http://blogs.koolwal.net/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/)

now my question is, how do I in order to fix the issue, pass the following parameter to the kernel, in the form of **“reboot=<parameter>”**, at the time of boot ?

---

### Post by Bucky Ball on 2010-10-01
10.10 is VERY fresh and these probs are going to occur. I think there is a forum specifically for 10.10 and that would be better rather than absolute beginners. Suggest a mod move this there if it exists.

Now might be a good time to shutdown, boot into the BIOS and boot from the install CD, open System->Partition editor and have a good look around. I would suggest deleting the lot, checking your install disk for errors, and re-installing. It is a fresh install? Easy.

These bugs will pop up on new releases! They are generally resolved but it takes time, collaboration, and people like you responding and filing bug reports on sites like Launchpad. You might find if you can update your box it might fix your problem and a couple of others you didn't know about yet! Enjoy the learning curve. Once this is sorted sounds like you are going to enjoy it. But as I say, be prepared for a few more ups and downs with a fresh release (I think you are actually running a pre-release which means this should definitely be moved to the appropriate forum, mods). ;)

I know you might think this is backwards, but if your brain begins to hurt, you could try 8.04 LTS. The last long term support release and still supported, two and a half years old and basically rock solid (for many). You might want to give that a go, at least until 10.10 is officially released. You will learn plenty sticking with 10.10 though. Good luck whatever you do.

---

### Post by hekastos on 2010-10-13
I found the solution finally, so for everyone with a Asus K50in which doesn't reboot ubuntu 10.10 this is what worked for me:

1.) Check actual kernel parameter: cat /proc/cmdline
2.) change in etc/default/grub the line 
GRUB_CMDLINE_LINUX="" 
into
GRUB_CMDLINE_LINUX="reboot=pci"
3.) run sudo update-grub

extremly easy if you know it, but majorly ****** up, if you have no clue and why editing etc/default/grub is called so much easier then editing menu.lst is still a unknown to me...

Anyway thx for any help & cya in the bitstream :popcorn:

---


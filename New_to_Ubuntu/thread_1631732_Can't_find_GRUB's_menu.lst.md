---
title: "Can't find GRUB's menu.lst"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by darnir on 2010-11-27
I have installed Ubuntu 10.10 in Dual Boot with my Windows 7.
Yesterday, after updating the OS, I found 2 entries of Ubuntu and Ubuntu(Recovery Mode) in my Grub Menu. I want to eliminate the extra entries and also bring Windows 7 higher up in the order. 
A simple google search shoed that I must edit my menu.lst file in /boot/grub/ directory. But in that directory, I can't find the menu.lst file!! 

Someone please help me out as to where I can find this file or else how to edit the GRUB menu otherwise..

---

### Post by lisati on 2010-11-27
The version of GRUB that comes with 10.10 doesn't use menu.lst any more. Have a look here for "grub2" information: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Elfy on 2010-11-27
You don't have menu.lst - grub changed to grub2.

I'd not be inclined to remove the Recovery option - if you get a problem with your system it could be invaluable.

You can set a default menu item in grub - check [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743) there is a section for setting the default

---

### Post by sikander3786 on 2010-11-27
Or you can also use a GUI tool, statup manager to make Windows your default OS.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

And 2 entries for Ubuntu mean 2 different kernels, both with a recovery option as well. Keeping at least one older kernel is advised so if the newer one is unable to boot somehow, you can still boot the older one and diagnose/solve the problem.

---

### Post by Elfy on 2010-11-27
> Yesterday, after updating the OS, I found 2 entries of Ubuntu and Ubuntu(Recovery Mode) in my Grub Menu.

> And 2 entries for Ubuntu mean 2 different kernels, both with a recovery option as well.

Not in this case - read the whole post.

---

### Post by wilee-nilee on 2010-11-27
So really there is a mod with some great tutorials on grub2 here is a link to the most relevant probably, but check out their signature for the rest.
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by I'mGeorge on 2010-11-27
this it's what you might need

```

grub-mkconfig > /boot/grub/menu.lst (will generate a config file with the old menu.lst name)
grub-mkimage -c /boot/grub/menu.lst (will embed menu.lst to be the default config file instead of grub.cfg)

```

Though you could resume in editing grub.cfg for simplicity's sake

---

### Post by drs305 on 2010-11-27
@ I'mGeorge,

Thanks for trying to help but the user is most likely using Grub2 so adding a menu.lst is most likely going to confuse the issue. 

The 'grub-mkconfig' command can make a menu named something different than the default /boot/grub/grub.cfg but instead of a redirection ">" you would use the "-o" option and then the desired filename.

Also, editing grub.cfg is only a temporary fix since whenever update-grub is run the grub.cfg file will be regenerated and any manual edits will be lost.

@ damir,

Welcome to the Ubuntu forums. There are several ways to accomplish what you want. The "G2-Tweaks" link in my signature line discusses various ways of building the Grub 2 menu, but it is pretty 'geeky' stuff. 

If you can't understand it tell us specifically what you want and we can help you construct the menu. We would need you to post your /boot/grub/grub.cfg file, or even better, run the boot info script from the following link and then post the contents of the RESULTS.txt:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by I'mGeorge on 2010-11-27
> **drs305 said:**
> 
Also, editing grub.cfg is only a temporary fix since whenever update-grub is run the grub.cfg file will be regenerated and any manual edits will be lost.


true the proper way to do it would be to use the configuration files from /etc/grub.d , so if you wanna make any changes and play safely with grub I guess editing the /etc/grub.d/40_custom would be the right thing to do.

---

### Post by drs305 on 2010-11-27
> **I'mGeorge said:**
> true the proper way to do it would be to use the configuration files from /etc/grub.d , so if you wanna make any changes and play safely with grub I guess editing the /etc/grub.d/40_custom would be the right thing to do.

The good and bad thing about Grub 2 is it's complexity. There are several ways of achieving the same result: changing the built-in settings in /etc/default/grub, modifying the /etc/grub.d/scripts, or making a new /etc/grub.d/40_custom entry. 

Often the 40_custom method is the most easy to understand and in many ways would be most familiar to someone used to Grub legacy.

---

### Post by darnir on 2010-11-27
Thanks a lot everyone for helping me out on this...
I had had the idea that my GRUB might have been v2 when I did not find the Menu.lst. But, during boot I paid attention to what was written and it said GRUB v1.85, which is why I did not go ahead and look for tutorials about GRUB2.
Secondly, The double entry of Ubuntu that I can see, is exactly the same as the first one, down to the minor revision number of the Kernel, which is why I want to remove it. I have no intentions of removing the recovery mode entries, I just want to re-arrange the entries though.
And for re-arranging or deleting GRUB entries, the Start-Up Manager seemed like no help to me.
Ill just re-boot my system, and upload a snapshot of my GRUB Boot screen to make matters clear.

---

### Post by wilee-nilee on 2010-11-27
> **darnir said:**
> Thanks a lot everyone for helping me out on this...
I had had the idea that my GRUB might have been v2 when I did not find the Menu.lst. But, during boot I paid attention to what was written and it said GRUB v1.85, which is why I did not go ahead and look for tutorials about GRUB2.
Secondly, The double entry of Ubuntu that I can see, is exactly the same as the first one, down to the minor revision number of the Kernel, which is why I want to remove it. I have no intentions of removing the recovery mode entries, I just want to re-arrange the entries though.
And for re-arranging or deleting GRUB entries, the Start-Up Manager seemed like no help to me.
Ill just re-boot my system, and upload a snapshot of my GRUB Boot screen to make matters clear.

Have you looked at the link I posted.
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by drs305 on 2010-11-28
> **darnir said:**
> Ill just re-boot my system, and upload a snapshot of my GRUB Boot screen to make matters clear.

Grub2 started with version 1.96 (even though it is Grub2) . Grub legacy never got past 0.97  You would have to ask the developers why they do it this way.  ;-)

Better than the snapshot would be the contents of RESULTS.txt, a file generated from the boot info script found at this link:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

From it, we will be able to tell not only what you see on the menu but why. 

Also just briefly restate what you want to add or subtract from what you see on the menu and we can give you specific instructions.

---


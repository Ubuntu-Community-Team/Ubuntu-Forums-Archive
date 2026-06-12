---
title: "I jacked something up . . . GRUB 2"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by rm06 on 2009-11-24
I modified the /etc/default/grub file to use a higher screen resolution. While this worked, I can no longer launch Ubuntu directly from the default  selection, I have to use the recovery console, log in via the command line and use 'startx' to get to the GUI.

When selecting the default (first) selection, the screen goes black and will not proceed from there. I also uninstalled the previous Linux version (2.6.31.14) from Synaptic so it wouldn't show in the GRUB menu.

Please help me fix this, I'm unsure where to begin.

---

### Post by drs305 on 2009-11-24
When you say you modified the screen resolution, are you talking about changing the GFXMODE or adding something to the GRUB_CMDLINE_LINUX_DEFAULT="" line.  

The former is for the grub 2 splash image only and shouldn't affect the resolution once the system kernel takes over.

If you modified the latter by adding a line such as "vga=xxx" that is now deprecated and may be what is causing the problem. For starters I would remove any "vga=" additions.

I haven't used it but you might search for "gfxpayload=", which is a line you can now load into the grub.cfg file. On the other hand, if you are trying "gfxpayload" and it doesn't work, reverting to "vga=", even though deprecated, may produce usable results.

---

### Post by rm06 on 2009-11-24
I modified and uncommented the GFXMODE line to read 1680x1050.

---

### Post by drs305 on 2009-11-24
> **rm06 said:**
> I modified and uncommented the GFXMODE line to read 1680x1050.

GFXMODE shouldn't cause a problem with the system resolution but there may be a problem with the transition between the two. Is the Grub2 resolution the same as the one you want/have on the system. I suppose that is what I would try first.

The other thing I would do is reinstall the older kernel. If the new kernel is -15 in Karmic, some people are having problems with it. You can reinstall a kernel in Synaptic by typing 2.6.31- in the upper right search box if you are using Karmic.

You can also check System, Admin, Hardware Drivers to see if your driver is installed, if you needed one.

---

### Post by wrgb2 on 2009-11-24
Try booting into recovery mode and choosing Update Grub (or something simailar) from the menu.

---

### Post by rm06 on 2009-11-24
It was the vga= line. 

I got it working now, appreciate the help!

---

### Post by rm06 on 2009-11-24
I guess I spoke too soon.

Now when I make my GRUB selection I get the following:

vga= is deprecated. Use set gfxpayload=text before linux command instead.
error: you need to load the kernel first

I'm not sure what may have happened now as it worked on the last reboot. I'm at a loss.

---

### Post by drs305 on 2009-11-24
> **rm06 said:**
> I guess I spoke too soon.

Now when I make my GRUB selection I get the following:

vga= is deprecated. Use set gfxpayload=text before linux command instead.
error: load kernel before proceeding

I'm not sure what may have happened now as it worked on the last reboot. I'm at a loss.

I don't know why it is no longer working, but what it is telling you to do is to remove the "vga=XXX" from the linux line and add a separate line before that with "gfxpayload=XXXxXXX". 

I was experimenting with just such a line even as I read this post.

---

### Post by rm06 on 2009-11-24
How do I modify files from live disk? I am unable to even boot from the recovery console.

---

### Post by garvinrick4 on 2009-11-24
This thread will tell you how to do 9.10 or below.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by drs305 on 2009-11-24
> **rm06 said:**
> How do I modify files from live disk? I am unable to even boot from the recovery console.

Can you get to the grub 2 command line? If so, you can modify the lines in an existing menu or do a completely independent boot by entering the proper commands. 

Have you seen the community doc on booting from the Grub 2 command line or rescue mode:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

If you can edit an existing menuentry, remove the "vga=XXX" from the linux line. But if you get the "load kernel" message again, move on to the next section on booting from the command line.

Type "c" to drop to the grub prompt if you aren't already there, then use the "ls" command to find your boot files. It's explained in the link.

Just to be sure - there have been a lot of wubi problems today. These instructions are for a normal partition installation of Ubuntu.

---

### Post by rm06 on 2009-11-24
I was actually able to remove the 'vga=' from GRUB using the "e" command instead of the "c" command which enabled me to boot up. I then removed it from the /etc/default/grub file and ran update-grub which seems to have fixed the problem.

I sincerely appreciate everyone's help in getting me out of this jam!

---

### Post by patek on 2010-01-31
Considering this thread is now solved, I've decided to remove my post and post a new thread at [http://ubuntuforums.org/showthread.php?p=8752869](http://ubuntuforums.org/showthread.php?p=8752869)

---


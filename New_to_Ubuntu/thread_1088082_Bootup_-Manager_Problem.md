---
title: "Bootup -Manager Problem"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by MiltR on 2009-03-05
I'm new to linux. I just put together an old Dell XPS T500 out of scrap parts from three computers. It has a Pentium III, 500 MHz. processor, 384 MB RAM and two 10 Gig. drives. I installed Windows ME on the master drive and Ubuntu 8.04, from a "live" CD I made, on the slave. I want to compare the two systems over time and see if I like Linux.

	In some misterious way, "Grub"has become my bootup-manager. Before installing Ubuntu, the bootup-manager showed several choices. Among the choices were Windows, Windows with prompts and Safe Mode. But now, Grub shows me five choices. Grub Kernel 2.6.24.23 and recovery mode, Grub Kernel 2.6.24.16 and recovery mode and Windows 95/98/ME. I can no longer access Windows ME safe mode, ME with prompts, etc.

	In looking at Grub during bootup, I see that it can be edited. It has Root, Kernel, Initrd and Quiet for each of the five choices. But I don't know what I'm doing yet. So I'm hesitant to mess with it.

	I want to have Windows ME as the first choice. It's now the fifth. And I want to have access to Windows ME, Windows ME with prompts and Windows ME Safe Mode, as well as Ubuntu.

	So...must I edit Grub? Is there a better bootup application, freeware of course? What should I do?

Thanks,
Milt

---

### Post by myddewji13 on 2009-03-05
no idea if this will helpl...but try startup manager for add/remove...

---

### Post by MiltR on 2009-03-05
Thanks for the comment. I looked at Starup Manager, and I may be wrong,but can't see how that would accomplish anything.

Milt

---

### Post by cariboo on 2009-03-05
Select Windows Me from the menu, then press F8 to see the windows menu. If you are seeing that menu from a normal Windows startup, you have a problem with your installation.

Jim

---

### Post by MiltR on 2009-03-05
Jim,

    Thanks for your interest in my problem.

    The issue is that wheather I boot the computer from "Off" or reboot it from Windows ME or Ubuntu, pressing F8 only causes the machine to boot to the selected operating system. It does not go to the "old" boot menu screen. I can only get to "Grub".

     I recognize that I have a problem. But I'm not sure where it is or how to correct it. My guess is that Grub has written instructions to the boot sector of one of the hard drives. I don't know how to correct that. I don't if I can remove Grub and get back to the old bootup-Manager either. I am hoping that someone here has experience with this issue.

Thanks,
Milt

---

### Post by brdmb on 2009-03-05
Hi Milt,

Try selecting Windows ME by pressing 'enter' in the grub menu.

Right after you select it, hold down F8.  I think this will get you into the Windows boot screen, where you'll be able to select SafeMode, etc.]

The startupmanager will let you select Windows ME as the default operating system to boot when you start up your computer and do nothing.

My guess as to what exactly happened: when you did the updates, you updated your kernel which caused Ubuntu to change your grub boot options to allow you to boot into the older kernel, if the updated kernel didn't work right.  This is a safety feature, but in your case it looks like it removed some options that you liked having!

David

---

### Post by MiltR on 2009-03-06
brdmp,

     Thanks for your reply. Both you and cariboo907 were correct. I can get to the Windows ME boot choices and access Safe Mode by using the F8 key. The trick is, it must be pressed _immeniately_ after I select the Windows ME startup choice. I had been hesitating too long when I tried it before.

     As to changing Windows ME to my default, I will explore it and try to figure it out.

     Again, thanks to both of you.

Milt

---


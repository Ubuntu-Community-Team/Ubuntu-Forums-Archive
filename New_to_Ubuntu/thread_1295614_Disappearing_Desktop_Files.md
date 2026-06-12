---
title: "Disappearing Desktop Files"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by sharondenscabbia on 2009-10-19
After some confusion, I've now noticed that what I'm encountering isn't a bug, but most likely a documented deliberate feature, but I still don't really know what's going on in the background. That's what I'm here to find out.

On more than a few occasions, I've booted up Ubuntu 9.4 to discover that a few files I've recently downloaded are missing from my desktop. They're not in my "desktop" folder either. When I then open up Firefox, it opens up webpages which aren't my most recent, but which I've not looked at for a few days. I see that the icons on the top bar are not quite the same as how I left them (I move them around often) and the programs under my "Applications" menu are missing the most recent.  

By now I've realised that it seems that Ubuntu is "reverting" to an earlier state, and I'm not sure why, or what the point of it is. I can't work out when it reverts as it seems to be random on bootup (although I have just loaded it up into this 'older' mode after a forced hard reboot due to it being unresponsive) and unless I look at things I've recently changed I can't tell that it has reverted.

So, can anybody tell me, whats going on in the background here, and how can I get to my most recent downloaded files on my desktop without rebooting it?

---

### Post by ZankerH on 2009-10-19
Did you (or someone else with physical access to your PC) perhaps set Firefox to save downloaded files somewhere other than the desktop and regularly delete browsing history?

---

### Post by martrn on 2009-10-19
Have you tried looking at the System Monitor (System>Administration>System Monitor) which enables you to graphically view the available memory usage and swap space and identify if it is actively being used properly.

You can type :  [FONT="Fixedsys"]cat /proc/meminfo[/FONT]  to list your memory useage of your computer or   [FONT="Fixedsys"]top[/FONT]  /  [FONT="Fixedsys"]ps aux[/FONT]   commands  identify which applications are consuming most memory.

Like you say there is defiently something going on in the background here but without knowing what you have installed on your computer it would be difficult to know what is going on in the background.

To find out disk usage type   [FONT="Fixedsys"]df -h[/FONT]   and try you best to find out which application is badly behaved or is not working as it should.

Make sure you have enough swap file space on your computer and make sure you have spare drive space and a certain percentage free on your hard drives and the Gnu/Linux Ubuntu expects there to always be hard drive space available or else it will not work.

Have you any other clue as to what may be the problem, usually a good guess as to what may be happening turns out to be a good clue for a start.

---

### Post by Hospadar on 2009-10-19
Try saving those files elsewhere and see if they keep disappearing.  If they do, it might be a problem with your filesystem, and it might be time for a re-format or new hard disk.

Have you noticed any other hard drive problems?

---

### Post by sharondenscabbia on 2009-10-19
I'm sorry, I believe I didn't make my initial post clear. This doesn't seem to be a problem with my disk drive, file system or memory. 

What it seems to me, is that there are 2 (nearly) identical Ubuntu operating systems on my computer. Each one has different settings for the taskbar, menu and Firefox has different settings. Each would appear to have a different "desktop" folder, even though there is only one user which seems to be shared between them. Whats then even more confusing is that one of these appears to simply be an older version of the other one, having older settings than the one I use most. If I was using Windows XP, I would assume that I'd "system restored" to a previous point, as besides OS/firefox specific settings, everything else is the same between the two incarnations. Because it seems like it could be a protective mechanism of sorts, I assumed it was a feature.

When I boot up my computer, I can't choose which one I go into. Grub has 4 listings for Ubuntu, the current version at the top, it's repair boot, and one before an update with it's corresponding repair. All 4 seem to randomly boot either of the two incarnations of Ubuntu, with the newer one coming up a lot more.

I'll take it from the confusion that this isn't meant to happen. Has anybody experienced something similar?

---

### Post by martrn on 2009-10-19
I have never experienced anything similar to what you mention, and have not heard of such as to what you mention. 

Ubuntu has a new kernel released every so often and each kernel contains its own virtual file system and a set of a few files which start loading the kernel into memory.  When grub selects a kernel to boot, it will look at the virtual file system and mount it.  Your designated hard drive will then load its-self as root with the rest of the virtual file system in /dev and /proc.  Any other hard disks or partitions will be mounted in /media on your file system.

When a new kernel is released it will add this kernel to a new compressed archive in your /boot directory and add or register itself with grub so it can be booted through grub when the computer is first switched on.

The number of users connected to an ubuntu computer and that can log on and start a desktop session will each have a directory in the /home directory of the ubuntu hard disk.  Eg, /fred  /whilma /barney and /betty sub-directories in the /home directories dictate that there are four users that can log on to an ubuntu computer.  The two, three, or four kernels that grub displays when first booting up the computer do not dictate that there are two, three, or four incarnations of ubuntu only that their has been a new kernel released since the previous one.  This is to provide newer features in newer kernels and allow you to roll back one kernel or two only if one does not work or end up toast.   It is not uncommon for experienced linux users to have 15 kernels on their computer.  (STILL ONLY ONE INCARNATION OF ONE GNU/LINUX/UBUNTU SYSTEM).  

There is not any roll back feature to the standard distribution of ubuntu, although ubuntu does perform an fschk (file system check) of the file system on boot depending on weather or not the computer was closed down properly.

I do not know how your hard drive is partitioned and it would help to know if you are having file system problems.  If you say you are missing files then it is possible that a particular application that you was trying to install failed and you will need to re-install that application.  If you are missing files it is possible that you had a crash or lockup, ensure you only use the most recent kernel or a known one that works, and put the missing files down to bad luck.

If you are still having more problems post back with ubuntu/linux specific problems and or any error messages you get from your /var/log directory.   It is difficult to work out sometimes from you terminology what you want, perhaps because you expect ubuntu to behave like windows, although I am not sure.  Ubuntu != Windows.

Anything else post back.

---

### Post by sharondenscabbia on 2009-10-23
Whilst I am an experienced computer scientist (mainly with Windows and Macs, Linux is simply an expansion of my postgrad studies), I understand that Linux and Ubuntu aren't either OS, and I don't expect Ubuntu to act as either. I am simply perplexed by how my experiences cannot be found in any written documentation. I have used Ubuntu for well over a year now, and the way it works is not alien to me

The 'incarnations' I speak of are not related to the number of different versions of kernels, I understand that there are various different versions of the Linux kernel on my computer, and that isn't the problem at all, I simply elaborated on what I said in case I'd missed anything relevant with my currently limited knowledge. Its not a problem with my file system or hard drive, I know exactly the symptoms of those problems and the specific symptoms I am having are not indicative of the symptoms I am observing. If it was a HD problem, Ubuntu wouldn't appear to switch between two 'versions' or 'incarnations' of itself, but simply lose files (largely) irretrievably. The problem Ubuntu upon booting seems to randomly choose between two incarnations of itself, each of which has a different desktop and settings. 

If I can give you the output for any settings files in order to explain my position, please tell me. Perhaps I was wrong to place this within the 'absolute beginners' area, I simply assumed I was using the OS wrong. If any admin could please move this for me to 'general questions', it may be more appropriate.

---

### Post by martrn on 2009-10-24
> **sharondenscabbia said:**
> Whilst I am an experienced computer scientist (mainly with Windows and Macs, Linux is simply an expansion of my postgrad studies), I understand that Linux and Ubuntu aren't either OS, and I don't expect Ubuntu to act as either. I am simply perplexed by how my experiences cannot be found in any written documentation. I have used Ubuntu for well over a year now, and the way it works is not alien to me.

Whilst I am not a qualified computer scientist, I could claim I am a little upset with the way technicitions are treated by people who profess to be 'qualified' experienced computer scientists. OK carrying (&joking aside), your experinces that you talk of are generally found in forums that contain topics such as kernel development, programming gnu utils and open source software development, usually in mailing lists and other types of communication.

> The 'incarnations' I speak of are not related to the number of different versions of kernels, I understand that there are various different versions of the Linux kernel on my computer, and that isn't the problem at all, I simply elaborated on what I said in case I'd missed anything relevant with my currently limited knowledge. Its not a problem with my file system or hard drive, I know exactly the symptoms of those problems and the specific symptoms I am having are not indicative of the symptoms I am observing. If it was a HD problem, Ubuntu wouldn't appear to switch between two 'versions' or 'incarnations' of itself, but simply lose files (largely) irretrievably. The problem Ubuntu upon booting seems to randomly choose between two incarnations of itself, each of which has a different desktop and settings.

I would say from what you describe it is not a problem with your hard discs or a releated hardware problems.  I would say that it is a problem with one or both or your kernels.  When ubuntu boots up it first boots a boot loader such as grub.  Grub is only a boot loader with very little computer code.  The second part of grub is contained on one part of your hard drive, which has a boot directory called /boot .  Withing that directory (ie within your /boot directory), you will have several kernels and some sort of configuration files that the kernel needs to boot.

When your kenel boots, (/boot/kernelnumber0000???.??00.?? which will be invoked by grub, your kernel will mount a virtual file system and arrange your root directory of your file system according to how the kernel is compiled and according to what it finds on your root filing system.  Everything in gnu/linux is a file on a file system so everything in /dev will be a file on the linux virtual filing system that the kernel has decided to assign to control your hardware.

> If I can give you the output for any settings files in order to explain my position, please tell me. Perhaps I was wrong to place this within the 'absolute beginners' area, I simply assumed I was using the OS wrong. If any admin could please move this for me to 'general questions', it may be more appropriate.

Just re-install ubuntu again because you might (more probable than not), have a faulty kernel in your /boot directory, or faulty configuration files in /boot that ubuntu needs to boot up.  For clarification I would sudgest based on what you speak your problems are related to a bad kernel or more than one bad or faulty kernels, due to either a corrupted kernel or a faulty installation routine when you installed ubuntu.

---

### Post by QLee on 2009-10-24
> **sharondenscabbia said:**
> After some confusion, I've now noticed that what I'm encountering isn't a bug, but most likely a documented deliberate feature, but I still don't really know what's going on in the background. That's what I'm here to find out.

On more than a few occasions, I've booted up Ubuntu 9.4 to discover that a few files I've recently downloaded are missing from my desktop. They're not in my "desktop" folder either. When I then open up Firefox, it opens up webpages which aren't my most recent, but which I've not looked at for a few days. I see that the icons on the top bar are not quite the same as how I left them (I move them around often) and the programs under my "Applications" menu are missing the most recent.  

By now I've realised that it seems that Ubuntu is "reverting" to an earlier state, and I'm not sure why, or what the point of it is. I can't work out when it reverts as it seems to be random on bootup (although I have just loaded it up into this 'older' mode after a forced hard reboot due to it being unresponsive) and unless I look at things I've recently changed I can't tell that it has reverted.

So, can anybody tell me, whats going on in the background here, and how can I get to my most recent downloaded files on my desktop without rebooting it?

Everything that you described seems to be related to userspace rather than any system stuff. Have you tried adding another user to the system and seeing if that new user's home behaves the same or similar? any differences might give us something to speculate about?

---

### Post by sharondenscabbia on 2009-11-25
I apologise for what I said in my previous post, I didn't intend to sound superior, I just wished to elaborate that it didn't seem to be a problem that I would know about.      	 	 		 	      :p

I have been away from my computer for a while due to studies, and have just picked it up again. I've not tried creating another user, I will try to do so and see what I experience.

I would very much dislike reinstalling Ubuntu. When I last installed it (which I have several times now) I had a great amount of trouble getting my Atheros wireless to work. Frankly, I'm not sure how i did! I'd therefore like to mess with it as little as possible as my ability to replicate what I did will be somewhat limited. However, if I can't get to the bottom of this within the next month or so, I will consider it.

Thanks all for the help.

---


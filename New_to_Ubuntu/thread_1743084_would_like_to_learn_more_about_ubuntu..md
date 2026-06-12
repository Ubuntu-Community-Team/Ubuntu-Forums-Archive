---
title: "would like to learn more about ubuntu."
date: 2011-04-29
forum: New to Ubuntu
---

### Post by georgelappies on 2011-04-29
Hi all, I am really getting into this ubuntu thing lately and want to learn more about how it is put together. So here is a few noob questions. 

1. Is everything in the OS configured via text files. 
2. If number one is true, where does all these files live?
3. What happens chronologically during the boot process?
4. What is the glue that holds the OS together?

I am a windows system admin so I know a little bit about computers but I would really like to know more.

Thanks in advance for any replies. 

George

---

### Post by rosencrantz on 2011-04-29
Hi George,
trying to answer some of your questions:
1. In a nutshell, yes. GUI configuration frontends usually just make changes to those config files.
2. Config files are sorted by permission ranges. Settings pertaining to one individual user are stored in hidden files in the user's home directory (like ~/.gnome or ~/.kde). System-wide settings (you need sudo permissions to modify) should be in /etc subdirectories, I think.
3. There is extensive documentation at the Linux documentation project [http://tldp.org/guides.html](http://tldp.org/guides.html)) It's a bit dated, but the inner workings of linux system haven't changed a lot in principle.
You can also find out a bit from the system logs (issue the dmesg command in a terminal or look at the log files in /var/log.
4. Probably shoe strings and duct tape. The kernel is written in C, most major applications as well, but there are libraries and interfaces for most major programming and scripting languages, so  you'll also find lots of smaller community apps in python or java.

---

### Post by JKyleOKC on 2011-04-29
Your third question doesn't have a single simple answer. Up until 2008, Ubuntu used the "SysV" initialization technique, in which a single initialization process launched other processes sequentially as directed by rules contained in a group of directories, all located within the /etc main directory.

However with the 8.04 release in April of 2008, Ubuntu began switching over to a very different technique called "upstart" which launches the processes pretty much in parallel, with each of them having certain events that start them and others that cause them to stop. This makes the chronological sequence depend entirely on the speed with which certain critical processes do their thing. With slow disks, the sequence may be quite different from the same code running on a system with very fast disks.

If you're familiar with the event-driven paradigm on which Windows is built, where an internal message pump determines which process gets the next time slice depending on what events occur, then you'll have no trouble grasping the way upstart works. However your question seems to imply an assumption that the boot actions have a single sequence, which was more true of the old SysV approach than it is today!

The only way to get a definitive answer to this question is to install the "bootchart" package and let it create a graph of all the boot actions. The result will apply to only the one specific system on which it's run, but it's quite useful when attempting to optimize the actions...

As for "what holds it all together" I'd say faith and persistence on the part of the thousands of folk who maintain the many parts of the system. The layer of "code" that's closest to the user is almost all composed of scripts written in bash (which is the equivalent of command.com or cmd.exe but is much more powerful) that are the equivalent of Windows *.bat files. These are straight text, and are easy to read and modify as desired. The next layer down seems mostly to be written in either perl or python. When you get down to the actual kernel, it's mostly C (not even C++) but there's a bit of assembly language as well.

---

### Post by georgelappies on 2011-04-29
Thanks so much for the insightful answers. It is much appreciated. Yeah the whole idea behind open source seems faith inspired and stems most definitely from the light side ;) not like in the other proprietary world were you buy a semi useless gui and then have to spend thousands on licensing to enable 'modules' to be activated in certain apps...

---

### Post by matt_symes on 2011-04-29
Hi

JKyleOKC is bang on the money with what he is saying.

There are, however, some basic principles followed.

1. PC boots up with post test.
2. Kicks off grub stage 1 (in MBR) which starts grub stage 2 (usually). This is where you get to pick your kernel to boot into.
3. grub2 loads the kernel and initramfs. initramfs main jobs is to find the root filing system. The kernel the pivots its root to the new root filing system.
4. sbin/init (usually as others can be called) is started. This is the parent process that kicks everything off including upstart.
5. Loads of things happen in parallel as JKyleOKC highlighted.
6. You are then presented with cli logon or gdm is started to allow you to logon from a GUI. 
7. With gdm after entering a password it starts X and your window manager etc.

This is a _very_ general overview

Kind regards

---

### Post by JKyleOKC on 2011-04-29
Thanks for putting my post in perspective, Matt! I completely overlooked that it needed to start from the BIOS ROM code.

I've not dug into the internals of Windows since the days of 3.1, but at that point it did have stuff very much like grub's multiple stages. The code in the MBR pulled in one of the two system files at a predefined memory address (0x7C00 as I recall but it's been a lot of years since I traced through this stuff) and transferred control to it, then that file brought in the rest of the MS-DOS kernel, got it running, and brought in the Windows kernel by launching win.com.

---

### Post by gregorthebigmac on 2011-05-05
I'm an old power user of win 95/98, but never bothered to keep up after win xp/7 came out. Switched to ubuntu after 8.04 came out, and love it, but never actually learned a whole lot about how it works. TIL, thanks!

---


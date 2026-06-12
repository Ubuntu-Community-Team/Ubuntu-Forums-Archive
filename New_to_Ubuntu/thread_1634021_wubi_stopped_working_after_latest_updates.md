---
title: "wubi stopped working after latest updates"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by jfloydb on 2010-11-29
I have seen a couple of threads with a similar problem, but I think my problem is a little different:

After the latest updates for 10.04 LTS (just minutes ago), my WUBI install will no longer load. My Windows Bootloader is still working, so I do not think that is the problem. (Until now) when the Windows Bootloader comes up, I choose Ubuntu (rather than windows xp), it then takes me to the Grub loader, where I choose Ubuntu, and (in the past) Ubuntu would load. Now all I get is a black screen, and I have to shut off the machine and re-start it to get back to the windows bootloader where I can choose windows xp.

Now I am in Windows. I can look in the C:\ drive and find the ubuntu folder. Inside the ubuntu folder I find a disks folder. Inside the disks folder I find a boot folder. Inside the boot folder I find a grub folder. THE GRUB FOLDER IS EMPTY. C:\ubuntu\disks\boot\grub\EMPTY. I am assuming that the grub folder should have something in it. If it is the case that "grub" is missing, how can I replace it through the Windows desktop interface? If I cannot, and I must do a new wubi install, how can I preserve all my files and data from my previous wubi install? 

Thanks for your patience, and a million thanks to whoever can help!

---

### Post by MindController on 2010-11-29
to solve your problem,[here](http://www.justlinux.com/forum/showthread.php?t=144294) is the best solution for you.

---

### Post by bcbc on 2010-11-30
You can copy data off a wubi install by using this tool: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) (just point it at the file c:\ubuntu\disks\root.disk

You can get it to boot again, by loop mounting and editing the grub.cfg file by hand - it's not in the c:\ubuntu folder it's on the actual virtual disk (within the root.disk).

See this link for instructions: [https://answers.launchpad.net/wubi/+question/135755](https://answers.launchpad.net/wubi/+question/135755)

If you reinstall, avoid updating packages grub-pc and grub-common - they are buggy

---

### Post by beew on 2010-11-30
Do a dual boot or install in an external harddrive. Wubi is  a crippled, castrated version of Ubuntu running under the thumb of Windows. Why would anyone seriously want to try Linux/Ubuntu want it?

---


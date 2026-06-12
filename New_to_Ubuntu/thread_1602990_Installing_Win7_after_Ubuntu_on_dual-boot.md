---
title: "Installing Win7 after Ubuntu on dual-boot"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Th3Alchemist on 2010-10-22
Hi to all!

I have my laptop on dual-boot (Windows 7 & Ubuntu 10.10) and since I'm a newbie to ubuntu (and already loving it), I got the following question:

I need to format and reinstall windows 7, and since it's not recommended to install windows after linux, what procedure should I take? Won't my GRUB disappear?

I wish I didn't need it anymore but I'm still dependent to it (can't get NI Multisim on Linux working)

Thanks for any reply ;)

---

### Post by P4man on 2010-10-22
If you reinstall 7, it will indeed overwrite the grub bootloader and render ubuntu unbootable. But you can fix that with a liveCD (or USB stick). Detailed instructions can be found here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

But before proceeding, you are sure its not a wubi install?

edit: btw, you can try running that app with wine under linux:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14245](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14245)

Or run it in a virtual machine.

---

### Post by ivarn on 2010-10-22
If that sounds complicated, you should try out a windows app called Auto Super Grub. You can install it from download.com and it's easy to figure out and use as well.
Now you have access to ubuntu as well as windows.
If you don't like super grub, you can install grub 2 from ubuntu
```
*sudo apt*-*get install grub2*
```

---

### Post by Th3Alchemist on 2010-10-22
Thanks for that quick reply **P4man**, I'm sure I'm not using wubi...
I still prefer using Windows for this kind of aplication sice I'm not and expert on ubuntu and wine... Too important work to mess around but thanks anyway!

I also will have that in mind **ivarn**, thank you also!

Marked as SOLVED

---

### Post by P4man on 2010-10-22
> **Th3Alchemist said:**
> .
I still prefer using Windows for this kind of aplication sice I'm not and expert on ubuntu and wine... Too important work to mess around but thanks anyway!

Yeah I understand. Wine isnt ideal, but I think you should really give a virtual machine a try if you maintain a dual boot only for a single app. If you have enough RAM, you can create a virtual machine from your (soon to be) fresh windows 7 install with pretty much a single click using this great app:
[http://blog.paragon-software.com/?p=439](http://blog.paragon-software.com/?p=439)

That generates the virtual drive and VM settings from your installed windows, and you can load load that in virtualbox, and have the exact same environment you had,  and see how it works under ubuntu. 

Not that 7 is ideal as guest OS, but this way you dont have to install, patch, update, active,  windows and your app in the VM just to see if its workable solution for you.

Aside from not needing to dualboot, this approach lets you move or boot your install on any machine, you can create snapshots, etc, etc. Instead of having to reboot, you can open your windows environment in a just few second. Its really neat! And fast too.

---


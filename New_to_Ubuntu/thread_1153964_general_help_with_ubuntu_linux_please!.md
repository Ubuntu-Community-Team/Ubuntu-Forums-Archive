---
title: "general help with ubuntu linux please!"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by jackbarnard on 2009-05-09
Hi, i have a vista machine at the moment with 2 hard drives, the first hard drive contains my vista install and my second contains backups but there is plenty of space left on it for a linux install.  I am just a little confused as to how i go about installing linux really: do I simply select the free space on my second hard drive as the partition for linux at the install stage? will I still have the dual boot screen asking me which one I want to boot if windows and linux are seperate hard drives? how do i uninstall linux if I ever need to?  would it be better for me to install linux on the same drive as my windows install?

i know this is a lot of questions but any help would be greatly appreciated, thanks

---

### Post by NightwishFan on 2009-05-09
Welcome to Ubuntu forums, and feel free to ask questions. First off let me ask if you are using the graphical installer, aka 'Live CD'.

As for installing on multiple drives, I have never tried it, however I think it should work fine using the free space. Please wait for a more definitive answer before you try!

*    Perhaps you should try the Wubi installer. WUBI is a program to install Wubi 'inside' Windows without rearranging disks. It is available on the Ubuntu Live CD. Wubi has almost no performance loss, and is great because it is very easy to remove, simply go to add/remove inside Windows, and click uninstall. It also coexists well and uses the native Windows bootloader.

Ubuntu should dual boot well with Windows Vista, generally it does better than with Xp. Remember to use Vista's built in partitioner to modify disks, since Windows is picky.

Edit: More coming, stay tuned.

If you choose to do a standard full installation, there is a tad bit of risk involved when it comes to Windows, however if you have the partition space preformatted, it should easily detect Windows and set up a dual boot.

---

### Post by Triptol on 2009-05-09
Some thoughts:

[LIST]
[*]Multiple discs work perfectly (doing it for years now)
[*]Read a little bit about grub, there will come a time when you need it (but it shouldn't be first on your list). Grubs starts your OSes.
[*]You can install Ubuntu in Windows (I think it is called the Wubi install). Personally I wouldn't recommend it, since you seem to have enough place on your discs.
[*]Make sure Windows is installed on the first disc or first partition on that disc
[/LIST]

Your steps would be something like this:
[LIST]
[*]Use Windows to resize your disc (if needed). The new space can be left empty. If you don't have a resize program, the Ubuntu installer can do it for you, but I would prefer the Windows method if possible.
[*]Check your BIOS and make double sure Windows is booting from the first disc.
[*]Boot from the Ubuntu installation CD and install Ubuntu on the Empty space. It will create its own partitions there, which is fine.
[*]During the installation let grub install in the Master Boot Record (MBR).
[*]Reboot and enjoy.
[/LIST]

There is a dual boot help page: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by jackbarnard on 2009-05-09
thanks for the reply, but what do you mean by 'preformatted', are you saying its ok to install linux on a seperate disk as long as the disk has been formatted inside windows? because i formatted the disk when i bought it so windows could save files onto it.

---

### Post by NightwishFan on 2009-05-09
I mean if you use Windows to make the empty space on your second disk. Not just "free space" but empty unformatted space for the Ubuntu install to use. I recommend using over 15gb.

You can do this in Windows Vista by right clicking my computer and going to "manage". You should defragment the disk before you do so. Other wise follow the above posters easy to understand instructions.

Here is a reference:
[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

If you create free space where you want to install Ubuntu, the Ubuntu installer will handle the rest when set up to use free space.

I still recommend using WUBI.

---

### Post by sandyd on 2009-05-09
> **jackbarnard said:**
> thanks for the reply, but what do you mean by 'preformatted', are you saying its ok to install linux on a seperate disk as long as the disk has been formatted inside windows? because i formatted the disk when i bought it so windows could save files onto it.

he means that you can either

1. pop the cd in while running windows and install it like that (NOT recommended)
2. Resize the partition on your drive and leave free UNPARTITONED space for ubuntu
Then when you get to the partitioning stage of ubuntu installation,  select "use free space" (or something close to that)


EDIT: whoops. someone beat me to it...

---

### Post by jackbarnard on 2009-05-09
> **Triptol said:**
> Some thoughts:

[LIST]
[*]Multiple discs work perfectly (doing it for years now)
[*]Read a little bit about grub, there will come a time when you need it (but it shouldn't be first on your list). Grubs starts your OSes.
[*]You can install Ubuntu in Windows (I think it is called the Wubi install). Personally I wouldn't recommend it, since you seem to have enough place on your discs.
[*]Make sure Windows is installed on the first disc or first partition on that disc
[/LIST]

Your steps would be something like this:
[LIST]
[*]Use Windows to resize your disc (if needed). The new space can be left empty. If you don't have a resize program, the Ubuntu installer can do it for you, but I would prefer the Windows method if possible.
[*]Check your BIOS and make double sure Windows is booting from the first disc.
[*]Boot from the Ubuntu installation CD and install Ubuntu on the Empty space. It will create its own partitions there, which is fine.
[*]During the installation let grub install in the Master Boot Record (MBR).
[*]Reboot and enjoy.
[/LIST]

There is a dual boot help page: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

so let me get this straight:

[LIST]
[*]I resize the partition on my second (not vista) disk so there is some free space using the vista disk management tool
[*]I then boot up with the Ubuntu Live CD and install Linux in this free space
[*]I check that my windows disk is booted first in my BIOS
[*]Reboot my computer and GRUB should detect that i have two OSes on seperate disks and give me the choice of which one I want to boot
[/LIST]
Please let me know if I have this right!
Thanks

---

### Post by NightwishFan on 2009-05-09
That sounds correct. Is that what you want to do? If you do not use Ubuntu at least more often than Windows I say install using WUBI, it is much safer. If you use Ubuntu more, then do the full installation.

---

### Post by jackbarnard on 2009-05-09
ok thanks, so whats the difference between the Linux you get from WUBI and the Linux full installation?  If theyre the same why isnt everybody using WUBI?

---

### Post by bpalone on 2009-05-09
If you are just wanting to try Linux, then the WUBI install is the best option.  It is the least invasive.  If you decide you don't like it, you just use the add/remove programs from control panel (I believe, as I haven't used it.).  That way you haven't messed with the file systems on your hard drive and you have an easy way out of Linux if you decide it isn't for you.

If you are sure you are going to stick with using and learning Linux, then I would say go with the full install, keeping a dual boot system.  I have dual boot systems on all my machines, except the server.  I very seldom go into Windows any more, with the exception of the Virtual Machine for printing postage and the odd time or two I need IE6 for some backwards website.

Again, if you are just trying it out, use the WUBI.  You can always change to the full install if you decide you like it.

Another option, not mentioned, is using Virtual Machine to install on.  I think Microsoft still gives theirs away and there is VirtualBox.  I don't know how well VirtualBox performs under Windows, but if it is anything like it does under Linux, then I would go that way.  The virtual machine route will allow you to try many different flavors of Linux or older versions of Windows if you have the install media.  You just need the disk space to store the virtual hardrives.  Another point in favor of the virtual machine route, is that you can probably find virtual machines already set up with Linux of various flavors, to download.  And, if you keep good copy of your installation, you can always get back to there with a few clicks and little typing (a couple minutes compared to hour or two). In other words, you could completely hose the installation and turn around and have it back in just a couple of minutes (less anything you had done since the original setup).  VirtualBox offers to take a snapshot before you do anything, so it can be returned to the state it was when you started the mod or install.

This got a bit lengthy, but I hope it gives you an idea or two to ponder.  WUBI is a very good option and doesn't require a lot of technical understanding.  Virtual Machine is another good option, but requires a bit more technical expertise. Then, you can also go for the dual boot option, which is also good.

---

### Post by jackbarnard on 2009-05-09
thats brilliant thanks for that! i hadnt thought of the virtual machine method its definitely something to ponder.

---

### Post by NightwishFan on 2009-05-11
Good luck, and have fun.

The main user differences in WUBI is that disk performance is slightly reduced (slightly) and hibernation is not available. (As far as I know, I still use 8.04 WUBI on some Windows PCs).

---


---
title: "Compter loads straight into windows xp."
date: 2008-12-15
forum: New to Ubuntu
---

### Post by jdc.84 on 2008-12-15
Hello,

Could anybody offer me any advice?

I recently got fed up with virtual box being slow with big programs  so went back to xp for the first time since the Ubuntu install. Windows worked fine and still does. 

I have not done anything with regards to any of the bootup settings, but now when i try to load back into Ubuntu there is no OS option like before.

I found some advice saying i should start with the 'live disc'. As i am new to Ubuntu i had not yet got around to making one...

Is the live disc the installation disc i used originally and if so what option should i use ("try ubuntu" or "load from first drive"?)

If Not can i make a 'live disc' from xp??

Thanks for any help.

John

---

### Post by squeabs on 2008-12-15
Ubuntu Live CDs come in a .iso format. You can burn that directly to cd. The disc you have is probably the right one. If you pop the Live CD into your cd slot, you'll be presented with some options. You can "try ubuntu", "install ubuntu" or "start from first drive". The third option will probably bring you back to your windows install. If you want to install a fresh copy of ubuntu on a partition, choose "install" or "try".
When you choose "try" you are running the entire ubuntu operating system from the cd. No changes will be made to your computer. Once you actually start up the installer and partition a spot for it on your hard drive, it will be installed and you should have the option to start up in ubuntu or windows via a menu when you turn on your computer.

---

### Post by Michael.Godawski on 2008-12-15
> If Not can i make a 'live disc' from xp?
here you go:

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by nhasian on 2008-12-15
if i understand you correctly, you are dual booting between Windows and Ubuntu.  You've been using Ubuntu for some time just fine but after you booted into windows the Grub boot menu that allows you to choose your operating system disappeared correct?  Super Grub Disk can help you fix this issue.

[http://www.supergrubdisk.org/wiki/Boot_Problems#Linux_Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems#Linux_Boot_Problems)

you can download the Super Grub Disk from:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by sydbat on 2008-12-15
You need to reinstall grub.

This might help - [http://ubuntuforums.org/showthread.php?t=811240&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=811240&highlight=reinstall+grub)

Or this - [http://ubuntuforums.org/showthread.php?t=724817&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=724817&highlight=reinstall+grub)

Or this (the last post) - [http://ubuntuforums.org/showthread.php?t=1011619&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=1011619&highlight=reinstall+grub)

---

### Post by fiatguy85 on 2008-12-15
Unfortunately, when you reinstall windows, it takes control of the boot process from the boot manager Ubuntu uses called GRUB, by overwriting the Master Boot Record.  You can use the "Live CD" which is what you originally installed Ubuntu from, to reinstall the GRUB boot manager.  Unfortunately it looks fairly complex.  The how to is located at:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The other option, if you have everything backed up is to install windows first, which you have done now, then reinstall Ubuntu.

---


---
title: "importing files"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by TotemLakeRoger on 2010-09-09
I am a brand new Ubuntu user.  I am very frustrated, partly because everything in the program and on the web is jargon and meaningless to a computer literate English Speaking American.
 
I did down load Ubuntu to my Compaq Presario computer.
 
My computer is 2 1/2 years old and came loaded with Vista Home Premium.  I do not have office.  I did find and install the Open Office dot org programs and use the office programs.  I don't have any other office programs.  I have 1000's of document files nearly all of which are in Microsoft Office formats.  
 
I can start from a shut down computer and choose between Vista and Ubuntu.  When I choose Ubuntu, I can access Open Office programs.  However, none of my existing files are listed and I can not find anyway to locate them or open them.
 
While using Ubuntu, how do I find and open the 1000's of files I already have?
 
TotemLakeRoger

---

### Post by bodhi.zazen on 2010-09-09
Where are the files located ? On your windows partition I assume.

You need to mount your windows partition :

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by sgosnell on 2010-09-09
Use Nautilus, the file manager, to look for them.  It's the equivalent of Windows computer explorer, or "My Computer".  They are probably on the Windows drive, which probably isn't automatically mounted when you boot Ubuntu.  It might be listed under /media, or under /dev (devices).  Double-clicking on an unmounted drive should mount it.  If you want it mounted automatically at boot, you will likely need to edit /etc/fstab, as root.  Folders in the system hierarchy, as opposed to your home folder hierarchy, belong to root, and must be edited as root, using sudo.  There are a couple of ways to do that, as usual.  You can open a terminal (the equivalent of a Windows command window) and type ```
gksudo gedit /etc/fstab
```and open the default text editor with that file open for editing (gksudo is for opening a gui program as root), or you can use Nautilus to navigate to it, and right-click on the file and select Open as administrator.  Be careful, and make sure you know what you're doing if you do edit fstab.  Linux assumes you know what you're doing, and will let you hose your system.  Make a backup copy before you change anything, and keep an external boot disk available, either on CD or USB drive, so you can reverse changes.  If you do this, nothing is irreversible, and you can almost always recover.

---


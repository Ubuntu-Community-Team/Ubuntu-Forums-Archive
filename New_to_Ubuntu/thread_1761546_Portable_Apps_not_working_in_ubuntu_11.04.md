---
title: "Portable Apps not working in ubuntu 11.04?"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by djpemberton on 2011-05-18
I have several portable apps on a flash drive that I use between computers. They had worked in 10.04, but when I upgraded all my computers to 11.04 they lost the ability to run. When I click on it I am told that it cannot be displayed and that "There is no application installed for executable files" and to choose a program to run it. When I look at their permissions, the box to allow running as a program is unchecked. When I try to check it, the check mark appears and then immediately disappears. I also cannot change it in the terminal.

Is there something I am missing?

---

### Post by crispy_420 on 2011-05-18
My guess that something missing is wine.

[Portable Apps]("http://portableapps.com/") is a Windows tool so emulation is needed.

---

### Post by mcduck on 2011-05-18
+1 to above.

Also, the execute permission probably can't be enabled because your files are on a FAT filesystem (most thumbdrives & memory cards are formatted as FAT), which doesn't support such features as file ownerships or permissions like they are used on Unix/Linux operating systems.

...not that the execute permissions would actually even mean anything if they indeed are Windows apps and thus opened with Wine.

---

### Post by beew on 2011-05-18
Who says anything about WINE?

There are Linux portable apps [http://portablelinuxapps.org/](http://portablelinuxapps.org/)

These worked in 10.04 and 10.10 but have stopped working in 11.04

---

### Post by mcduck on 2011-05-18
> **beew said:**
> Who says anything about WINE?

There are Linux portable apps [http://portablelinuxapps.org/](http://portablelinuxapps.org/)

These worked in 10.04 and 10.10 but have stopped working in 11.04

Then it's just the permission problem.

The easy solution is to format the usb drive in some Linux filesystem so you can make the files executable. The downside is that Windows and OS X systems won't be able to access the drive any more.

..and the hard way is to keep the drive as FAT, and tweak the udev rules so that FAT drives get mounted with execute permissions. (previous Ubuntu versions gave files on FAT & NTFS filesystems execute permissions by default, which was changed in 11.04 for security reasons)

---

### Post by beew on 2011-05-18
> **mcduck said:**
> Then it's just the permission problem.

The easy solution is to format the usb drive in some Linux filesystem so you can make the files executable. The downside is that Windows and OS X systems won't be able to access the drive any more.

..and the hard way is to keep the drive as FAT, and tweak the udev rules so that FAT drives get mounted with execute permissions. (previous Ubuntu versions gave files on FAT & NTFS filesystems execute permissions by default, which was changed in 11.04 for security reasons)

I am aware of what you are saying, but these apps just don't work in Natty anymore, and it has nothing to do with FAT or permission. Just download any one  to your Natty box (so there is no issue of FAT) , change the permission and try. They used to work in Mav and Lucid.

---

### Post by mcduck on 2011-05-19
> **beew said:**
> I am aware of what you are saying, but these apps just don't work in Natty anymore, and it has nothing to do with FAT or permission. Just download any one  to your Natty box (so there is no issue of FAT) , change the permission and try. They used to work in Mav and Lucid.

Actually I just tried Chromium and VLC, and both worked fine for me.

Have you tried executing them from a terminal? You might catch some useful error message or something that way..

---

### Post by sid32 on 2011-06-24
I can make programs on usbs executable if I force install "udisks 1.0.1-build1." If I try to make them executable with a newer build of udisks I can't make them executable at all. The permissions just don't stick. 

So its not a fat32 problem as nothing has changed except the udisk build. This is a really anoying bug for me, as I have a python script I need to be able to run from my usb mp3 player, right now I solved the problem by pinned the old udisks version, but would like to be able to use a newer version before this creates problems on my system.

---

### Post by mcduck on 2011-06-25
> **sid32 said:**
> I can make programs on usbs executable if I force install "udisks 1.0.1-build1." If I try to make them executable with a newer build of udisks I can't make them executable at all. The permissions just don't stick. 

So its not a fat32 problem as nothing has changed except the udisk build. This is a really anoying bug for me, as I have a python script I need to be able to run from my usb mp3 player, right now I solved the problem by pinned the old udisks version, but would like to be able to use a newer version before this creates problems on my system.

Yes, it *is* a FAT problem. As the file system lacks support for permissions, all permissions are applied to the whole file system at the time it's mounted (As applying them to individual files would be impossible). The old version of udisk gave all files execute permissions, which was a bit of a security issue so the mounting was changed to remove that permission. Which is why using the old version of udisk helps. (not a bug, then, but a design choice for better security).

What comes to your python script, the permissions shouldn't be an issue unless you try to run it by double-clicking on it (as in trying to execute the python script itself, instead of executing python and giving it the script to run as a parameter, "*python /path/to/your/script.py*")

---

### Post by a1an on 2011-08-22
I noticed that if you change a bash script extension to .exe the permissions magically become executable and you can run the script.

I think the security issue is not worth the wile to remove the ability to run scripts and apps from usb sticks as there is no autorun feature on usb drives in Linux that I am aware of and the ability to run apps across computers is quite useful.

---


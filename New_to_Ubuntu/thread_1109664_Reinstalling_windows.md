---
title: "Reinstalling windows"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Inseki on 2009-03-29
I am only running ubuntu on this computer, and also on my laptop. However I have begun to think it would be useful to have a windows computer, and as this one is older and will be used less I thought of installing windows onto it.

However my vista cd said it could not be written over the partition because it was not "NTFS" format, I may have mistaken that acronym, I didn't write it down.

I've come across this guide
[http://ubuntuforums.org/showpost.php?p=129357&postcount=6](http://ubuntuforums.org/showpost.php?p=129357&postcount=6)

I wouldn't mind dual booting either, although I don't see the point since I have another dedicated linux machine.

Unfortunately I don't know how to do this part
> format your windows partition with fat 32. you can mount it at /windows (or where ever) if you'd like.

I am hoping someone with experience installing windows over ubuntu will be able to help me.

Thank you for any advice in advance m(_ _)m

---

### Post by SunnyRabbiera on 2009-03-29
Eh if vista offers an overwrite just tell it to reformat, I would just ignore the issue and see if it will offer a overwrite.
How old is this computer, how much drive space you have on this computer?
NTFS is the default filesystem of windows XP/Vista if you are wondering.
You may also want to try gparted live, I am not sure if it supports NTFS but see if you can use it to preformat your drive to NTFS.

---

### Post by bpalone on 2009-03-29
If you are going to wipe Linux from the machine you can format it with Gparted.  I am not sure but I think you can run it from the live CD you installed with.  Or, you can download a Gparted Live CD from here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It is all done from a GUI so you be able to figure it out easily.  Just be sure you mean to do what you do.  There is no recovery from an error.

---

### Post by Inseki on 2009-03-29
It doesn't really offer an overwrite version, it just says the drives are incompatible.

This desktop is about 2 1/2 years old, and has about 125 gb of disk space.

Edit: Thank you bpalone, I will try that.

---

### Post by SunnyRabbiera on 2009-03-29
Well like said above try the gparted live CD, I think the Ubuntu offers write support for NTFS as well to create a NTFS drive...
you can try to reformat it that way.

---

### Post by bpalone on 2009-03-29
Forgot this in first post.  Gparted doesn't do NTFS, but will format to FAT32, which Vista should recognize and allow the install.

---

### Post by diablo75 on 2009-03-29
I would think Vista would install on a drive with NO partitions on it, because there's nothing there to overwrite.  I'd just delete everything with gparted, and try it then.

---

### Post by Inseki on 2009-03-29
Thank you to everyone who posted advice in this thread m(_ _)m.

I am now posting from the same desktop currently running windows vista.

I fear this machine will go largely unused now lol.

---

### Post by lovinglinux on 2009-03-29
> **Inseki said:**
> Thank you to everyone who posted advice in this thread m(_ _)m.

I am now posting from the same desktop currently running windows vista.

I fear this machine will go largely unused now lol.

Too late. I would tell you to install Vista inside a [Virtual Machine]("http://en.wikipedia.org/wiki/Virtual_Machine") like Virtualbox on your desktop and keep Ubuntu on the laptop. This way you can enjoy Ubuntu on both machines and access Windows Vista whenever you need, without rebooting.

---


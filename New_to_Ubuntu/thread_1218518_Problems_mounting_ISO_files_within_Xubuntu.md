---
title: "Problems mounting ISO files within Xubuntu"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-07-20
Hey there,

I have tried to use the mount.sh and unmount.sh scripts from [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html) in a fresh install of xubuntu.  I have done this successfully before in ubuntu, but when i try it here I get this message within the terminal (this is a full transcript of the attempt):

matthew@matthew-laptop:~$ sudo chmod +x /home/matthew/mount.sh
[sudo] password for matthew: 
matthew@matthew-laptop:~$ sudo chmod +x /home/matthew/unmount.sh
matthew@matthew-laptop:~$ sudo mv /home/matthew/mount.sh ~/.gnome2/nautilus-scripts/
mv: accessing `/home/matthew/.gnome2/nautilus-scripts/': Not a directory
matthew@matthew-laptop:~$ sudo mv /home/matthew/unmount.sh ~/.gnome2/nautilus-scripts/
mv: accessing `/home/matthew/.gnome2/nautilus-scripts/': Not a directory
matthew@matthew-laptop:~$ 

Any suggestions?  Thanks in advance for any help.

--Red

---

### Post by bandgeek on 2009-07-20
Try this mkdir ~/.gnome2/nautilus-scripts/ then try to copy again.

---

### Post by Redmage913 on 2009-07-20
another error...

matthew@matthew-laptop:~$ mkdir ~/.gnome2/nautilus-scripts/
mkdir: cannot create directory `/home/matthew/.gnome2/nautilus-scripts/': File exists

---

### Post by Redmage913 on 2009-07-20
however, it worked.  the script copied successfully, i'm guessing - there doesn't seem to be any sort of confirmation for many terminal commands.

oh, another problem. i installed gnome and started using that, but my standard file manager program does not work. I have to use Thunar File Manager to interface with my file system.  any way to reset the default file manager?

---

### Post by bandgeek on 2009-07-20
First see if it copied successfully by going to ~/.gnome2/nautilus-scripts/ and/or trying to use it.

For your information ~/ stands for /home/*homefolder name*

The default file manager is called Nautilus so in a terminal type:
sudo apt-get install Nautilus

---


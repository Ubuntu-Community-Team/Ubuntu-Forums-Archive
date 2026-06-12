---
title: "don't have necessary permissions to edit file"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-03-23
im trying to edit /etc/init.d/mountdevsubfs.sh in an attempt to get usb working virtualbox but when i go to save the text file it won't let me please help me out here

---

### Post by mvalviar on 2009-03-23
gksudo gedit <filename>

Can be issued on the terminal or Alt-F2

---

### Post by bruce2000 on 2009-03-23
This should do it:

> 
gksu gedit /etc/init.d/mountdevsubfs.sh


---

### Post by rhcm123 on 2009-03-23
> **mamamia88 said:**
> im trying to edit /etc/init.d/mountdevsubfs.sh in an attempt to get usb working virtualbox but when i go to save the text file it won't let me please help me out here

I'm going to make the assumption that you know what you are doing after you get the file open. I'll snip this command if the community thinks otherwise.

You need root privilages to do that. Just use sudo to open the file. eg:
```
sudo nano /etc/init.d/mountdevsubfs.sh
```

---

### Post by mamamia88 on 2009-03-23
ok that worked now i have to put 
  #
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

after the do_start() function  do i put it after the TTYMODE or the }?

---

### Post by Kareeser on 2009-03-23
You should just have to put it at the end.......

---

### Post by bodhi.zazen on 2009-03-23
I do not know what you are doing exactly, but see this post for how to enable usb devices :

[http://ubuntuforums.org/showpost.php?p=6122145&postcount=4](http://ubuntuforums.org/showpost.php?p=6122145&postcount=4)

With the PUEL edition, usb devices work out of the box. Are you sure you need to edit this file ? And what how to are you following, you syntax looks way off.

---

### Post by mamamia88 on 2009-03-23
ok i manged to get it working thanks for all the help

---

### Post by dweible75 on 2009-03-23
> **mamamia88 said:**
> im trying to edit /etc/init.d/mountdevsubfs.sh in an attempt to get usb working virtualbox but when i go to save the text file it won't let me please help me out here


Usually, whenever you get a save error indicating lack of permission it means you are trying to edit a file as a user that requires you to have root privileges.

There are a number of ways to gain the permissions you need to be able to properly edit and configure the file you mention. Many of them have already been submitted to you in this thread. I just want to make sure that you understand why it happened so that if you run into a similar problem in the future you will know the why and how of it.

Using the **sudo** command in a terminal window or in the console (Alt + F1) allows you to gain super user privileges for the command given after sudo, thus typing:

```
sudo <name of your editing program> /path/to/file
```

will give you the permissions required to make changes and save a file normally only allowed access by root users. And these permissions are only granted on a temporary basis, meaning, for the duration of time with which you use the editing program you invoked with the sudo command. Once you exit the editing program your privileges revert back to their default setting and if you try to open the editing program again without using sudo to edit a root-access-only file you will be unable to save your changes.

Another piece of advice: whenever you make changes to system documents always back them up first. Most editors will do it for you now, but never make that assumption. Saving a copy of any document you open and appending a .old or .backup to the name of the file before you begin to edit it is a good practice in. It gives you something to go back to in case you manage to fubar your system with an accidental editing error.

---

### Post by bodhi.zazen on 2009-03-23
If you are going to edit a file in a terminal, use :

```
sudo -e /path/to/file_to_edit
```

Set your editor in .bashrc if you like 

EDITOR=/bin/nano

If you are going to edit a file with an X application (like gedit) use gksu

```
gksu gedit /path/to/file_to_edit
```

so, if you are going to run X apps as root, use gksu (kdesudo if running KDE).

---


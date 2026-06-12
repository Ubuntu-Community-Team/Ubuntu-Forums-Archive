---
title: "I need help"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by Bioboy725 on 2011-05-29
I'm new to ubuntu and need help. I tried to update my ubuntu and when I turned my laptop back on it displayed a message while booting.

Starting up …
mount: mounting none on /dev failed: No such device
Udevd[866]: error initializing netlink socket

libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument
Segmentation fault
Gave up waiting for root device. Common problems:
  - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/module; ls /dev)
ALERT! /dev/disk/by-uuid/6c21f30e-4c2e-4af6-9d80-97355f6ff2d1 does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of commands.

(intitramfs) 





(no longer message) If it helps the computer  is a Dell latitude

---

### Post by Rubi1200 on 2011-05-29
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Bioboy725 on 2011-05-29
I'm not sure what you mean by cd/usb
I Upated it using an update manager then restarted the laptop and it displayed the message from my first post on a black screen.
I have no idea what to do to get it to the desktop.

---

### Post by khelben1979 on 2011-05-29
If you have no important files on the Ubuntu system which needs backup, simply reinstall Ubuntu.

Otherwise you can get yourself another hard disc, install Ubuntu on this one, copy over files from your old hard disc to your new one. I think it's easier than struggling with scripts as you're a newbie in this and probably just want your Ubuntu back and working for you.

If the budget don't allow this, you'll need to struggle to get this working. I think the advice with Rubi1200 is OK for that purpose.

---

### Post by Bioboy725 on 2011-05-29
I know I'm going to sound stupid but can you explain to me how I am to reinstall ubuntu if all my laptop does is stay at a black screen with the message from my first post. I know that was probably a stupid question but oh well.

---

### Post by wildmanne39 on 2011-05-29
> **Bioboy725 said:**
> I know I'm going to sound stupid but can you explain to me how I am to reinstall ubuntu if all my laptop does is stay at a black screen with the message from my first post. I know that was probably a stupid question but oh well.Hi, just insert the livecd or usb disc you used the first time,then restart the computer.

---

### Post by Bioboy725 on 2011-05-29
Could one of you explain where I could get the cd. The computer was given to me with ubuntu already on it. 
Sorry for having to ask so many questions.

---

### Post by Thewhistlingwind on 2011-05-29
> **Bioboy725 said:**
> Could one of you explain where I could get the cd. The computer was given to me with ubuntu already on it. 
Sorry for having to ask so many questions.

It's K.

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Burn that ISO to CD, the contents, not the ISO.

---

### Post by Rex Bouwense on 2011-05-29
Using the computer that you are now posting with download Ubuntu at
[http://www.ubuntu.com/](http://www.ubuntu.com/)
You can then burn that ISO to a CD or a flash drive.
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
The second site also explains how to do all of that good stuff.
Enjoy
Rex

---

### Post by wildmanne39 on 2011-05-29
> **Bioboy725 said:**
> Could one of you explain where I could get the cd. The computer was given to me with ubuntu already on it. 
Sorry for having to ask so many questions.Hi, also if you are using a windows system you need to read on the download site about how to burn the iso it will tell you to install a program that will allow you to burn it. I think one of them is called infra recorder.

---

### Post by webofunni on 2011-05-29
That error means that kernel is not able to mount none to /dev. In grub screen how many entries you can see ? 

With default entry highlighted in grub press letter e and see the version of vmlinuz. 

see the line that looks like "vmlinuz-2.6.38-8-generic" and find the version, here for eg 2.6.38. It seems you are booting the old kernel.

---

### Post by taidaniel on 2011-05-29
Or you could also down load unetbootin and make a live USB yourself. Download it from [here.]("http://unetbootin.sourceforge.net/") Check the website for instructions.

If you don't mind my asking, how did you install ubuntu in the 1st place?

---


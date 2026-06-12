---
title: "Trouble Mounting"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by Deedlit on 2009-09-15
I am running Hardy (still) and periodically have trouble mounting flash drives, cameras, mp3 players. All of which have at one time or another mounted without a hitch are now giving me errors and telling me I do not have permission to mount this. I have dried mounting as root, which is very confusing for me, and this ends up not working. I'm wondering if switching to Jaunty would help, or if I should stay with Hardy and find some kind of fix.

---

### Post by HarrisonNapper on 2009-09-15
First, make sure you have admin privileges by entering the following command into the terminal:
> 
less /etc/group |grep -i admin
This will look something like the following if you are:
> 
admin: x :110:root,yourusername
If not, enter the following in to the terminal:
> 
sudo usermod -a -G <yourusername>
Let us know if it works.

---

### Post by HarrisonNapper on 2009-09-15
Also, there is a way of doing this graphically so that you don't have to use the terminal; let me know if you would prefer to do it that way.

---

### Post by Deedlit on 2009-09-16
Okay, I ran the command in terminal and it came back similar but not the same.

Here's what I got
lpadmin:x:109:myusername
admin:x:115:myusername

Thank you so much for your help!

---

### Post by Deedlit on 2009-09-16
Although, the emoticon was not there it was actually

lpadmin: x:109:myusername
admin: x:115:myusername

---

### Post by unutbu on 2009-09-16
Please post the output of 
```

ls -ld ~/.gvfs
```

Perhaps this directory (which is used when mounting certain devices) has the wrong permissions. This may (or may not) reveal the problem.

---

### Post by Deedlit on 2009-09-17
dr-x------ 3 deedlit deedlit 0 2009-09-14 01:09 /home/deedlit/.gvfs
deedlit@eeyore:~$

---

### Post by unutbu on 2009-09-17
Okay, that did not reveal the problem.

Are all the devices (flash drive, camera, mp3 player) connected via USB cable?

What output do you see when you plug one of those devices in and type
```

lsusb
lsmod | grep usb
ps axu | grep gvfs
```

---

### Post by Deedlit on 2009-09-17
All the devices connect via usb hub. When I plugged the flash drive in, it mounted right up. Of course because I didn't want it to. I guess I will mark this as solved, since it is working. I just don't know for how long. Thank you for your help.

---


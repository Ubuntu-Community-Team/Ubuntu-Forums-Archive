---
title: "Error Mounting at start up"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by GMarkow on 2010-11-07
Hi all,
   I recently installed Ubuntu 10.4. I booted once and everything went great. However after a restart the system now hangs up at start up saying "Error mounting 0" with an option to skip or repair manually. If I skip nothing happens, if I repair manually I get put to the terminal where I am very confused. How do I fix this???

If my /ect/fstab is of help it reads...

# / was on /dev/sdb2 during installation
UUID=4862-blah-blah / ext4  errors=remount-ro 0 1

# swap was on /sdb6 during installation UUID=c15bd-blah-blah none  swap  sw 0 0

/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0  0

//Workgroup/mp3 /media/My Book/MP3
guest,uid=1000,iocharset=utf8,codepage-unicode,unicode 0 0

---

### Post by cariboo on 2010-11-08
I would suggest once you are at the prompt, start up nano and comment out the line. Then once you are back at the desktop you can diagnose the problem. Once you have logged in at the prompt type:

```
sudo nano /etc/fstab
```

then scroll down to the line for the mount that doesn't work add put a # in front of it:

```
#//Workgroup/mp3 /media/My Book/MP3 guest,uid=1000,iocharset=utf8,codepage-unicode,unicode 0 0
```

then press Ctrl-O to save and Ctrl-X to exit, then you can either start the desktop by typing:

```
startx
```

or reboot:

```
sudo reboot
```

Once you are back at the desktop, open a terminal and type:

```
sudo mount -a
```

the above command will try try to mount the drive, and when it can't, it will give you an error message that will help you solve the problem.

---

### Post by sikander3786 on 2010-11-08
I hope **cariboo907's** fix will work for you. But incase it doesn't, it would be handy if you post the complete output of these commands from your desktop.

```
cat /etc/fstab
```

and

```
sudo blkid
```

Is there a floppy drive present really?

---


---
title: "I can't open my cd drive in Ubuntu"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by st4 on 2009-04-15
I just received my Ubuntu cd in the mail. I decided to do a clean install of it on my pc. I think I deleted windows but I'm not sure.

And now I can't get the disk drive compartment to open;) What am I doing wrong?

---

### Post by st4 on 2009-04-15
I get this error message

[I]There was an error ejecting the volume or drive.

org.freedesktop.Hal.Device.Volume.UnknownFailure: Cannot open /media/.hal-mtab [/I]

---

### Post by sahabcse on 2009-04-15
Have you installed ubunut? 
Type the command in terminla

#sudo eject

---

### Post by st4 on 2009-04-15
Hi, thanks for the reply. Yeah, I'm using Ubuntu right now. Can you tell where to put the command? I know it sounds very n00bish, but I would appreciate that very much. Thank you

---

### Post by |Mitch| on 2009-04-15
applications/accessories/terminal is where you type the command

---

### Post by st4 on 2009-04-15
It didn't work. Is there anything else I can do? And it also didn't ask me for my username and password.

---

### Post by |Mitch| on 2009-04-15
don't put the # in front of the sudo

---

### Post by st4 on 2009-04-15
I got this message in the terminal,



To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo eject
umount: /cdrom: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
eject: unmount of `/cdrom' failed
ubuntu@ubuntu:~$

---

### Post by stumbleUpon on 2009-04-15
You have some processes running that are accessing the cdrom. Close all windows and try again to eject as earlier. If not just restart the machine once and all processes using the cdrom will be killed.

---

### Post by st4 on 2009-04-15
Thanks, I restarted my pc and for a second the disk drive opened and closed long enough for me to get the Ubuntu cd out. Then it went back into dual boot mode and I chose Vista.

It says in the Ubuntu cd sleeve that the default installation of Ubuntu deletes all of the existing software and data from your computer. Why didn't this happen?

---

### Post by |Mitch| on 2009-04-15
You have to delete the Vista partition to do that, I don't think you actually installed Ubuntu. I think you were just merely running from the Live CD. Reboot with the disk in the drive and delete the Vista partition to install ubuntu on the whole drive.

---

### Post by stumbleUpon on 2009-04-15
As |Mitch| said, it looks like you have not installed ubuntu but have merely been using the live CD (and thats why you were not able to eject it :) ).

This guide has step by step instructions with pictures to install the desktop CD.

[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

This is for installing in dual boot mode. There are others in the left frame in the above site which you can look up for more information.

---

### Post by st4 on 2009-04-15
Thanks again guys, I appreciate it.

---


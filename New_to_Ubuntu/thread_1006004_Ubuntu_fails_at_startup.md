---
title: "Ubuntu fails at startup"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by hortie on 2008-12-08
I am new to ubuntu and am having trouble at startup.  I am writing to please solicit advice on what to try next-- locate and save my files using the ubuntu CD at startup followed by reinstall, or perhaps a better option.

I have no idea what went wrong, so at the risk of being verbose, I am providing all obvious info below:

I installed ubuntu 8.10 on my Dell Inspiron E1505 (previously running only Win XP) using the Install Inside Windows option.

Ran great for months, then suddenly upon startup, no friendly user interface as usual-- instead I now arrive at the grub prompt.

I have no idea what that means, so I figured I would try to reinstall.  I tried to access the ubuntu user interface via by starting up with the installs CD, but had to allow an installation of a file from the installs CD prior to restart to boot ubuntu from the CD upon restart.

Anyway, I can access the user interface now, but have no idea how to locate the files I would like to copy prior to reinstalling the software.

Can I please bother someone to help me locate my files prior to reinstall?

Alternately, is there something smarter I can try?

Thanks.

---

### Post by theozzlives on 2008-12-08
All your files should be in /home/user

---

### Post by hortie on 2008-12-08
thanks ozzie.

How may I access /home/user when starting from the installs cd?

---

### Post by caljohnsmith on 2008-12-08
You should be able to mount your Wubi Ubuntu install from the Live CD and recover your files if the Ubuntu partition file is not corrupted; first boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -l
```
And look for your Windows NTFS or FAT partition; it will probably be sda1 or sda2 if you have a recovery partition. Once you know which partition Windows is on, just do:
```
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt
sudo mkdir /Ubuntu
sudo mount -o loop /mnt/ubuntu/disks/root.disk /Ubuntu
gksudo nautilus /Ubuntu &
```
And replace sdaX above with the Windows partition. After doing the last command, you should see your Ubuntu root directory in the Nautilus file browser. How about giving that a shot, and if you run into problems, let me know and we can work from there. :)

---

### Post by hortie on 2008-12-08
thanks.

I made it to:

sudo mount -o loop /mnt/ubuntu/disks/root.disk /Ubuntu

but then got the following error:

/mnt/ubuntu/disks/root.disk: No such file or directory

---

### Post by hortie on 2008-12-09
Ubuntu 8.10 is not starting up for some reason-- I default to grub not the ubuntu user interface.

I have posted previously in an attempt to recover my files from ubuntu before I reinstall.  There have been replies, but they have not worked, and now there are no more replies.

I have listed the suggestions from the user community below, and why they have not worked.

Can I please bother everyone for other suggestions for _how to recover my files from ubuntu after booting with the install CD (I think this is called livecd)?_  I appreciate your help, but am still stuck, so any other suggestions would be very much appreciated.



_Previous Suggestions That Have Not Worked_

(1) All your files should be in /home/user
> This did not work b/c I cannot see /home/user when starting from installs cd

(2) sudo mount /dev/sdaX /mnt
sudo mkdir /Ubuntu
sudo mount -o loop /mnt/ubuntu/disks/root.disk /Ubuntu
gksudo nautilus /Ubuntu &

> This results in an error /mnt/ubuntu/disks/root.disk: No such file or directory . . . I have tried variations on suggestion #2, but cannot see my files.

---

### Post by kojo on 2008-12-09
I was able to recover files this way.  I used a partition program, gparted, to mount the hard drive partition containing my files.  I then was able to find those files and recover them.

I believe gparted is already on the live cd.

launch it from a terminal window
```
gparted
```

you may have to launch as root
```
sudo gparted
```

Don't give up!  :KS

---

### Post by Sef on 2008-12-09
I have used [Knoppix]("http://knoppix.com") for recovering files.

---

### Post by Pjotrovitz on 2008-12-09
This should be easy.

When you boot the liveCD and open Nautilus, you should see some drives in the left panel. They are usually labeled by their size. Click on them to mount them, one of them should be your old root partition (if you had a separate home partition, it will look a bit different). When you have found your old root partition, go to /home/<your old username>/ on that partition. You should now be able to put the files you need on a removable drive or whatever.

Good luck!

---

### Post by hortie on 2008-12-09
Thanks everyone-- if I used the Install Within Windows option, am I still looking for a partition?

---

### Post by Pjotrovitz on 2008-12-09
Ouch.. That explains a lot. Let me research wubi a bit and get back to you. Your files are inside a virtual hard drive inside your windows drive, I'm not sure how to get anything out of it. In the future: The install inside windows option is mostly for an extended preview. I'ts not smart to put files on it that you can't afford to loose.

---

### Post by Pjotrovitz on 2008-12-09
If you can boot windows, take a look at this:

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?)

If not, boot the live cd, mount the windows partition, go to ubuntu\disks\ on it and tell me what you find there.

---

### Post by caljohnsmith on 2008-12-09
OK, how about posting the full output of all the commands, including the fdisk command, so I can get a better idea of what the issue might be. If you can, just copy/paste the entire terminal session so I can see everything that way.

---

### Post by handydan918 on 2008-12-09
> **hortie said:**
> Ubuntu 8.10 is not starting up for some reason-- I default to grub not the ubuntu user interface.

I have posted previously in an attempt to recover my files from ubuntu before I reinstall.  There have been replies, but they have not worked, and now there are no more replies.

I have listed the suggestions from the user community below, and why they have not worked.

Can I please bother everyone for other suggestions for _how to recover my files from ubuntu after booting with the install CD (I think this is called livecd)?_  I appreciate your help, but am still stuck, so any other suggestions would be very much appreciated.



_Previous Suggestions That Have Not Worked_

(1) All your files should be in /home/user
> This did not work b/c I cannot see /home/user when starting from installs cdYou won't find a directory called /home/user. You will find a directory called /home/hortie or /home/whateverusernameyousetupwhenyouinstalledUbuntu.> 

(2) sudo mount /dev/sdaX /mnt
sudo mkdir /Ubuntu
sudo mount -o loop /mnt/ubuntu/disks/root.disk /Ubuntu
gksudo nautilus /Ubuntu &

> This results in an error /mnt/ubuntu/disks/root.disk: No such file or directory . . . I have tried variations on suggestion #2, but cannot see my files.

---


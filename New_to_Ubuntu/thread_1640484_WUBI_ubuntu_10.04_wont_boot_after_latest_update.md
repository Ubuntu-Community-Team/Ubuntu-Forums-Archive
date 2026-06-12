---
title: "WUBI ubuntu 10.04 wont boot after latest update"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by REMIX8604 on 2010-12-07
i updated few days ago. i restarted and now when i choose the ubuntu option it restarts my laptop, and gives me the choice between windows and ubuntu again and again. i read another post that might help me about change some .cfg file but i have no idea how to get to it. im not sure how to pull up a terminal at this point. right now im just stuck with windows and a dead ubuntu. im going to make a live usb right now to see if i can at least get to my files thru that.

thanks in advance for the help

---

### Post by bcbc on 2010-12-07
See [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) problem #2, fix #1 - and also the permanent fix further below.

---

### Post by REMIX8604 on 2010-12-08
> 
ubuntu@ubuntu:~$ sudo mkdir /media/win
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/win
ubuntu@ubuntu:~$ sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
/media/win/ubuntu/disks/root.disk: No such file or directory

  this is far as i get. im having trouble identifying my windows partition that contains the root.disk

im not sure what you ment by identify the windows partition. does that mean to switch to the directory that contains the root.disk file?

---

### Post by bcbc on 2010-12-08
Your main windows partition may not be the first physical partition - maybe you have a hidden recovery partition etc.

So if it's not on /dev/sda1, then just unmount it and try the next:
```
sudo umount /dev/sda1
sudo mount /dev/sda2 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

```
etc. until you find it then continue the instructions.

This will give you a list of partitions```
sudo blkid
```

---

### Post by bcbc on 2010-12-08
Actually, run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") - it will tell you where it is, or paste back the results and I'll check it out.

---

### Post by amjjawad on 2010-12-08
> **REMIX8604 said:**
> this is far as i get. im having trouble identifying my windows partition that contains the root.disk


[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Edit:
Oh, bcbc already posted that :)

---

### Post by REMIX8604 on 2010-12-08
here you go, i pastied my results. 

[http://www.pastie.org/1358181](http://www.pastie.org/1358181)

i cant make much sense of this. but if i had to guess id say sda3

---

### Post by REMIX8604 on 2010-12-08
*UPDATE* it was in sda3 and it worked just fine. it took me awhile but im good now.

THANK YOU VERY MUCH!!

now i think i understand how wubi works aswell. please correct me if i have this wrong. instead of doing a partition it works more like daemon tools, mounting and unmounting a virtural disk. root.disk is just like an .iso? so if i want to get my files from (wubi) ubuntu i mount the root.disk file and go in there to find any files i may need. 

am i close? either way i love ubuntu and its fun trying something new.

---

### Post by amjjawad on 2010-12-08
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bcbc on 2010-12-08
> **REMIX8604 said:**
> *UPDATE* it was in sda3 and it worked just fine. it took me awhile but im good now.

THANK YOU VERY MUCH!!

now i think i understand how wubi works aswell. please correct me if i have this wrong. instead of doing a partition it works more like daemon tools, mounting and unmounting a virtural disk. root.disk is just like an .iso? so if i want to get my files from (wubi) ubuntu i mount the root.disk file and go in there to find any files i may need. 

am i close? either way i love ubuntu and its fun trying something new.

Yes, wubi installs ubuntu to a virtual disk. It's mounted as a loop device - which simulates a block device like a partition. That way you don't have to create a physical partition for it.

Great you got it fixed :)

---

### Post by Rubi1200 on 2010-12-08
Although I updated the thread and added that the user needs to substitute sda1 for whatever is the correct Windows partition, I think I will add something else as well since this does appear to be causing some confusion.

And, great you got it fixed too :)

---


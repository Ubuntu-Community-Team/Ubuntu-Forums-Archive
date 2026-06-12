---
title: "[SOLVED] Permissions"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Starbase 9525 on 2009-01-06
I added another hard drive to my Ubuntu 8.04 box and was able to somehow get it mounted. It shows up on my desktop and I can access it, but when I try to drag a folder to it I get the message "Error while copying. The folder "folder" cannot be copied because you do not have permissions to create it in the destination." If I right click the drive on the desktop it says the permissions of the disk could not be determined. If I access the drive and right click inside of it it shows root as the owner. How do I change the permissions so I can drag and drop files to this drive? I am new to Linux.

---

### Post by JoshuaRL on 2009-01-06
Well, how did you end up mounting it?  What commands did you use?

---

### Post by Starbase 9525 on 2009-01-06
I believe this is what I did in terminal;

sudo mkdir /mnt/forty
sudo mount /dev/sdb1 /mnt/forty
sudo df /mnt/forty

---

### Post by Zeroberry on 2009-01-06
Is it possible to mount as user instead of root? That might be your problem.

---

### Post by Starbase 9525 on 2009-01-06
> **Zeroberry said:**
> Is it possible to mount as user instead of root? That might be your problem.

How would I do that? And if I do that would I have to unmount the drive, and what would be the best way to do that?

---

### Post by Zeroberry on 2009-01-06
I'm not very good with the commands but you can run nautilus as root (hasn't messed anything up for me so far xD) and unmount using that.

sudo nautilus

in terminal

---

### Post by Starbase 9525 on 2009-01-06
> **Zeroberry said:**
> I'm not very good with the commands but you can run nautilus as root (hasn't messed anything up for me so far xD) and unmount using that.

sudo nautilus

in terminal

Ok, but then how would I mount as user instead of root?

---

### Post by JoshuaRL on 2009-01-06
Well, as I understand it all filesystems not in fstab mount with root permissions.  That's why it is like that.  To unmount do this:
```
sudo umount /mnt/forty
```

Also, you would probably want to mount filesystems to /media, that's where Ubuntu usually does it.  I know there are other distros (puppy for sure) that use /mnt, but Ubuntu does it different.

[Here is bodhi_zazen's guide to fstab to help with mounting this drive.](http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab)  I'm working through it myself for a media player that has been giving me fits.

---

### Post by oldos2er on 2009-01-06
> **Zeroberry said:**
> I'm not very good with the commands but you can run nautilus as root (hasn't messed anything up for me so far xD) and unmount using that.

sudo nautilus

in terminal

 When calling a graphical program such as Nautilus, use 'gksu' in place of 'sudo.' Here's why: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by JoshuaRL on 2009-01-06
Well, I forgot about this.  It's [the Psycocats tutorial on automounting](http://www.psychocats.net/ubuntu/mountwindows) internal drives, by aysiu.  Couldn't be easier.  Sorry for sending you to fstab.  BIG chunk of info.

---

### Post by Starbase 9525 on 2009-01-06
> **JoshuaRL said:**
> Well, I forgot about this.  It's [the Psycocats tutorial on automounting](http://www.psychocats.net/ubuntu/mountwindows) internal drives, by aysiu.  Couldn't be easier.  Sorry for sending you to fstab.  BIG chunk of info.

Yeah, I was wading through that and trying to find the info I needed. I got the drive listed in fstab and thought I set the user id to me but when I mounted it again it still wouldn't let me drag and drop. I think I will look at your other recommendation.

---

### Post by JoshuaRL on 2009-01-06
> **Starbase 9525 said:**
> Yeah, I was wading through that and trying to find the info I needed. I got the drive listed in fstab and thought I set the user id to me but when I mounted it again it still wouldn't let me drag and drop. I think I will look at your other recommendation.

That's my problem, I get a new hammer and then every problem is a nail.  That post I linked you earlier is the answer to a nagging issue I've had for a couple months, and I got excited.  But the Psychocats tutorial should be for you.

---

### Post by Starbase 9525 on 2009-01-06
The tutorial that the link pointed to was about mounting NTFS drives, mine was ext3. However that tutorial was part of a site that had another tutorial on mounting linux filesystems so I found the info I needed and it worked(when I followed the steps correctly). Thanks for the information. My next goal is to set up something to take the files I put on this drive and compare them to the laptops they came off of and back up any changes. Old dog has to learn new tricks.
Thanks again.

---

### Post by b0b138 on 2009-01-06
[https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20A%20Mount%20Point](https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20A%20Mount%20Point)

---


---
title: "I need to access microsofts system32 folder using ubuntu"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Cyber Altair on 2009-04-04
Everytime I try to open the hard disk where my windows vista is installed I get a Can't mount volume error.

Reason I need to access is that I messed up some .dll files meaning I can't access windows to fix it and I have a cd from which I booted my computer with.

Any ideas on how to open the system32 folder?

---

### Post by jelle_ on 2009-04-04
look in the locations tab from the taskbar to mount your windows-partition. then choose windows and system32

---

### Post by Cyber Altair on 2009-04-04
Don't mean to be an a$$ here but a screenshot of some sort would be really helpful or at least a broken down step by step since I'm really new to the whole Ubuntu experience.

---

### Post by Nepherte on 2009-04-04
Open nautilus (file browser) by pressing Alt + F2, type nautilus and press enter. The file browser should now open and at the left side you should see your windows disk under "location" somewhere. Click on it and it should be mounted.

---

### Post by Cyber Altair on 2009-04-04
I still get the cannot mount volume window.

---

### Post by Mrandersonjr on 2009-04-04
Go to filesystem,then go to media and click on disk (if that is your default hard drive) and it should mount,if not,try to mount it with Gparted.If that doesn't do the trick,Go to Filesystem then /etc and finally fstab and list the contents of that file,and whatever the drive is you are trying to mount,put a # infront of it and make sure there is a space.

If it won't save after the change,Open the terminal type sudo su and it will ask for your password,enter it.

THEN enter: gedit /etc/fstab
and make the changes then save.
(The changes being putting a # in front of the drive you are trying to mount.)
and make sure there is a space between # and the start of the path of your drive)
Then Ctrl+Alt+Backspace and log in again and it should mount.

---

### Post by halitech on 2009-04-04
> **Cyber Altair said:**
> I still get the cannot mount volume window.

sounds like the drive was not unmounted cleanly in windows in which case Ubuntu won't mount it to prevent it from doing any further damage to the filesystem. You could try to force mount it but it could make things worse.

---

### Post by sandyd on 2009-04-04
FYI, info for people helping him 

he needs to "force" his partition to be mounted (using ntfs-3g) b/c he has not shut down his computer properly



@OP. while your waiting, go to Acessories => Terminal 
type in
```

sudo fdisk -l

```post the results here (copy and paste i mean)

OR, if your windows partition is the first on your hard disk, just type this in (theirs no waranty, as this can make it worse...)
```

mount -t ntfs-3g /dev/sda1 /media/sda1/ -o force

```then go to /media/sda1
 
EDIT: just saw the person who posted in front of me.

---

### Post by Cyber Altair on 2009-04-04
The drive's name is 209.7 GB Media so basically I should open fstab then in a new line type "# 209.7 GB Media" then save it?

At the above poster, I got this

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ba10ba0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       38912   107764020    f  W95 Ext'd (LBA)
/dev/sda5           25497       38912   107763988+   7  HPFS/NTFS

---

### Post by halitech on 2009-04-04
hold off for now on making any changes to fstab. Post the output of sudo fdisk -l as carlee suggested

---

### Post by linuxuser21 on 2009-04-04
> **halitech said:**
> sounds like the drive was not unmounted cleanly in windows in which case Ubuntu won't mount it to prevent it from doing any further damage to the filesystem. You could try to force mount it but it could make things worse.

No, I'm trying to do it via Virtualbox to get him a screenshot.  I'm getting an error too.  It acts like it's not mounted.

---

### Post by gandaran on 2009-04-04
> **Cyber Altair said:**
> I still get the cannot mount volume window.
can you provide some details of your setup? are you dual booting windows and ubuntu or just using the live cd to access the windows partition, if dual booting go you have more than one hard disk? 
can you see the mounted windows partition in ubuntu?
using the live cd would be a lot better if you are having problems finding the windows partition, run the live cd then open terminal and type **sudo -i**, now navigate with the root nautilus windows to the mounted windows and change whatever you want.

edit;
should read **sudo -i nautilus** sorry!

---

### Post by sandyd on 2009-04-04
> **Cyber Altair said:**
> The drive's name is 209.7 GB Media so basically I should open fstab then in a new line type "# 209.7 GB Media" then save it?

At the above poster, I got this

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ba10ba0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       38912   107764020    f  W95 Ext'd (LBA)
/dev/sda5           25497       38912   107763988+   7  HPFS/NTFS
type this in
```

mount -t ntfs-3g /dev/sda1 /media/sda1/ -o force

```then go to /media/sda1 

done

---

### Post by linuxuser21 on 2009-04-04
Is it looking like this?

---

### Post by linuxuser21 on 2009-04-04
Oh, I've seen this problem before, you just don't have Windows shutdown correctly.  Just shut it down from the Start menu.

---

### Post by Cyber Altair on 2009-04-04
I did.
Also i tried this: -

mount -t ntfs-3g /dev/sda1 /media/sda1/ -o force

and got a "mount: only root can do that".

No it doesn't look like that screenshot linuxuser21. I'll try shutting my computer down.

Also I'm booting Ubuntu from a CD.

---

### Post by halitech on 2009-04-04
do it as sudo
```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1/ -o force
```

---

### Post by albinootje on 2009-04-04
> **Cyber Altair said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       38912   107764020    f  W95 Ext'd (LBA)
/dev/sda5           25497       38912   107763988+   7  HPFS/NTFS

Okay, try this :
```

sudo mkdir /media/windows1
sudo mkdir /media/windows2
sudo ntfs-3g /dev/sda1 /media/windows2 -o force,uid=1000,umask=000
sudo ntfs-3g /dev/sda5 /media/windows2 -o force,uid=1000,umask=000

```
After that browse to /media in your file manager.

---

### Post by Cyber Altair on 2009-04-04
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/sda1/: No such file or directory


I got that. I'll try turning my computer off then trying again

---

### Post by halitech on 2009-04-04
> **linuxuser21 said:**
> Oh, I've seen this problem before, you just don't have Windows shutdown correctly.  Just shut it down from the Start menu.

if the OP could boot then he would be able to fix the windows problem from windows but since he cant boot the system, shutting it down from the start menu isn't going to work

---

### Post by linuxuser21 on 2009-04-04
> **halitech said:**
> if the OP could boot then he would be able to fix the windows problem from windows but since he cant boot the system, shutting it down from the start menu isn't going to work

Oh, yeah... I knew that.  lol.

---

### Post by albinootje on 2009-04-04
> **Cyber Altair said:**
> 
fuse: failed to access mountpoint /media/sda1/: No such file or directory

```

sudo mkdir /media/sda1

```
and try again.

---

### Post by Cyber Altair on 2009-04-04
I tried down my computer then tried to open it. Luckily the volume I wanted to open and I did the changes I needed to do.

Thanks for all the help guys. Damn Ubutnu is really confusing.

---

### Post by halitech on 2009-04-04
> **Cyber Altair said:**
> I tried down my computer then tried to open it. Luckily the volume I wanted to open and I did the changes I needed to do.

Thanks for all the help guys. Damn Ubutnu is really confusing.

its only confusing because its different then windows. Personally I find working on windows computers confusing now because I've been using Linux for the last 3 years at home and only occasionally touch a windows computer.

glad to hear you got it fixed up though

---

### Post by albinootje on 2009-04-04
> **Cyber Altair said:**
> Damn Ubutnu is really confusing.

Step by step you will see some logic and hopefully understand things.

Please do some reading here :
[http://www.ubuntupocketguide.com/download.html](http://www.ubuntupocketguide.com/download.html)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Cyber Altair on 2009-04-05
Thanks.

I guess it's because I'm really into windows I find everything so different. Ubuntu layout is rather better then Windows tbh.

---


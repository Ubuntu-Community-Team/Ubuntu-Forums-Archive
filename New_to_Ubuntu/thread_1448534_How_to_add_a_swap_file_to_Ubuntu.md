---
title: "How to add a swap file to Ubuntu"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by lsk3993 on 2010-04-06
Hi,

I've just installed Ubuntu in a dual boot with Windows 7 and made a large partition to be shared between the two OS's.
I wish to create a 4GB swap file for Ubuntu in this shared partition as it's the only space left on the drive now.

I had a look at the [relevant bit of the swap FAQ]("https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?") on help.ubuntu.com and from what I understand I need to do:
```
sudo dd if=/dev/zero of=/mnt/512Mb.swap bs=1M count=512
```I was told that for a computer with 4GB RAM and a 320GB HD I should use 4GB swap however when I tried:
```
sudo dd if=/dev/zero of=/media/shared4096Mb.swap bs=1M count=4096
```it didn't work, it just seems to be doing nothing.

What have I done wrong?
Thanks

---

### Post by mickObrian on 2010-04-06
Ubuntu automatically creates swap space when you install it, you can check by going to GParted: System > Administration > GParted. Look for "linux-swap", if you see it in there then you already have swap space, if not you can create it with GParted, shrink the shared partition and then format it with the "linux-swap" file system.

---

### Post by lsk3993 on 2010-04-06
UPDATE: in my newbie impatience I seem to have created two files: 'shared' and 'shared4096Mb.swap'. These are (not surprisingly 4GB each). Is there a chance that either of these are correctly configured and are proper swap files?

---

### Post by lsk3993 on 2010-04-06
> **mickObrian said:**
> Ubuntu automatically creates swap space when you install it, you can check by going to GParted: System > Administration > GParted. Look for "linux-swap", if you see it in there then you already have swap space, if not you can create it with GParted, shrink the shared partition and then format it with the "linux-swap" file system.
Also, no I didn't create a swap file partition during installation as I was told it would be more convenient to have it as a file and that it could be done later.
I also cannot seem to be able to resize the shared partition since it is ntfs, or is there another reason why it can't be resized?

---

### Post by mickObrian on 2010-04-06
> **lsk3993 said:**
> UPDATE: in my newbie impatience I seem to have created two files: 'shared' and 'shared4096Mb.swap'. These are (not surprisingly 4GB each). Is there a chance that either of these are correctly configured and are proper swap files?
Where are you getting this information? I'd recommend using GParted, it's easier to see what you're doing.

---

### Post by lsk3993 on 2010-04-06
> **mickObrian said:**
> Where are you getting this information? I'd recommend using GParted, it's easier to see what you're doing.
Oh sorry, they are in /media

---

### Post by mickObrian on 2010-04-06
If it's set up like I think it is you should just get rid of both current swap spaces by booting up the LiveCD, then go into Windows and extend the NTFS partition over the swap space, then shrink the extended NTFS partition to make room for the swap space, then boot into the Ubuntu LiveCD and turn the unformatted space into swap space.

---

### Post by lsk3993 on 2010-04-06
> **mickObrian said:**
> If it's set up like I think it is you should just get rid of both current swap spaces by booting up the LiveCD, then go into Windows and extend the NTFS partition over the swap space, then shrink the extended NTFS partition to make room for the swap space, then boot into the Ubuntu LiveCD and turn the unformatted space into swap space.
Oh ok, so you wouldn't advise me having a swap file, and I should make a swap partition?

---

### Post by mickObrian on 2010-04-06
Didn't you say you have two swap partitions? How did you manage that when you said you couldn't shrink the NTFS partition? Here's what mine looks like. I also just realized my swap space is way to big.

---

### Post by uRock on 2010-04-06
Did you do a full install or did you use Wubi?

---

### Post by lsk3993 on 2010-04-06
> **mickObrian said:**
> Didn't you say you have two swap partitions? How did you manage that when you said you couldn't shrink the NTFS partition? Here's what mine looks like. I also just realized my swap space is way to big.
Sorry, I think I may have confused you... I've attached screen shots of the /media folder and GParted

---

### Post by lsk3993 on 2010-04-06
> **uRock said:**
> Did you do a full install or did you use Wubi?
I did a full install, I used Wubi before, but I wouldn't trust windows with my Ubuntu install :P

---

### Post by uRock on 2010-04-06
> **lsk3993 said:**
> Sorry, I think I may have confused you... I've attached screen shots of the /media folder and GParted

Ubuntu doesn't use swap files. It has to be in a separate partition. As you know you will not be able to create another partition outside of your Extended partition. You will have to create it within your Extended partition. By first shrinking the 288GB partition by 4GB.

---

### Post by lsk3993 on 2010-04-06
> **uRock said:**
> Ubuntu doesn't use swap files. It has to be in a separate partition. As you know you will not be able to create another partition outside of your Extended partition. You will have to create it within your Extended partition. By first shrinking the 288GB partition by 4GB.
Ok, I guess I read this wrong then: [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)
From what I understood, it says I can make a swap file :confused:
Ok, I'll make a swap partition then, and just delete the two files it left me in /media then?

---

### Post by sisco311 on 2010-04-06
The NTFS partition is mounted under /media/Shared. You have to edit the command accordingly:
```
sudo dd if=/dev/zero of=**/media/Shared/**4096Mb.swap bs=1M count=4096
```

The command is *silent* & it may take some time to complete. Be patient.

and you have to mount the NTFS partition at boot time:
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

& finally add this line to the fstab file:
```
/media/Shared/4096Mb.swap    none    swap    sw    0    0
```

---

### Post by lsk3993 on 2010-04-06
> **sisco311 said:**
> The NTFS partition is mounted under /media/Shared. You have to edit the command accordingly:
```
sudo dd if=/dev/zero of=**/media/Shared/**4096Mb.swap bs=1M count=4096
```The command is *silent* & it may take some time to complete. Be patient.

and you have to mount the NTFS partition at boot time:
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

& finally add this line to the fstab file:
```
/media/Shared/4096Mb.swap    none    swap    sw    0    0
```
Thank you, I wasn't really expecting the silent command- being used to windows and its stupid loading menus and fancy hourglasses :P

Also, what is an fstab file?

---

### Post by uRock on 2010-04-06
> **lsk3993 said:**
> Ok, I guess I read this wrong then: [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)
From what I understood, it says I can make a swap file :confused:
Ok, I'll make a swap partition then, and just delete the two files it left me in /media then?

I stand corrected. I had never heard of people doing that.

It looks like the files was created, so I am guessing you need to do the next command in the line while making the line changes that you made for the system to look in the shared partition.

---

### Post by sisco311 on 2010-04-06
> **lsk3993 said:**
> Thank you, I wasn't really expecting the silent command- being used to windows and its stupid loading menus and fancy hourglasses :P

Also, what is an fstab file?

After the swap file is created you have to format it:
```
sudo mkswap /media/Shared/4096Mb.swap
```

and create an entry for it in the /etc/fstab file. To edit the file run:
```
gksudo gedit /etc/fstab
```
and copy/paste this
```
/media/Shared/4096Mb.swap    none    swap    sw    0    0
```
at the end of the file.

---

### Post by lsk3993 on 2010-04-06
> **sisco311 said:**
> After the swap file is created you have to format it:
```
sudo mkswap /media/Shared/4096Mb.swap
```and create an entry for it in the /etc/fstab file. To edit the file run:
```
gksudo gedit /etc/fstab
```and copy/paste this
```
/media/Shared/4096Mb.swap    none    swap    sw    0    0
```at the end of the file.
Thank you again, I am currently in a LiveCD session trying to find those two incorrectly made swap files that I need to delete but I can't seem to find them as /media appears to be empty.
How do I get to them from the Live CD?

---

### Post by sisco311 on 2010-04-06
You don't need the Live CD to delete the files. Boot your Ubuntu installation use the rm command to delete the files:
```
sudo rm -i /mnt/512Mb.swap
```
and
```
sudo rm -i /media/shared4096Mb.swap
```

Be careful, the rm command is dangerous, make sure that you delete the files you want.

---

### Post by lsk3993 on 2010-04-06
> **sisco311 said:**
> You don't need the Live CD to delete the files. Boot your Ubuntu installation use the rm command to delete the files:
```
sudo rm -i /mnt/512Mb.swap
```and
```
sudo rm -i /media/shared4096Mb.swap
```Be careful, the rm command is dangerous, make sure that you delete the files you want.
The problem is that one of the files I'm trying to delete is called 'shared' (see attached screenshot). In /media, there is a folder called shared (which is the mounted partition). If I do ```
sudo rm -i /media/shared
``` might that delete (or affect) the partition?
I can't even unmount the Shared partition because it gives me an error messgae:
> Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sda6 from /media/SharedThanks again for all the help, don't know what I'd do without these forums :)

---

### Post by sisco311 on 2010-04-06
Linux is case sensitive shared is a file & Shared is a directory. By default, rm doesn't delete directories. So, go ahead & remove that *shared* file.

---

### Post by lsk3993 on 2010-04-06
> **sisco311 said:**
> Linux is case sensitive shared is a file & Shared is a directory. By default, rm doesn't delete directories. So, go ahead & remove that *shared* file.
Ok, done that... thought it would be better to double check before blindly running it.
Thanks so much again, had a few other problems but I fixed them myself and everything seems ok now :D
Thanks everyone!
I wonder if I will ever get the hang of Ubuntu >__<

---


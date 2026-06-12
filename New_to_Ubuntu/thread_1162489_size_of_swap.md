---
title: "size of swap"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by tengteng on 2009-05-17
hello everybody.

I have jaunty dual booting with xp on a 160gig hard drive and xp is in a 10 gig partition while jaunty is in another 9gig partition.  The rest of the drive is for my files in another ntfs partition. 

I was just wondering why my swap is only 470MB. I got 3 gigs of ram installed. why is my swap so small? I read that it should be around 1.5x the size of ram installed.  I installed jaunty using a live cd and chose option 3.  I left around 9 gigs raw for jaunty to install itself.  

Is my swap size too small and if so how do I make it bigger? Also, why did jaunty automatically make the swap only 470MB when it installed itself? Did I missing something when I installed jaunty? I don't know much about computers and am learning as I go along.

Should have studied computer science in college instead of psychology.. hehe.. :)

Thanks in advance!

---

### Post by Didius Falco on 2009-05-17
Hi, and welcome to the Ubuntu forums!

I want to check and see if you have a separate swap partition or a swap file, so if you could open a Terminal shell from **Applications/Accessories/Terminal** and type ```
sudo fdisk -l
``` andcopy/paste the output here, please.

Regards,

Didius

---

### Post by tengteng on 2009-05-17
here it is..:)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e609e60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1385    11124981    7  HPFS/NTFS
/dev/sda2            1386       19457   145163340    f  W95 Ext'd (LBA)
/dev/sda5            1386       18181   134913838+   7  HPFS/NTFS
/dev/sda6           18182       19397     9767488+  83  Linux
/dev/sda7           19398       19457      481918+  82  Linux swap / Solaris

---

### Post by SunnyRabbiera on 2009-05-17
The automatic partition always tries to adjust to the size available, so it might be the reason why your swap is so small.
But how much RAM do you have?
Usually the larger the ram the less you need swap, so if you have say 2GB of RAM swap isnt needed as much.
But it does come in handy, especially with suspend.

---

### Post by tengteng on 2009-05-17
I got 3 gigs of ram.. So is it ok for me to just leave the swap size alone? 

Thanks!

---

### Post by SunnyRabbiera on 2009-05-17
> **tengteng said:**
> I got 3 gigs of ram.. So is it ok for me to just leave the swap size alone? 

Thanks!

3GB is plenty, I would not worry about it unless you use suspend a lot.

---

### Post by Didius Falco on 2009-05-17
Thank you for posting that information. If you only had 9 gigs of free space to install Ubuntu, it would make the swap partition small to leave more room for itself.

Nine Gigs is a pretty small space when you start adding applications and your own data. You might want to consider resizing some partitions, or getting a friend who has more computer experience to do it for you, if you aren't comfortable with doing it yourself.

Lets have a look at how much free space you have in the partitions on your Hard Drive. Open a Terminal again, and type```
 df 
``` and post the output here.

Regards,

Didius

---

### Post by tengteng on 2009-05-17
Ok thanks! I barely use suspend anyways..

I got problems with shutting down and mounting usb drives though.  But I guess its not related to my swap size, is it? 

I'm using an acer travelmate 3270 laptop and sometimes the rig don't turn off after shutdown.. Screen just says ' _[ numbers here] shutting down' and it doesn't off itself.  restart is no problem though.

Re the usb drives, they dont mount.  Its in ntfs and I saw there are lots of problems mounting them.

Not too bugged about these though.. Hopefully I can find solutions to them soon..  Overall I like using ubuntu better than xp.

---

### Post by tengteng on 2009-05-17
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6              9614116   3068880   6056864  34% /
tmpfs                  1547844         0   1547844   0% /lib/init/rw
varrun                 1547844       104   1547740   1% /var/run
varlock                1547844         0   1547844   0% /var/lock
udev                   1547844       156   1547688   1% /dev
tmpfs                  1547844       208   1547636   1% /dev/shm
lrm                    1547844      2392   1545452   1% /lib/modules/2.6.28-11-generic/volatile


As of now ubuntu is using 2.9 gigs in its partition and i guess its fine for now.. Is it?  I have all my files in the separate big partition and use both xp and jaunty to access them. Mostly just spreadsheets, pics and videos.  The partitioning sizes is an old habit I picked up from using windows hehe.. Small drive c for windows and keep all my files in a large drive d. That way if I mess up drive c i can just reinstall the os without losing my personal flies..  This will work with jaunty too, right?

---

### Post by Didius Falco on 2009-05-17
Yes, as long as you are keeping all the big data files in a separate partition, you should be okay. Actually, I do that myself - it's easier to back them up and if a Bad Thing should happen in the o/s and you wind up reinstalling, at least you know all your data is safe.

Enjoy Ubuntu!!

Regards,

Didius

---

### Post by tengteng on 2009-05-17
Thanks guys!

Oh yeah.. my jaunty sometimes randomly freezes for several seconds when I open apps like firefox or pidgin.. Is this normal? Would it happen less if I used xubuntu instead? I think I like the idea of a lightweight no-frills os on a dual core laptop.. :) Tried out a wubi installed xubuntu 9.04 on a celeron 430 desktop with 1 gig ram and it was lively and fast.. :)

Again thanks for all your patience with a newbie.. Even if i'm kinda off topic already. hehe

---

### Post by Didius Falco on 2009-05-17
Xubuntu would be faster than Gnome. It could be because of your video card, though I have an ATI 4870 and sometimes there is a very slight delay before things open up.

 What kind of video card/chip do you have? In a Terminal, type ```
lspci | grep VGA
``` and it will tell you. That's a pipe, not an L or an I, btw...

Regards,

Didius

---

### Post by tengteng on 2009-05-17
Oops.. how do i type a pipe on the terminal? don't know how to..
Anyways my gpu is an nvidia geforce go7300. Saw it on the laptop's manual

Thanks!

---

### Post by tengteng on 2009-05-17
I figured it out already.. :)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

---

### Post by Didius Falco on 2009-05-17
Do you have any of the Desktop Effects enabled? **System/Preferences/Appearance**, **Visual Effects** tab... 

Didius

---

### Post by tengteng on 2009-05-17
No I don't.. desktop effects = none. :)

---


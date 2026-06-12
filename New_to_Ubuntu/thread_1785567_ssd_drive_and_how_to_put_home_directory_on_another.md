---
title: "ssd drive and how to put home directory on another drive"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-06-18
Hi Ubuntu Humans and Aliens:

This query sort of follows from an earlier query I made where I asked about how large an SSD I'd need for the Ubuntu opperating system. See: [http://ubuntuforums.org/showthread.php?t=1776199]("http://ubuntuforums.org/showthread.php?t=1776199") if you are interested.

To summarize that discussion, some responders said to get a second mortgage for my house and buy as large an SSD as possible. Other responders said that I could easily get away with an SSD that as 64GB if I put my home directory on another (mechanical) drive.

I've probably installed the Ubuntu operating system one million times. However, I know how to specify which drive I want the installation on. However, 

[COLOR="Red"]**HOW DO I INSTALL UBUNTU ON THE SSD AND THE HOME DIRECTORY (/home/yours_truely) ON ANOTHER DRIVE??**[/COLOR]

:-k

Many, many thanks for your advice!!!

Best regards,
Phil Smith de Duluthistan, GA

---

### Post by YesWeCan on 2011-06-18
My Ubuntu install consumes less than 6GB without my /home directory. So you can go for a super-small SSD, no problem. 16GB would be plenty.

The way it works is that you would install as normal on the SSD. Then you create a second /home partition on another drive. You then copy the SSD/home contents to the new /home. Then you set up fstab to mount the new /home as /home.

The original /home is still there on your SSD but becomes unused. The new /home is linked to the path /home so it as if the new /home is actually the old /home.

All this can be specified using the Ubuntu Installer. You just have to tell it which partition to mount /home on.

---

### Post by ajgreeny on 2011-06-18
You do not tell us if you already have a separate /home partition, but I suspect not.

If I am right you can see how to do everything with a separate /home at installation in this link:-
[Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome") 

If you do already have a separate /home then just make sure you set it to mount as /home, but do not click the format button, when you install.  It does not matter which of the two (or more) drives your /home is on so far as the OS is concerned, just as long as it is mounted as /home when the system boots.

As for the size of the SSD;  my root partition is 10GB with 10.04 and I have used 4.4GB, so unless there are good reasons for having a 64GB SSD, eg faster read/write, you will be unlikely to use very much of it.

An alternative is to put both root and /home on the SSD and use your conventional spinning disk as a data partition (docs, photos, videos, music etc etc), mounted at boot time using /etc/fstab.  If there is little data of that sort in /home, it will not take a great deal of space; it will just be configurations and so on.

---

### Post by oldfred on 2011-06-18
I prefer ajgreeny's suggestion of a separate /data partition. Then the user configuration files that also are often loaded are on the SSD and only data which may be only loaded sometimes is on the spinning drive.

I do not have SSD yet, but keep all my installs in 20-25GB partitions with /home. And my /home is about 1GB with 3/4 of that .wine which I have not yet moved into my /data. My total / is about 7GB with lots of programs and my /home. 

If only running Linux consider gpt as a slight improvement in partitioning. Arch recommends gpt and only 25% use in SSD partition.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)
[http://disktrim.sourceforge.net/](http://disktrim.sourceforge.net/)
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)

---

### Post by YesWeCan on 2011-06-18
I keep thinking of doing this myself. I have everything on a RAID10. But I must confess the RAID is so fast that I think I just want the SSD to be fashionable. ;)

---

### Post by wolfen69 on 2011-06-18
> **oldfred said:**
> 
[http://disktrim.sourceforge.net/](http://disktrim.sourceforge.net/)


Just an FYI: TRIM is now in all recent kernels. No need for any 3rd party stuff.

---

### Post by Old Jimma on 2011-06-19
Thank you for all of your comments. I really appreciate them. Here is my plan. Please review it to see if I've got the idea correct!

In what follows, please note that I'm making a new computer with ssd primary drive for the operating system and a second mechanical drive for my /home directory.


[COLOR="Green"]**Step 1:**[/COLOR] partition the ssd 'mannually' using psychocats suggestions found at [[COLOR="DarkGreen"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

In this 'manual operation, I'll use approximately 16GB for swap (since I have 8Gb of memory), and leave a small amount of space for the /home directory.

[COLOR="Green"]**Step 2:**[/COLOR] complete the install with this configuration.

[COLOR="Green"]**Step 3.**[/COLOR] Reboot. Then use gparted to reformat the entire mechanical hard drive as one partition, and to ext4 format.

Let's pretend that the mechanical hard drive is /dev/sdb1 

[COLOR="Green"]**Step 4.**[/COLOR] Add the following line to /etc/fstab:

/dev/sdb1    /home   ext4    defaults     0        2

[COLOR="Green"]**Step 5:**[/COLOR] Just for fun, make sure I own everything by opening a terminal window and typing:

sudo chown -R myaccountname:myaccountname /home

[COLOR="Green"]**Step 6:**[/COLOR] Reboot.

[COLOR="Red"]My question is: Is this sequence correct? [/COLOR]

I think that Step 4 may not be quite correct.

Thanks,
Phil Smith
Duluth, GA

---

### Post by cchhrriiss121212 on 2011-06-19
2 points:
16GB is insane for swap, go with 4GB max as it is hardly used on most systems.
You could format the old drive and set it as /home during the install procedure, which will be much easier than setting it up post-install.

---

### Post by YesWeCan on 2011-06-19
You can do all this automatically with the Ubuntu installer. It will take care of everything like fstab entries. Why do it manually?

The swap doesn't need to be so huge. As you have 8gb of ram you probably wont ever use any swap at all. I have a 4GB swap on mine. Its just a sort of ram emergency supply. You only need as much swap as ram if you have a mobile that you want to put into suspend mode to save battery: in this case all the ram content is temporarily copied to swap. Also, I wouldn't put the swap on the SSD it would be an expensive waste. Just put a swap partition on the hard disk somewhere.

---

### Post by pqwoerituytrueiwoq on 2011-06-19
yes 16 gb is plenty or a [FONT=Courier New]/[/FONT] partition and it only cost about [50$]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820139428") for a sata 2 drive (8 gig would be ok just be sure to check the drives speed)
i will suggest putting [FONT=Courier New]/var[/FONT] and [FONT=Courier New]/tmp[/FONT] on the other hdd also
unless you want to put [FONT=Courier New]/tmp[/FONT] on the ram (*tmpfs /tmp tmpfs defaults,noatime,mode=1777*)
swap should definitely go on the old hdd and not on the ssd since we do not want to wear the drive out using it as ram
i also hear you should use noatime and nodiratime on a ssd so and partition on your ssd should have those under [FONT=Courier New]<options>[/FONT] in fstab file

---

### Post by jimbo99 on 2011-12-28
> **Phil Smith said:**
> Thank you for all of your comments. I really appreciate them. Here is my plan. Please review it to see if I've got the idea correct!

In what follows, please note that I'm making a new computer with ssd primary drive for the operating system and a second mechanical drive for my /home directory.


[COLOR="Green"]**Step 1:**[/COLOR] partition the ssd 'mannually' using psychocats suggestions found at [[COLOR="DarkGreen"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

In this 'manual operation, I'll use approximately 16GB for swap (since I have 8Gb of memory), and leave a small amount of space for the /home directory.

[COLOR="Green"]**Step 2:**[/COLOR] complete the install with this configuration.

[COLOR="Green"]**Step 3.**[/COLOR] Reboot. Then use gparted to reformat the entire mechanical hard drive as one partition, and to ext4 format.

Let's pretend that the mechanical hard drive is /dev/sdb1 

[COLOR="Green"]**Step 4.**[/COLOR] Add the following line to /etc/fstab:

/dev/sdb1    /home   ext4    defaults     0        2

[COLOR="Green"]**Step 5:**[/COLOR] Just for fun, make sure I own everything by opening a terminal window and typing:

sudo chown -R myaccountname:myaccountname /home

[COLOR="Green"]**Step 6:**[/COLOR] Reboot.

[COLOR="Red"]My question is: Is this sequence correct? [/COLOR]

I think that Step 4 may not be quite correct.

Thanks,
Phil Smith
Duluth, GA

It is mostly correct, except in one regard.  This forces the contents of your home folder into the root of the second drive.  It does not address putting your home folder into a folder itself, say for the purposes of separating multiple accounts, or other very valid results.  I know this is an old thread, but I thought I'd point that out.

---


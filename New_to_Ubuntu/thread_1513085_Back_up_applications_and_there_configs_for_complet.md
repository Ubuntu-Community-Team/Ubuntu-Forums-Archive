---
title: "Back up applications and there configs for complete clean install"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by joshmuffin on 2010-06-18
Hey all I'm gonna wipe my hdd (including corrupted windows partition :D) and do a complete fresh install the problem is I have configured all my programs perfectly and I don't want to loose the programs or there configuration. What's the best way to go about this? SBackup?

Thanks in advanced, Josh

---

### Post by oldfred on 2010-06-18
You have all your user settings and data in /home, so you want to back that up including the hidden files.

You may have custom system settings in /etc. Did you have to make any system changes, if so back those up. If going to a new version old setting may not be appropriate so just save copies, just in case you need to remember a setting.

You can list all the installed programs.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

I moved /home and then created a /data. I now have three installs of Ubuntu, old, Karmic & Lucid with plans for another for Maverick. With data in a separate partition I only need 15-25GB for each root, maybe less since I have only used 6GB for root & 1GB for /home.

---

### Post by joshmuffin on 2010-06-19
Thanks heaps for the help. I only just got back into Ubuntu and its been forever since I last did this =P

---

### Post by k3lt01 on 2010-06-19
You could get Remastersys and do a complete backup copy of your system. Do you have a separate /home? If you do you can leave it for now while you tidy up th rst of your hdd.

---

### Post by joshmuffin on 2010-06-19
Nar home isn't separate but I'm going to make it with this wipe.

Can either of you possible help me with partitioning?

I'm aiming for :

3 primary-
8G Ubuntu 10.04
8G Ubuntu 10.09
8G Linux Mint

/home 500g

swap 8g

---

### Post by k3lt01 on 2010-06-19
> **joshmuffin said:**
> Nar home isn't separate but I'm going to make it with this wipe.

Can either of you possible help me with partitioning?

I'm aiming for :

3 primary-
8G Ubuntu 10.04
8G Ubuntu 10.09
8G Linux Mint

/home 500g

swap 8gIf you are intent on having 2 Ubuntu installs you should have 2 separate /home directories. So make it look like this

8gb Ubuntu 10.04 /
8gb Ubuntu 10.10 /
8gb Mint /
2gb SWAP
166gb /home for 10.04
166gb /home for 10.10
166gb /home for Mint.

Doing a separate /home for each makes sure each install has its correct settings as they are in the /home partition. If you mix /home among the 3 different installs you can cause problems if they are setup differently and if thy have different program versions.

---

### Post by oldfred on 2010-06-19
If you are doing multiple installs the separate /home is less necessary, but you may want a separate /data which you can share without issue since it is just all your data. I even try to move some things that are normally stored in /home hidden files to data like firefox and thunderbird profiles. I created /Data with all the standard folders then added a few and link the data into each install ( I use a script to make it easy to set up)

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)
[http://ubuntuforums.org/showthread.php?t=1411482](http://ubuntuforums.org/showthread.php?t=1411482)

---

### Post by k3lt01 on 2010-06-19
> **oldfred said:**
> If you are doing multiple installs the separate /home is less necessary, but you may want a separate /data which you can share without issue since it is just all your data.I disagree, I know from personal experience that there can be conflicting settings files if you have a single /home. It caused me a couple of days of work trying to figure it out. A separate /home is a necessity if you are using different systems, keep them small by all means but keep them separate. A common /data is a good idea in this case.

---

### Post by oldfred on 2010-06-19
I totally agree with k3lt01. I was not clear that I meant a separate /home partition is not as necessary with a /Data partition but you still need the standard installs of the /home folder inside each install. You should not share /home between installs. Some say you can if you use different user ids but I think that defeats the purpose.

---

### Post by k3lt01 on 2010-06-19
My apology oldfred, I may have come across a little harsh.

---

### Post by joshmuffin on 2010-06-19
I think I'll do:

100GiB for each of the three primaries, a swap and a 300GiB /data 

how do you properly set the mount points and such

---

### Post by joshmuffin on 2010-06-19
I have:
Sda1 ubuntu 10.04 mounted to "/" -100gib
sda2 which will be ubuntu 10.10 mounted to "/boot" -100gib
sda3 which will be linux mint left as empty space for the moment -100gib
sda4 mounted to "/data" -700gib
and sda5 as swap -4gib

I'm not really sure what should be mounted at "/boot" and what should be mounted at "/".

---

### Post by k3lt01 on 2010-06-19
> **joshmuffin said:**
> I think I'll do:

100GiB for each of the three primaries, a swap and a 300GiB /data 

how do you properly set the mount points and suchYou will have to do 3 separate installs so for your first install, I'll use Ubuntu 10.04 as the example, boot with your LiveCD follow the instructions until you get to the partitioner.

Now your in the partitioner you will need to select "Manual partitioning". This will bring up your disk, you will b doing most of your hard work now.

You will need to delete the partition that is already there and that will make your disk look all the same. Now create a new partition of 100gb for Ubuntu 10.04 when creating this you will need to choose "use this partition" the file format (ext4 is standard now) and what your mount point is (/),once that is done create 2 more 100gb partitions but don't choose "use this partition", don't assign any mount point and don't format, with the second and third 100gb partitions.

Now you should have 3 separate 100gb partitions, one of which is set as / and will be formatted (this will be shown with a tick in the format box).

Now you need to create a SWAP space so follow the same procedure you did with the 100gb partitions except instead of choosing ext4 you choose SWAP.

After you have done that you create another partition of the size you want, 500gb by the above post, select ext4, use this partition and format.

After you have done all this accept the changes, write them to disk and let Ubuntu 10.04 install. Once it has installed boot it and check it works ok. Get your next Install disk ready and reboot.

Now follow the procedure as per above but remember only install on the proper partitions. So Ubuntu 10.10 will go on the 2nd partition and you do not need to format any other partitions at all. However you do need to tell it where the SWAP and /data partitions are. To do this just select the SWAP partition in the partitioner and also the /data partition. It is important that with the /data partition you select "ext4" and "use this partition" give it a mount point "/data" but DO NOT FORMAT IT. What you are doing is keeping it setup as it already is but telling Ubuntu 10.10 that it is there for it to use.

Once Ubuntu 10.10 is installed reboot and test it so you know it works ok. Get your Mint disk, reboot and follow the procedure again remembering that you only format the 3rd 100gb partition but you tell Mint where the SWAP and /data partitions are.

Hope that helps, let us know how you go.

---

### Post by k3lt01 on 2010-06-19
> **joshmuffin said:**
> I have:
Sda1 ubuntu 10.04 mounted to "/" -100gib
sda2 which will be ubuntu 10.10 mounted to "/boot" -100gib
sda3 which will be linux mint left as empty space for the moment -100gib
sda4 mounted to "/data" -700gib
and sda5 as swap -4gib

I'm not really sure what should be mounted at "/boot" and what should be mounted at "/".
/boot is usually within / so I wouldn't give it a different mount point. Just give each version its own / and make sure as shown in my previous post that each one knows where SWAP and /data is.

---

### Post by joshmuffin on 2010-06-19
Beauty, easy to follow step by step instructions thanks heaps man. I'm on the live CD now and I've done all the partitioning I just had to check it was right. Ubuntu 10.04 just installed smoothly thanks, now I can get to work on 10.10 and mint :D

---

### Post by k3lt01 on 2010-06-19
Glad to help. Let us know how you go with the rest of it. I may install 10.10 sometime soon to, I have a partition ready for it.

---

### Post by joshmuffin on 2010-06-20
The 3 installs went really well. Upgrading to 10.10 was a bit messy and I'm still playing around with getting gnome-shell running, but hey that was the point of me installing 10.10.

One thing I'd note for people do a similar kind of this as me:
Each time you install an OS it changes grub  to have it as the only boot option.
(with grub version 2.0)```
sudo update-grub
``` Will scan for partitions and then add them all to grub and such. basically it makes everything work nicely :)

---


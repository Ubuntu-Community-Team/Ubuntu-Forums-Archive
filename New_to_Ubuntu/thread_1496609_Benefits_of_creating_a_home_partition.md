---
title: "Benefits of creating a /home partition"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by lukemk1 on 2010-05-29
Okay guys, so I'm fairly new to linux and I am slowly making the switch from Windows 7 to Ubuntu...

As I'm researching for applications to replace my current window solutions I read about how creating /home on a separate partition/HDD  will allow me to store all my files in that so I don't need to back up due to a reinstall, upgrade, or distro switch. 

My question is, is this worth it? I usually will move all files important to me to separate drives anyways... but if this gives me a benefit to upgrade or even switch distro's as the guide said without losing data then I would consider this option. 

Also, if this is worth it should this be done on just a separate partition or a completely different hard drive?

Idea's and/or helpful thoughts are would be great.

Thanks.

---

### Post by SoFl W on 2010-05-29
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1411215").

---

### Post by antenna on 2010-05-29
Yes it's worth it, you covered the benefits really.  Less hassle for a reinstall/switch distro etc.  Of course you may want to backup anyway in case of installer or user error at install time but it's not strictly necessary with a separate /home (and I don't typically bother).

---

### Post by lukemk1 on 2010-05-29
How theoretically would you install a new distro and tell it to use the /home directory that is already there without it causing any data to be erased?

---

### Post by bodhi.zazen on 2010-05-29
> **lukemk1 said:**
> How theoretically would you install a new distro and tell it to use the /home directory that is already there without it causing any data to be erased?

You have to be very careful the installation does NOT format the /home partition. Most will offer the option to mount the partition at /home without formatting the partition.

Personally I use a data partition (ther are a number of config files in $HOME that I do not need).

The main advantage of a separate home or data partition is the you can re-install the OS without data loss. This holds true of any OS, Linux, BSD, or Windows.

There are 2 potential problems with a shared /home partition:

1. Very rare, one of the config, or dot ( . ) files in your home partition will conflict across distros or versions of applications.

2. A bigger potential problem, usernames. The OS does not understand your user name, you are a number, or uid. The first user in Ubuntu is 1000 , but in Fedora the first user is 500. So if you use the same user name across distros you would need to map all the users in /home to have the same uid.

This is less an issue on single user systems, but is a problem with multiple users.

You can avoid the problem by assigning a unique user name to each user on each distro, but this kind of defeats the point of a separate /home.

Can be an issue with /data , but , almost be definition the information on /data has permissions of 777 or 666 ...

---

### Post by mapes12 on 2010-05-29
If you have installed Ubu then thought "Oh dear, I should have /home on its own partition", then here you go:-

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

### Post by pdlethbridge on 2010-05-29
In addition to the home folder I also have my files backed up in a fat32 partition. Added protection if you mistakenly format the home partition.

---

### Post by daimaru on 2010-05-29
givin what u posted i think there s no benefit in u using a /home on a seperate partition. Basically its the same in windows if you dont save your files in the usual "my documents" etc spaces since they get ereased during reinstall. If you did not do that in windows you don t have to in ubuntu. 

Personally i use a different partition for my /home directory as well as /var/ and /boot but that is a personal preference. It has its benefits and a few security benefits if ur running a server, but given that you  backup your files anyway it will not be necessary for u running a desktop pc.

---

### Post by colin.p on 2010-05-29
For the past couple of updates, 8.10, 9.04 and 9.10, I used a separate home partition. However, when I went to 10.04, and after deciding I no longer needed XP, I told the installer to use the whole drive. I was going to set up a separate home but since I back up to several drives, I said screw it and only have a / and swap.
However, I do a regular backup of my home using Grsync and just copy over whatever I need to the new set up. Had Thunderbird updated to version 3 (from 2 in Karmic) and had all my folders copied over and up and running in minutes. So I really don't see any use (for me at least) for a separate /home partition. YMMV

Colin

---

### Post by BoneKracker on 2010-05-29
The main benefits of creating a separate home partition are:

1.  Preventing denial-of-service caused by a user exhausting disk space available to the operating system.

2.  Enhanced security by applying restrictive mount options to the /home partition (e.g. -o nosuid, nodev, noexec)

3.  Isolating user data within its own filesystem (user data not corrupted by system operations and vice-versa, users cannot build hard links to system files, etc.).

4.  Convenience in managing user data by being able to refer to it at the device or filesystem level (e.g.: the dd utility only works with devices, not directories; the find, locate, and symlinks utilities can be restricted to "same filesystem"; you can unmount the partition and perform operations on it while the system is running, etc.).

In addition to security afforded by filesystem isolation and restrictive mount options, another reason to use a separate partition is to use a specialized filesystem for a group of files that might all be small, large, frequently read or written, needed instantaneously, rarely needed, shared over the network, etc..

There are many schools of thought on partitioning.  A traditional partitioning scheme (more applicable to servers than desktops) would include separate partitions for /boot, swap, /, /tmp, /var, /usr, /home, and possibly /var/tmp, /opt, and /srv.

On my (non-ubuntu) desktop, I have /boot, /, /tmp, /var/tmp, /home, and a partition inside /usr for the directory that holds all the package manager data files (gigabytes of small files, in my weird distro).

I think a separate /home partition is a good idea.  However, if your objective is portability across distros or operating systems, then bodhi.zazen's approach of using a "data" directory is a better approach (you can still mount it inside your home directory, on on say ~/data or ~/documents or whatever).

---

### Post by gabo.cr on 2010-05-29
I never used a /home partition before, but after reading a lot, I decided to do it with Lucid.
I think it is a great idea, and it can save a lot of time when upgrading.

---

### Post by Chipshot on 2010-05-29
> **lukemk1 said:**
> Okay guys, so I'm fairly new to linux and I am slowly making the switch from Windows 7 to Ubuntu...

As I'm researching for applications to replace my current window solutions I read about how creating /home on a separate partition/HDD  will allow me to store all my files in that so I don't need to back up due to a reinstall, upgrade, or distro switch. 

My question is, is this worth it? I usually will move all files important to me to separate drives anyways... but if this gives me a benefit to upgrade or even switch distro's as the guide said without losing data then I would consider this option. 

Also, if this is worth it should this be done on just a separate partition or a completely different hard drive?

Idea's and/or helpful thoughts are would be great.

Thanks.   	 	 	 	 	 	  Lukemk1, My limited experiences as new user to Ubuntu (and there's no lookin' back through the rear Window) was that a home partition was helpful. However, it was easier for me to just buy another drive and mirror it with Clonezilla once a month and then swap drives. In the interim, before the swap, it's easy enough to copy and paste my documents to backup media, TAR evolution and  use the below (gleaned from one of many Ubuntu's sources) to reinstall programs. There is a little cleanup but it is minor (ex: Firefox Boook marks). It may be ham fisted but it's almost zero grief.
 ….
 To replicate your packages selection on another machine (or restore it if re-installing), you can run this 
  
 Code: 
  
 dpkg --get-selections > ~/my-packages 
  
 This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal: 
  
 Code: 
  
 sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade 
  
 It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository. I did this with Jaunty and a lot of packages I installed manually on Hardy were available in the Jaunty repos. So I didn't search for many applications after the fresh install.

---

### Post by pdlethbridge on 2010-05-30
This is how I have mine set up. If I mess up, all I have to do is replace the OS on ext 2 / and if I ever have problems with the OS caused by corrupt files in the home partition, I save my important files to the fat 32 partition and then format the home partition on the fresh OS install
[IMG]http://i768.photobucket.com/albums/xx330/pdleth/computer/Screenshot.png?t=1275192915[/IMG]

---

### Post by frenchn00b on 2010-05-30
Goes for JFS filesystem if it is a big /home
it is more stable than EXT4 , being my own experience 

I had often ext crashes

---

### Post by lukemk1 on 2010-05-30
Okay so if I'm understanding this correctly then this is only an advantage for backing up files but not settings, right?

So if I'm already backing my files up to another drive then there is no real reason to do this correct?

---

### Post by sica07 on 2010-05-31
Almost all your personal(user) settings are stored in the /home folder. So it is an advantage of settings too. An example, if you want to keep your pidgin settings and logs after a fresh Ubuntu reinstall you could do 2 things: 
1)backup your .purple folder or
2) if you have /home as a separate partition, do nothing. A fresh os won't affect your pidgin settings because they are on a different partition

---

### Post by mactece on 2010-05-31
I think you should go with the separate home partition. If you get a boot problem or bad sectors in the root area or want to install a different os then its simpler to fix with a separate home partition. If you need to reinstall, then when it asks how you want the disk arranged select the option to do it by yourself. Then select the first partition and tell it to make it root (/) and reformat. Next select the home partition and tell it to make it home (But don't allow it to reformat). If you want to try out other OSs then create a third partition and again select your data partition to be home when you install them.

---

### Post by lazyart on 2010-05-31
When I upgraded from Karmic to Lucid it was a disaster.  The upgrade process locked up and I had a system that was unbootable.

So, I reinstalled, wiping out the / paritition.  I told the installer to use my existing /home partition, but not to format it.  When Lucid install completed, all my files and settings were waiting for me.  I installed Thunderbird and there were all my emails and contacts.  As I installed other applications I had previously, they all picked up my settings and I just keep rolling.  It only takes a few seconds to set up a separate /home.  It literally saves you hours in getting your settings back.  And of course, had I not had a separate /home I might've lost pictures and files and such (actually, I was able to access them after the crash and back them up externally using a LiveCD, but I ended up not having to restore that backup).

---

### Post by lukemk1 on 2010-05-31
Alright, thanks everyone. After reading all your replies it seems as though I will go with having /home on a separate partition or drive.

---

### Post by BoneKracker on 2010-05-31
Put [SOLVED] in the Title of the original post.

---


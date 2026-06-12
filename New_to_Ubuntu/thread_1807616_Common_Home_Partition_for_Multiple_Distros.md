---
title: "Common Home Partition for Multiple Distros"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by JASONFUSARO on 2011-07-19
I have not found a straight forward answer to the following questions after searching.



Can I copy or move my home directories of each Distro I have installed to a single partition and assigning each their own home subdirectory.

Like /PuppyHome, /UbuntuHome, /ZorinHome etc..

or 

does it have to be simply /home and subdirectories associated with the particular username ie.. /JasonPuppy, /JasonZorin, /JasonUbuntu, etc..

If this is possible do they have to be mounted on boot in in /etc/fstab and /etc/mtab or does they copy or move take care of this upfront?

Does the /usr subdirectory also have to be transfered?

The screenshot shows my current partition setup


Things have been running pretty smooth I have upgraded grub and the linux kernel in a couple of distros, that is where I have been devoting most of my time with learning (kernel upgrades) currently trying out Puppy woof. I am enjoying things a little bit more now.:)

Thanks everyone,

---

### Post by jacksaff on 2011-07-19
It's fine to use the same home partition for multiple distros, but make sure that you do not allow the /home partition to be formatted when installing!! Also, back it up beforehand just in case the installer formats it anyway (shouldn't with modern distros but who knows?). 

What is not advisable is to use the same account (ie. identical username and id) for different distros. The home folder contains a lot of config info and if different versions of programs are writing to the same config files bad things will happen. 

In this case, use different users for each distro and link across folders of data that you want to be common - documents, music, pictures, .wine etc. This stuff should be fine to write to from any account, though you might have to tweak permissions of the original folders to allow you to access them from distros/users other than the original one.

---

### Post by JASONFUSARO on 2011-07-19
> **jacksaff said:**
> It's fine to use the same home partition for multiple distros, but make sure that you do not allow the /home partition to be formatted when installing!! Also, back it up beforehand just in case the installer formats it anyway (shouldn't with modern distros but who knows?). 

What is not advisable is to use the same account (ie. identical username and id) for different distros. The home folder contains a lot of config info and if different versions of programs are writing to the same config files bad things will happen. 

In this case, use different users for each distro and link across folders of data that you want to be common - documents, music, pictures, .wine etc. This stuff should be fine to write to from any account, though you might have to tweak permissions of the original folders to allow you to access them from distros/users other than the original one.



I already have them installed and running, I would like to change how they operate by moving things around, this question does not pertain to fresh installs but to re-arranging what is already installed.


thanks

---

### Post by jacksaff on 2011-07-19
Either way should work, you just need to make sure the correct folder is mounted as /home in fstab.
ie. if one /home then put your user's /username home folder in there and make sure /home is mounted correctly in fstab, or if multiple homes such as /puppyhome /ubuntuhome, then make sure the correct one is mounted and it will need to have the correct user's home folder inside it.

---

### Post by JASONFUSARO on 2011-07-19
> **jacksaff said:**
> Either way should work, you just need to make sure the correct folder is mounted as /home in fstab.
ie. if one /home then put your user's /username home folder in there and make sure /home is mounted correctly in fstab, or if multiple homes such as /puppyhome /ubuntuhome, then make sure the correct one is mounted and it will need to have the correct user's home folder inside it.



Does it matter if I do a move or a copy, ie. move would no longer have it on the current partition and copy would leave a backup on the current partition.


So if I do a move then no changes are recorded within the environment unless I manually do a mount at boot? In other words if I don't mount the home directory at boot then there will be no home at all whether I do a copy or move, no links will be made like a move that takes place in windows where everything takes place automatically?



So if I make partition 15 the /HOME partition and either copy or move each distro's /home directory to it changing each name after the copy or move to the corresponding distro ie. /ZorinHome etc.. then I have to go into each Distros /etc/fstab and add a mount /sda15/Home/WHATEVER_THE_DISTROS_HOME_NAME_IS??


Is this correct?

---

### Post by JASONFUSARO on 2011-07-19
If you look at the screen-shot, is this correct?

---

### Post by JASONFUSARO on 2011-07-19
I just booted into Shakra and I noticed an error message that said Shakrahome is not a directory!!

---

### Post by skatinjj on 2011-07-19
Having to manually edit fstab for each distro makes sense to me logically if you want the correct home directory (or one at all if your moving them around to some place else).

The path /dev/sda15/Shakrahome would not be correct unless Shakrahome is on the root of the drive like /etc/ is.

::EDIT::

i.e

If the folder your mounting was in /home/ then the mount point would be:

/dev/sda15/home/Shakrahome

---

### Post by JASONFUSARO on 2011-07-19
> **skatinjj said:**
> Having to manually edit fstab for each distro makes sense to me logically if you want the correct home directory (or one at all if your moving them around to some place else).

The path /dev/sda15/Shakrahome would not be correct unless Shakrahome is on the root of the drive like /etc/ is.

::EDIT::

i.e

If the folder your mounting was in /home/ then the mount point would be:

/dev/sda15/home/Shakrahome



thanks I was having a boot problem.

I'll make the change

---

### Post by JASONFUSARO on 2011-07-19
/home   ----->    /dev/sda15/Shakrahome    ext3    defaults    0  0




is this correct

---

### Post by skatinjj on 2011-07-19
The line in fstab looks correct except for the directory path.

/dev/sda15/Shakrahome to me indicates that there is a folder on the root of the drive named'Shakrahome' and if that is not true it won't mount.

the 'dir' needs to be where the folder Shakrahome is.

i.e

My home folder is located /home/james

---

### Post by Wim Sturkenboom on 2011-07-19
//Did not read the question properly

---

### Post by JASONFUSARO on 2011-07-19
/home                  /dev/sda15/Chakrahome  ext3  defaults     0 0

          [COLOR="Red"]there are spaces between /home and /dev they are not showing up for some reason?[/COLOR] 


this is giving me an error Chakrahome is not a directory?

am I missing a forward slash or something


Chakrahome is in fact in the root of partition 15



and contains the folder /jason  



what gives??

---

### Post by Jguy on 2011-07-19
your screenshot indicated the folder name is 'Shakrahome'. Was that not the case? It should work...

---

### Post by skatinjj on 2011-07-19
Maybe:


/dev/sdb15 /dev/sda15/Chakrahome  ext3 defaults 0 0

---

### Post by JASONFUSARO on 2011-07-19
```
[jason@Chakra64KDE ~]$ ls
Desktop/  arkkn3842.98-1-x86_64.pkg/  GRUBbooks  grub2_1.99-8_amd64.deb  slack-book.pdf
[jason@Chakra64KDE ~]$ cd /
[jason@Chakra64KDE /]$ ls
$RECYCLE.BIN/  boot/  etc/   lib/    lost+found/  mnt/   root/  sbin/  sys/  usr/  root-image-pkgs.txt
bin/           dev/   home/  lib64/  media/       proc/  run/   srv/   tmp/  var/
[jason@Chakra64KDE /]$ cd home
[jason@Chakra64KDE home]$ ls
jason/
[jason@Chakra64KDE home]$ cd jason
[jason@Chakra64KDE ~]$ ls
Desktop/  arkkn3842.98-1-x86_64.pkg/  GRUBbooks  grub2_1.99-8_amd64.deb  slack-book.pdf
[jason@Chakra64KDE ~]$ cd /media
[jason@Chakra64KDE media]$ ls
DistroHood/
[jason@Chakra64KDE media]$ cd Distrohood
DistroHood
[jason@Chakra64KDE DistroHood]$ ls
Shakrahome/  lost+found/
[jason@Chakra64KDE DistroHood]$ cd Shakrahome
[jason@Chakra64KDE Shakrahome]$ ls
jason/
[jason@Chakra64KDE Shakrahome]$ cd jason
bash: cd: jason: Permission denied
[jason@Chakra64KDE Shakrahome]$ cd /jason
bash: cd: /jason: No such file or directory
[jason@Chakra64KDE Shakrahome]$ cd /
[jason@Chakra64KDE /]$ ls
$RECYCLE.BIN/  boot/  etc/   lib/    lost+found/  mnt/   root/  sbin/  sys/  usr/  root-image-pkgs.txt
bin/           dev/   home/  lib64/  media/       proc/  run/   srv/   tmp/  var/
[jason@Chakra64KDE /]$ cd home
[jason@Chakra64KDE home]$ ls
jason/
[jason@Chakra64KDE home]$ cd jason
[jason@Chakra64KDE ~]$ ls
Desktop/  arkkn3842.98-1-x86_64.pkg/  GRUBbooks  grub2_1.99-8_amd64.deb  slack-book.pdf
[jason@Chakra64KDE ~]$ cd /
[jason@Chakra64KDE /]$ cd /media
[jason@Chakra64KDE media]$ ls
DistroHood/
[jason@Chakra64KDE media]$ cd Distrohood
DistroHood
[jason@Chakra64KDE DistroHood]$ cd Shakrahome
[jason@Chakra64KDE Shakrahome]$ ls
jason/
[jason@Chakra64KDE Shakrahome]$ ls -la
total 12
drwxr-xr-x  3 root root 4096 05.07.2011 07:24 ./
drwxr-xr-x  4 root root 4096 18.07.2011 22:24 ../
drwx------ 15 root root 4096 18.07.2011 05:18 jason/
[jason@Chakra64KDE Shakrahome]$ su -
Password: 
[root@Chakra64KDE ~]# cd jason
-bash: cd: jason: No such file or directory
[root@Chakra64KDE ~]# ls
[root@Chakra64KDE ~]# cd /
[root@Chakra64KDE /]# ls
$RECYCLE.BIN/  boot/  etc/   lib/    lost+found/  mnt/   root/  sbin/  sys/  usr/  root-image-pkgs.txt
bin/           dev/   home/  lib64/  media/       proc/  run/   srv/   tmp/  var/
[root@Chakra64KDE /]# cd media/DistroHood
[root@Chakra64KDE DistroHood]# ls
Shakrahome/  lost+found/
[root@Chakra64KDE DistroHood]# cd Shakrahome
[root@Chakra64KDE Shakrahome]# cd jason
[root@Chakra64KDE jason]# ls
Desktop/  arkkn3842.98-1-x86_64.pkg/  GRUBbooks  grub2_1.99-8_amd64.deb  slack-book.pdf

```

apparently both are pointing to Shakrahome

---

### Post by bodhi.zazen on 2011-07-19
I was going to say, you can use a common home directory for all your distros, but it is best to use a unique user name for each distro.

To migrate you / home , see :

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

And yes you will need to then update fstab on each distro ;)

---

### Post by JASONFUSARO on 2011-07-19
Here is where I stand


I changed the name of the home directory in Chakra to homeYY

Commented fstab line

rebooted


upon booting Chakra

I got 


Logging in jason

Cannot enter home directory Using /


rebooted


Loaded ArchBang

removed # comment from fstab in Chakra



rebooted



Selected Chakra to boot from menu
and got


Cannot enter home directory Using /


so I know this is crap and not working

```
/home                  /dev/sda15/Chakrahome  ext3  defaults     0 0
```


the question is what does it have to be??

---

### Post by bodhi.zazen on 2011-07-19
That fstab line is waaaay off.

```
/dev/sda15  /home/Chakrahome  ext3  defaults     0 0
```

See: [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by JASONFUSARO on 2011-07-19
> **bodhi.zazen said:**
> I was going to say, you can use a common home directory for all your distros, but it is best to use a unique user name for each distro.

To migrate you / home , see :

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

And yes you will need to then update fstab on each distro ;)




Without fully understanding you I was in my ArchBang Distro and followed the instructions from the link and failed to notice the naming convention you stated, I can't seem to get it back now having a stat error


the home folder is there and appears intact as does the old_home in ArchBang


What I was after was 

something like


/DistroHood/ArchBang_Home/jason

/DistroHood/Chakra_Home/jason

/DistroHood/Ubuntu_Home/jason

etc..


but apparently I have 
/DistroHood/home


and need to change my username in each Distro before I execute the commands in the link thereby having

/DistroHood/home/jasonArchBang
/DistroHood/home/jasonChakra
/DistroHood/home/jasonUbuntu


etc..


am I correct in my understanding??



I would have prefered solution #1 but now I have to backtrack to replace my home directory or can I just rename old_home back to home and delete the home directory in DistroHood (<- a take on neighborhood)

??


things were running preeeeetty smooth for awhile I hope I didn't just set myself back amonth or so???

---

### Post by bodhi.zazen on 2011-07-19
Well, I have no idea as to the layout of your partitions as you have not posted the information.

I think you mis-understand mount points.

Say you have a partition, sda2, that you use as your /home partition.

On that partition you have several directories, user_1 user_2 etc ...

in fstab you would use

/dev/sda2 /home auto defaults 0 2

mount /home

ls /home will show user_1 and user_2

"/DistroHood/ArchBang_Home/jason" makes no sense

---

### Post by JASONFUSARO on 2011-07-19
> **bodhi.zazen said:**
> Well, I have no idea as to the layout of your partitions as you have not posted the information.

I think you mis-understand mount points.

Say you have a partition, sda2, that you use as your /home partition.

On that partition you have several directories, user_1 user_2 etc ...

in fstab you would use

/dev/sda2 /home auto defaults 0 2

mount /home

ls /home will show user_1 and user_2

"/DistroHood/ArchBang_Home/jason" makes no sense




I posted as screen-shots


now I can't log into ArchBang and the solution you offered 
```
That fstab line is waaaay off.

Code:
/dev/sda15  /home/Chakrahome  ext3  defaults     0 0
```


gives me the cannot enter home directory using / 


error that I previouly posted??


now is the problem related to the fact that I modified things as root and I need to set permissions back to jason??


might that be the cause of the problems?


like I said things were going pretty smooth for awhile

thanks,

---

### Post by JASONFUSARO on 2011-07-19
If you go back to page 1 of this thread you can clearly see the screenshot I placed there in the opening thread of Gparted showing my partition structure, and I believe I stated what I was trying to achieve clearly, I don't see where you come up with partition 2 holding everything?

---

### Post by JASONFUSARO on 2011-07-19
> **bodhi.zazen said:**
> Well, I have no idea as to the layout of your partitions as you have not posted the information.

I think you mis-understand mount points.

Say you have a partition, sda2, that you use as your /home partition.

On that partition you have several directories, user_1 user_2 etc ...

in fstab you would use

/dev/sda2 /home auto defaults 0 2

mount /home

ls /home will show user_1 and user_2

"/DistroHood/ArchBang_Home/jason" makes no sense




/DistroHood is the label I gave to partition #15

which is the same as /dev/sda15


ArchBang_Home is the subdirectory I wish to store jason in which takes the place of /home on the distros normal partition


there is only one user per distro jason and he is the user on eeach and every distro same name no difference

---

### Post by bodhi.zazen on 2011-07-19
You are making this process more complicated then it is.

In order to share a /home partition, identify a partition (which you have not done in your screen shot), mount it in temporary location, and copy your users home directory to it.

Then update fstab and mount it at /home

It is that simple.

Your problems stem from:

1. Starting this project with insufficient information.
2. using /multiple/sub/directories/for/home/user
3. A lack of understanding mount points.

A users home directory is located at 

/home/user

If you have a /home partition, and you mount it at home, and you ls /home you will see user1 user2 etc.

If you unmount the partition and re-mount it at say /mnt 

When you ls /mnt you will see user1 user2 etc, why is that do you think ?

There is not such thing as mounting 

/dev/sda3/home/some/funky/directory /home/your_user

You would first need to mount /dev/sda3 somewhere, say /mnt

and then mount --bind

mount -o bind /mnt/your/complex/directory/system/user_1 /home/user_1

see man mount for details

Stop, take a deep breath, read the documentation, understand what you are doing and why and all will be well in the world again.

---

### Post by JASONFUSARO on 2011-07-19
> **bodhi.zazen said:**
> You are making this process more complicated then it is.

In order to share a /home partition, identify a partition (which you have not done in your screen shot), mount it in temporary location, and copy your users home directory to it.

Then update fstab and mount it at /home

It is that simple.

Your problems stem from:

1. Starting this project with insufficient information.
2. using /multiple/sub/directories/for/home/user
3. A lack of understanding mount points.

A users home directory is located at 

/home/user

If you have a /home partition, and you mount it at home, and you ls /home you will see user1 user2 etc.

If you unmount the partition and re-mount it at say /mnt 

When you ls /mnt you will see user1 user2 etc, why is that do you think ?

There is not such thing as mounting 

/dev/sda3/home/some/funky/directory /home/your_user

You would first need to mount /dev/sda3 somewhere, say /mnt

and then mount --bind

mount -o bind /mnt/your/complex/directory/system/user_1 /home/user_1

see man mount for details

Stop, take a deep breath, read the documentation, understand what you are doing and why and all will be well in the world again.





I wish to have Partition #15 hold each and every /home folder of every distro 8 distros 8 subdirectories on partition #15, each subdirectory on #15 having the name of the Distro and within each of those subdirectories a user subdirectory /jason same name in each one.


what I need to know is how to best move each directory ie. /home from their current locations to partition #15 and what command has to be placed in fstab in each of those distros in order to connect to them when I run each distro. 


sorry 2 months to your many years I appologize

---

### Post by nothingspecial on 2011-07-19
May I take this off track and offer what I would do? 

Copy each distros /home/$USER to  /home in each distro (but only the config files, not the data, they don't take up much space)

Ensure your uid and gid is the same in each distro.

Use the partition as a seperate data partition, with eg Documents, Videos, Music etc in it.

Link those directories to the /home/$USER of each distro.
```

ln -s /media/data/* ~/
``` (or whatever)

Much easier and simpler than having multiple seperate /homes on one partition.

---

### Post by amjjawad on 2011-07-19
Tried to stay away from this topic but can't really help it.

I had 9 Operating Systems installed on one machine, 8 Linux Distros on one HDD and WinXP on another HDD.

Each Linux Distro had it's OWN /home, period.

ALL the 8 Linux Distros were sharing ONE swap partition.

That's THE BEST way to do it.

The best thing to make it sharable with ALL OS's is an NTFS Data Partition, specially if Windows is installed.


Now, I'm done with "the exploring and learning" part of multiple Distros so I quit Mutli-Booting :)

Good luck with your research!

---

### Post by bodhi.zazen on 2011-07-19
> **JASONFUSARO said:**
> I wish to have Partition #15 hold each and every /home folder of every distro 8 distros 8 subdirectories on partition #15, each subdirectory on #15 having the name of the Distro and within each of those subdirectories a user subdirectory /jason same name in each one.


what I need to know is how to best move each directory ie. /home from their current locations to partition #15 and what command has to be placed in fstab in each of those distros in order to connect to them when I run each distro. 


sorry 2 months to your many years I appologize

But /home does not work that way. On any distro, ls /home what do you get ? A list of user names.

Again, you need to understand what a file system tree means.

If you want to do what you are asking you would make a bunch of directories on sda15

arch/user_name
ubuntu/user_name
fedora/user_mane

whatever.

You then would need to mount sda15 somewhere other then /home , use any location you like, /mnt, /media/home_dir, whatever, does not matter so long as it is NOT /home.

You would then need to use the bind option I already gave you, and it would vary with each distro.

mount -o bind /mnt/arch/user_name /home/user_name

On ubuntu you would use

mount -o bind /mnt/ubuntu/user_name /home/user_name

Your problem is your are not following the proper syntax and you are not understanding the file system tree and you are not using the bind option.

There is no way to directly 

mount /dev/sda15/arch/user_name /home/user_name

So the easiest method by far is to drop the complex/directory/system/you/are/using/for/home/in/dev/sda15 and use

user_names

without sub directories.

If you insist on using /complex/directories/it/is/certainly/possible/but/you/are/not/reading/the/man/page/for/mount --bind

---

### Post by JASONFUSARO on 2011-07-19
> **nothingspecial said:**
> May I take this off track and offer what I would do? 

Copy each distros /home/$USER to  /home in each distro (but only the config files, not the data, they don't take up much space)

Ensure your uid and gid is the same in each distro.

Use the partition as a seperate data partition, with eg Documents, Videos, Music etc in it.

Link those directories to the /home/$USER of each distro.
```

ln -s /media/data/* ~/
``` (or whatever)

Much easier and simpler than having multiple seperate /homes on one partition.



I have partirion #14 as a shared partition.

What I am striving for is a simple way to upgrade the distro at a later point in time if I so choose, but due to the lack of ability to create a seperate /home partition for each distro I need to get them into one location and point each distro to that location so I don't loose my settings, I am not worried about data, my photos, documents etc are on a completely seperate partition.

The max of 16 partitions, of which I exausted my search to no avail has left me without a choice of having created seperate /home partitions if I decide to keep just one distro I would then store the /home on a different partition when installing.

---

### Post by nothingspecial on 2011-07-19
> **JASONFUSARO said:**
> I have partirion #14 as a shared partition.

What I am striving for is a simple way to upgrade the distro at a later point in time if I so choose, but due to the lack of ability to create a seperate /home partition for each distro I need to get them into one location and point each distro to that location so I don't loose my settings, I am not worried about data, my photos, documents etc are on a completely seperate partition.

The max of 16 partitions, of which I exausted my search to no avail has left me without a choice of having created seperate /home partitions if I decide to keep just one distro I would then store the /home on a different partition when installing.

Yes, but as bodhi.zazen keeps saying, you can't do what you want to do.

If you keep your /home in each distros / then it is easy (and takes very little space) to backup your settings. You share the data between them. eg

```
before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/backup/11.04_Backup.tgz /home; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds."; exit 0
```

less than 1gig per home

---

### Post by JASONFUSARO on 2011-07-19
> **bodhi.zazen said:**
> But /home does not work that way. On any distro, ls /home what do you get ? A list of user names.

Again, you need to understand what a file system tree means.

If you want to do what you are asking you would make a bunch of directories on sda15

arch/user_name
ubuntu/user_name
fedora/user_mane

whatever.

You then would need to mount sda15 somewhere other then /home , use any location you like, /mnt, /media/home_dir, whatever, does not matter so long as it is NOT /home.

You would then need to use the bind option I already gave you, and it would vary with each distro.

mount -o bind /mnt/arch/user_name /home/user_name

On ubuntu you would use

mount -o bind /mnt/ubuntu/user_name /home/user_name

Your problem is your are not following the proper syntax and you are not understanding the file system tree and you are not using the bind option.

There is no way to directly 

mount /dev/sda15/arch/user_name /home/user_name

So the easiest method by far is to drop the complex/directory/system/you/are/using/for/home/in/dev/sda15 and use

user_names

without sub directories.

If you insist on using /complex/directories/it/is/certainly/possible/but/you/are/not/reading/the/man/page/for/mount --bind



so if I understand correctly I change my username in each distro prior to miving the home to partition #15 and just access the username that pertains to which distro I am using?

what would the mount command look like in that situation in each distro?

---

### Post by bodhi.zazen on 2011-07-19
> **JASONFUSARO said:**
> so if I understand correctly I change my username in each distro prior to miving the home to partition #15 and just access the username that pertains to which distro I am using?

what would the mount command look like in that situation in each distro?

Yes, use a unique user name for each distro, change user names if you need to.

Then copy the /home/unique_user_name to sda15 (mounted in a temporary location) using the information in the previous links.

The directory structure of sda15 is 

user_name_1
user_name_2
user_name_3
...
user_name_8

Then update fstab and mount /dev/sda15 at /home

reboot - should be working

---

### Post by malspa on 2011-07-19
> **amjjawad said:**
> Tried to stay away from this topic but can't really help it.

I had 9 Operating Systems installed on one machine, 8 Linux Distros on one HDD and WinXP on another HDD.

Each Linux Distro had it's OWN /home, period.

ALL the 8 Linux Distros were sharing ONE swap partition.

That's THE BEST way to do it.

The best thing to make it sharable with ALL OS's is an NTFS Data Partition, specially if Windows is installed.


Now, I'm done with "the exploring and learning" part of multiple Distros so I quit Mutli-Booting :)

Good luck with your research!

Here, 8 Linux distros across two hard drives; each has its own /home; shared swap partition; shared data partitions. 

I keep thinking that I'll cut down on the number of distros, but I'm too interested in following each of those projects, and I want to continue to do so over a number of years.

Nothing I've read so far has made me feel inclined to change things to having each distro share a single /home partition. Maybe I'm missing something; what are the advantages in doing so? My impression is that it involves more work than simply keeping the /home partitions separate.

---

### Post by bodhi.zazen on 2011-07-19
> **malspa said:**
> Nothing I've read so far has made me feel inclined to change things to having each distro share a single /home partition. Maybe I'm missing something; what are the advantages in doing so? My impression is that it involves more work than simply keeping the /home partitions separate.

It is a matter of style. As long as each distro has a unique user name a shared /home partition it technically trivial to maintain.

Then when you want to do backups, simply back up a single /home partition , rather then 8 /home/user directories across 8 distros.

Alternately use a /data partition.

I have already outlined why the OP has made the process seem more complicated then it is, read up if you are so interested, otherwise do not judge from this thread.

---

### Post by amjjawad on 2011-07-19
> **malspa said:**
> what are the advantages in doing so? My impression is that it involves more work than simply keeping the /home partitions separate.

Same here. But also, there is no harm to know/learn the hard way :)

For me, I'm done with Multi-Booting :)

---

### Post by JASONFUSARO on 2011-07-19
> **bodhi.zazen said:**
> It is a matter of style. As long as each distro has a unique user name a shared /home partition it technically trivial to maintain.

Then when you want to do backups, simply back up a single /home partition , rather then 8 /home/user directories across 8 distros.

Alternately use a /data partition.

I have already outlined why the OP has made the process seem more complicated then it is, read up if you are so interested, otherwise do not judge from this thread.


from thread #31 explaining why I am doing or rather trying to do it like so, I don't know if you seen this?

again I appologize for the complication, seems to be my M.O. not purposely mind you.

```
I have partirion #14 as a shared partition.

What I am striving for is a simple way to upgrade the distro at a later point in time if I so choose, but due to the lack of ability to create a seperate /home partition for each distro I need to get them into one location and point each distro to that location so I don't loose my settings, I am not worried about data, my photos, documents etc are on a completely seperate partition.

The max of 16 partitions, of which I exausted my search to no avail has left me without a choice of having created seperate /home partitions if I decide to keep just one distro I would then store the /home on a different partition when installing.
```

---

### Post by JASONFUSARO on 2011-07-19
I changed the user and group permission on the ArchBang /home/jason directory of which it was root I used dolphin as root to move things around I think that is the cause of the problem I am rebooting

---

### Post by nothingspecial on 2011-07-19
Just backed up my home, less than one minute, total size 151M, that includes some big debs, my trash and .cache

---

### Post by JASONFUSARO on 2011-07-19
> **nothingspecial said:**
> Just backed up my home, less than one minute, total size 151M, that includes some big debs, my trash and .cache

How many distros?

---

### Post by nothingspecial on 2011-07-19
> **JASONFUSARO said:**
> How many distros?

Does not matter. You set it to do automatically. While you sleep. (but I suppose, less than 8 minutes for all of them in your case)

If you are interested in the way I do it then post back saying so.

If not post back saying no thanks and I will bow out.

I don't mind either way :)

---

### Post by JASONFUSARO on 2011-07-19
> **JASONFUSARO said:**
> I changed the user and group permission on the ArchBang /home/jason directory of which it was root I used dolphin as root to move things around I think that is the cause of the problem I am rebooting



That was the problem, I am back in ArchBang


Maybe I should just leave well enough alone, and leave things as they are!?

WORKING



But that would leave the upgrade problem, how to do it and not lose any modifications to the distro settings, is their any easy solution that does not entail mounting and moving and such, just a simple copy somewhere do the upgrade and then copy back????

---

### Post by nothingspecial on 2011-07-19
> **JASONFUSARO said:**
> That was the problem, I am back in ArchBang


Maybe I should just leave well enough alone, and leave things as they are!?

WORKING



But that would leave the upgrade problem, how to do it and not lose any modifications to the distro settings, is their any easy solution that does not entail mounting and moving and such, just a simple copy somewhere do the upgrade and then copy back????

:-\"

---

### Post by JASONFUSARO on 2011-07-19
sure if it's simple and you can explain each move.

---

### Post by JASONFUSARO on 2011-07-19
> **nothingspecial said:**
> Does not matter. You set it to do automatically. While you sleep. (but I suppose, less than 8 minutes for all of them in your case)

If you are interested in the way I do it then post back saying so.

If not post back saying no thanks and I will bow out.

I don't mind either way :)

sure if it's simple and you can explain each move.

---

### Post by JASONFUSARO on 2011-07-19
stepping away temporarily

---

### Post by malspa on 2011-07-19
> **bodhi.zazen said:**
> It is a matter of style. As long as each distro has a unique user name a shared /home partition it technically trivial to maintain.

I see.

> **bodhi.zazen said:**
> Then when you want to do backups, simply back up a single /home partition , rather then 8 /home/user directories across 8 distros.

Alternately use a /data partition.

Yeah, my approach of using and backing up a separate data partition seems easy enough.

> **bodhi.zazen said:**
> I have already outlined why the OP has made the process seem more complicated then it is, read up if you are so interested, otherwise do not judge from this thread.

Right. This subject comes up a lot, and I see that the OP is struggling with it a bit, so I'm not judging by this thread at all.

Looks like there are advantages and disadvantages; one approach is as good as the other, I guess. Thanks for the reply.

---

### Post by nothingspecial on 2011-07-19
You have many distros.

I don't know what every ones default uid and gid are. You can find out by typing ```
id
```

To make this easy, you have to have the same one across all distros.

You make an ext4 partitition labled "data"

In each distro you do ```
sudo mkdir -p /media/data
``` (or without sudo if root is enabled and sudo not configured).

Put your data (Documents, Music etc) in there.

In each fstab you put

```
LABEL=data     /media/data      ext4     defaults          0        0
```

Then you link all the stuff in your data partition to each home

```
ln -s /media/data/* ~/
```

Then you set a cron job to backup your /home
```

sudo tar --same-owner -cpvzf /media/backup/11.04_Backup.tgz /home
``` 

(that assumes you have an external drive mounted /media/backup but you could use whatever. Also, give each distros home a different name)

When you upgrade you simply extract the backed up home.

---

### Post by JASONFUSARO on 2011-07-19
Just so I am understood as to what I am trying to accomplish I will restate


I could not create a seperate home partition for each Distro because of the 16 limit on partitions, and I wanted to try a few different ones.

I would not be attempting this movement of the home directories if there was not a problem with doing an upgrade. 

Any photo, documents, music etc. I share off of another  partition, it is mainly the software downloads and settings for each distro I am concerned about if I decide to do an upgrade. Which I may or may not, probably may just for the learning experience.

If I could just copy the home somewhere temporary and do the distro upgrade then copy the home directory back none of this would be required, but since as I have read and learned this is not the case, therefore I am trying to find the simplest solution to the problem. A single distro and seperate home would solve it but that is not where I am at.

Secondly the reasoning behind having multiple distros and a Boot partition like I have makes it a little easier to fix problems that may arise in a distro, I can still get in somewhere and not have to resort to a CD boot or USB boot.

---

### Post by JASONFUSARO on 2011-07-19
> **nothingspecial said:**
> You have many distros.

I don't know what every ones default uid and gid are. You can find out by typing ```
id
```

To make this easy, you have to have the same one across all distros.

You make an ext4 partitition labled "data"

In each distro you do ```
sudo mkdir -p /media/data
``` (or without sudo if root is enabled and sudo not configured).

Put your data (Documents, Music etc) in there.

In each fstab you put

```
LABEL=data     /media/data      ext4     defaults          0        0
```

Then you link all the stuff in your data partition to each home

```
ln -s /media/data/* ~/
```

Then you set a cron job to backup your /home
```

sudo tar --same-owner -cpvzf /media/backup/11.04_Backup.tgz /home
``` 

(that assumes you have an external drive mounted /media/backup but you could use whatever. Also, give each distros home a different name)

When you upgrade you simply extract the backed up home.





when you extract the extraction simply overwrites or does it merge with the home? And are all the settings intact or do you have to tweak and tinker with things??

---

### Post by nothingspecial on 2011-07-19
> **JASONFUSARO said:**
> Just so I am understood as to what I am trying to accomplish I will restate


I could not create a seperate home partition for each Distro because of the 16 limit on partitions, and I wanted to try a few different ones.

I would not be attempting this movement of the home directories if there was not a problem with doing an upgrade. 

Any photo, documents, music etc. I share off of another  partition, it is mainly the software downloads and settings for each distro I am concerned about if I decide to do an upgrade. Which I may or may not, probably may just for the learning experience.

If I could just copy the home somewhere temporary and do the distro upgrade then copy the home directory back none of this would be required, but since as I have read and learned this is not the case, therefore I am trying to find the simplest solution to the problem. A single distro and seperate home would solve it but that is not where I am at.

Secondly the reasoning behind having multiple distros and a Boot partition like I have makes it a little easier to fix problems that may arise in a distro, I can still get in somewhere and not have to resort to a CD boot or USB boot.This would do it ...... 3rd time I'm posting this ....
```

sudo tar --same-owner -cpvzf /media/backup/11.04_Backup.tgz /home
```

That will copy your /home (assuming you've listened to what bodhi is saying and have /home mounted correctly)

I'm leaving this now. Good luck :D

---

### Post by malspa on 2011-07-19
> **JASONFUSARO said:**
> I could not create a seperate home partition for each Distro because of the 16 limit on partitions, and I wanted to try a few different ones.

Gotcha. Yeah, using a common /home partition seems like a nice way of keeping the total number of partitions down. Myself, I kinda stick with these same distros for quite awhile, for the most part. Not really trying out lots of new distros; or when I do, it's usually via a live session, and if I really like what I see, or if I'm interested enough, then I'll think about replacing one of the existing distros with the new one.

In your case, have you ever considered doing virtual installations? Not my cup of tea, but a lot of people prefer going that route.

---

### Post by bodhi.zazen on 2011-07-19
> **malspa said:**
> Looks like there are advantages and disadvantages; one approach is as good as the other, I guess. Thanks for the reply.

As with all things Linux, there is often more then one potential solution. personally I use a data partition and back up only a (small) handful of configuration files.

It is more important to understand the underlying process. The reason you see the question come up is that users are often advised to use a separate /home partition, but the details of doing so are not explained, and it can get a little complex.

For some time sharing a single home directory across 8 distros is likely to be more and more problematic as you will likely have configuration problems with gnome (gnome 2 vs gnome3 vs Unity). Less problems with other DE/WM.

---

### Post by amjjawad on 2011-07-19
> **JASONFUSARO said:**
> I am trying to find the simplest solution to the problem. 

If I were you, I would do this:

sda1 = Windows (if any) 
sda2 = root for Distro1
sda3 = root for distro2
sda5 = root for Distro3
sda6 = root for Distro4
sda7 = root for Distro5
sda8 = root for Distro6
sda9 = root for Distro7
sda10 = root for Distro8
sda11 = SWAP for Distro1 - Distro8
sda12 = NTFS Data Partition

There will be NO separate /home for each.

OR

You could have ONE /home for your main Distro. That's how I had done it before.

I'm sorry about my previous post, I made ONE separate /home ONLY for my main Distro.
 
> 
Secondly the reasoning behind having multiple distros and a** Boot partition** like I have makes it a little easier to fix problems that may arise in a distro, I can still get in somewhere and not have to resort to a CD boot or USB boot.

This is OLD.
Now, with GRUB2, life became much easier.

1) Install Disto1's boot loader to the MBR of your HDD.

2) Install Distro2 - Distr8 Boot Loaders to the same partition where each Distro is installed.

3) Reboot

4) Login to your main Distro and run this command from Terminal:

```
sudo update-grub

```

and THAT IS ALL :)

You're making it much complicated with /boot and common /home for all your distros.

Good Luck!

---

### Post by JASONFUSARO on 2011-07-19
> **amjjawad said:**
> If I were you, I would do this:

sda1 = Windows (if any) 
sda2 = root for Distro1
sda3 = root for distro2
sda5 = root for Distro3
sda6 = root for Distro4
sda7 = root for Distro5
sda8 = root for Distro6
sda9 = root for Distro7
sda10 = root for Distro8
sda11 = SWAP for Distro1 - Distro8
sda12 = NTFS Data Partition

There will be NO separate /home for each.

OR

You could have ONE /home for your main Distro. That's how I had done it before.

I'm sorry about my previous post, I made ONE separate /home ONLY for my main Distro.
 


This is OLD.
Now, with GRUB2, life became much easier.

1) Install Disto1's boot loader to the MBR of your HDD.

2) Install Distro2 - Distr8 Boot Loaders to the same partition where each Distro is installed.

3) Reboot

4) Login to your main Distro and run this command from Terminal:

```
sudo update-grub

```

and THAT IS ALL :)

You're making it much complicated with /boot and common /home for all your distros.

Good Luck!



Thanks but my structure and setup is working fine, I boot of sda2- GRUBBOOT and don't need to worry on whether or not a distro will or won't miss another distro, I just modify grub.cfg on GRUBBOOT. Everything is working fine I am having no problems booting into any distro nor windows vista. If I decided I was never going to do a distro upgrade there would be no use for this thread!


That is where the problem lies, if I decide to do a distro upgrade and how it might be handled the easiest. If I don't then there will never be a problem.

---

### Post by JASONFUSARO on 2011-07-19
How I stand


I performed the instructions as per the link in thread #20 for ArchBang but that did not work because you cannot perform a bind command in fstab that has to take place externally.

So I copied the jason directory in the home directory using dolphin and pasted it in partition #15 which I call DistroHood using the Label and just pasted. In terminal I chmod, chgrp, and chown the directory because dolphin was started from a terminal in as root and it had root permissions I changed them all back to jason. 

This line was added to fstab

[CODE/dev/sda15               /home    ext3      defaults     0 0][/CODE]


I then created a user in Toorox jasonTRX and simply copied the directory using thunar to DistroHood and changed the permissions again and added this line to fstab

```
/dev/sda15               /home    ext3      defaults     0 0
```I am currently in Toorox which booted fine and to make sure I am actually using sda15 I renamed home to homeYY in both distros.

What I can't figure out though is why when the user name is changed it does not automatically change everything in the corresponding directory, do you need to do a grep and change all occurences of jason to jason(xx) whatever the distro name will be??

It worked ok for the first distro I just simply moved everything but now unless I figure out how to make the corresponding name change so it coincides within the directory I will lose all settings and modifications in the distro by having to create another directory along with a different name.

Whereas if I could simply move the whole directory, ie. that is what I initially set out to accomplish.


If dev/sda15 could simply be /dev/sda15/Toorox it would solve this issue, why it can only be /dev/sda15 has me a bit confused.



If dev/sda15 is an actual device then a directory created on dev/sda15 is an actual directory, so why can't the mount occur on it ie. dev/sda15/DistroHood as it does on dev/sda15 ????

this is my structure


sda1 = Windows Vista
sda2 = GRUBBOOT
sda3 = SWAP
sda4 = EXTENDED
sda5 = root for Chakra
sda6 = root for UbuntuStudio64
sda7 = root for CtkArch
sda8 = root for ArchBang
sda9 = root for UltimateEdition
sda10 = root for TooroxGnome
sda11 = root for Puppy
sda12 = root for Zorin
sda13 = Free Partition
sda14 = SHARED partition
sda15 = DistroHome
                   containing   so far    /jason (ArchBang)
                                                 /jasonTRX (Toorox)                                               
/jasonCtkArch


The following is grub.cfg on BOOTGRUB a dedicated GRUB partition

```

if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

set menu_color_normal=black/white
set menu_color_highlight=white/red

insmod part_msdos
insmod ext2
set gfxmode=640x480
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root ee7be487-f281-4072-9af3-72612c9a684c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  #set root='(hd0,msdos10)'
  search --no-floppy --fs-uuid --set=root /dev/sda2
  #search --no-floppy --fs-uuid --set=root /dev/sda10
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_input console
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 1337-6DBF
load_video
##############insmod jpeg
terminal gfxterm
insmod png
background_image -m /boot/grub/1110.png
set timeout=95
### END /etc/grub.d/00_header ###



### BEGIN /etc/grub.d/42_NEW_Chakra_Distros ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root C65A6C105A6C0013
    chainloader +1
}
menuentry "-"  {
set
}

menuentry "Chakra Linux, with Linux vmlinuz26 Fallback (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    #search --no-floppy --fs-uuid --set=root ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6
    linux /boot/vmlinuz26 root=/dev/sda5 ro quiet
#/dev/disk/by-uuid/ca7b9adc-9887-496c-a1ad-a3a5ec4f3cf6 ro quiet
    initrd /boot/kernel26.img
}
menuentry "-"  {
set
}

menuentry 'UbuntuStudio 64 bit on sda6, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    #search --no-floppy --fs-uuid --set=root c7e7c5c2-09fe-4db4-8633-554f90059f45
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sda6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}

menuentry "CtkArch Linux (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 0920168c-5419-4412-8134-713ed2c3814c
    #linux /boot/vmlinuz26 root=/dev/disk/by-uuid/0920168c-5419-4412-8134-713ed2c3814c ro quiet resume=/dev/disk/by-uuid/759ac79d-c3af-49f4-ae9a-19a2e3464a02
    linux /boot/vmlinuz26 root=/dev/sda7 ro quiet resume=/dev/disk/by-uuid/759ac79d-c3af-49f4-ae9a-19a2e3464a02
    initrd /boot/kernel26.img
}

menuentry "ArchBang Linux, with Linux vmlinuz26" --class archlinux --class gnu-linux --class gnu --class os {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root /dev/sda8            #ee7be487-f281-4072-9af3-72612c9a684c
    echo    'Loading ArchBang Linux kernel vmlinuz26 ...'
    linux    /boot/vmlinuz26-patched root=/dev/sda8 ro  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/kernel26-patched.img
}
menuentry "Ultimate, with Linux 2.6.35-25-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    #search --no-floppy --fs-uuid --set=root /dev/sda9               #52777f50-fd1d-42d8-9a17-5ad1ddf0b794
    #linux /boot/vmlinuz-2.6.35-25-generic root=UUID=52777f50-fd1d-42d8-9a17-5ad1ddf0b794 ro quiet splash
    linux /boot/vmlinuz-2.6.35-30-generic root=/dev/sda9 ro quiet splash    
    initrd /boot/initrd.img-2.6.35-30-generic
}

menuentry "Toorox Gnome 64 bit (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    #search --no-floppy --fs-uuid --set=root /dev/sda10      #91033a5b-7407-4a80-b1aa-07ff96202ee3
    linux /boot/vmlinuz root=/dev/sda10 nomce noapic lang=us
}
menuentry "Puppy, with Linux  (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    'insmod part_msdos
    'insmod ext2
    set root='(hd0,msdos11)'
    #search --no-floppy --fs-uuid --set=root /dev/sda11        #856f3983-f4e9-45da-b500-e199fefbbad1
    linux /boot/vmlinuz root=/dev/sda11 pmedia=atahd
    
}
menuentry "Zorin, (Software design Pkgs) with Linux (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    #search --no-floppy --fs-uuid --set=root /dev/sda12               #06ca0e47-d483-4dbe-bfe8-4656dc6cd0eb
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sda12 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}

### END /etc/grub.d/42_NEW_Distros ###

```

---

### Post by JASONFUSARO on 2011-07-19
> **malspa said:**
> Gotcha. Yeah, using a common /home partition seems like a nice way of keeping the total number of partitions down. Myself, I kinda stick with these same distros for quite awhile, for the most part. Not really trying out lots of new distros; or when I do, it's usually via a live session, and if I really like what I see, or if I'm interested enough, then I'll think about replacing one of the existing distros with the new one.

In your case, have you ever considered doing virtual installations? Not my cup of tea, but a lot of people prefer going that route.



Yes I have VirtualBox set up in windows vista and I had in UbuntuStudio but once I got the multiboot going it does not make much sense unless your going to do something that might screw things up. I have the fastest booting mainly Arch Toorox and also have them on USB, like I stated in a previous post it makes it real easy to make changes quickly if you have a couple of quick loading distros installed, with the GRUBBOOT partition I don't have to worry about a distro crapping out and it stopping me from booting into another distro or having to wait for a long load time using LiveCD, ArchBang comes up and allows root access as does Toorox with Thunar and things get real quick, they boot in under a minute so making a change rebooting and logging back in in less than 2 minutes. As opposed to a LiveCD wich could take upwards of 8 minutes or more.


It has been working out real well the way I have it set up right now. It is just the problem of losing settings and software downloads is you do an upgrade that has me confused right now, which is the reason for this thread.

I am not concerned with data storage I have a 500 GiB , a 320 Gib and a 120 GiB external and I store photos and stuff on the shared partition.  It would also simplify things if when you downloaded a package you could download it to a directory like in windows ProgramFiles and each distro could have access to it without having to re-download each time in each seperate distro, there must be a way to standardize it somehow and I am surprised that Linux being around as long as it has some wizard hasn't worked that problem out yet. Why I have to download thunar or dolphin or knapshot each time I install a distro strikes me as odd at time consuming, if it were stored on my hard drive then any distro should have the option of doing a search for an existing package and linking up, just like update-grub does a search for installed kernels and adds them to grub.cfg.

---

### Post by JASONFUSARO on 2011-07-19
As regards post #26 page 3  I have only been at this for a month not 2 months, as I seen from my first post 4 weeks ago. I have been at this 24/7 trying to get a multiboot going and have accomplished that, irregardless of the fact of old google searches with outdated info and sidelined help at times. But it is rather difficult and time consuming tracking down usable info to accomplish a task when that data may be outdated or it may not apply to your particular version and until you become aware of these things it tends to make the process that much more difficult.

Linux is a not to easy system to get going but as you aquire more and more experience yoou realize how powerfull it is and using that power efficiently may take years, so I appreciate the experienced help and assistance and appologize that I don't sit and just polish off the manuals I download before setting out to solve some problem and bug you guys, so thanks again.

---

### Post by bodhi.zazen on 2011-07-20
> **JASONFUSARO said:**
> I performed the instructions as per the link in thread #20 for ArchBang but that did not work because you cannot perform a bind command in fstab that has to take place externally.

One problem you have, you either need to ask or need to read up on these things.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

```
/dev/sda15 /mnt auto defaults 0 2
/mnt/your/complex/path/to/home/user /home/user none bind 0 0
```

---

### Post by malspa on 2011-07-20
> **JASONFUSARO said:**
> It would also simplify things if when you downloaded a package you could download it to a directory like in windows ProgramFiles and each distro could have access to it without having to re-download each time in each seperate distro, there must be a way to standardize it somehow and I am surprised that Linux being around as long as it has some wizard hasn't worked that problem out yet. Why I have to download thunar or dolphin or knapshot each time I install a distro strikes me as odd at time consuming, if it were stored on my hard drive then any distro should have the option of doing a search for an existing package and linking up, just like update-grub does a search for installed kernels and adds them to grub.cfg.

Yes, that would simplify things, but in reality, it doesn't work like that. Different distros have in their repos different versions of apps like Thunar, Dolphin, and KSnapshot. The config files won't be the same. As far as I know, running an app from one distro inside another distro doesn't happen. Someone can correct me if I'm wrong about that, though.

---

### Post by JASONFUSARO on 2011-07-20
Thank you

---

### Post by JASONFUSARO on 2011-07-20
> **bodhi.zazen said:**
> One problem you have, you either need to ask or need to read up on these things.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

```
/dev/sda15 /mnt auto defaults 0 2
/mnt/your/complex/path/to/home/user /home/user none bind 0 0
```






Thank you

---

### Post by JASONFUSARO on 2011-07-20
> **malspa said:**
> Yes, that would simplify things, but in reality, it doesn't work like that. Different distros have in their repos different versions of apps like Thunar, Dolphin, and KSnapshot. The config files won't be the same. As far as I know, running an app from one distro inside another distro doesn't happen. Someone can correct me if I'm wrong about that, though.



what, if any, documentation covering config files have you come across or are aware of, that would save me an exaustive search?

---

### Post by JASONFUSARO on 2011-07-20
> **bodhi.zazen said:**
> One problem you have, you either need to ask or need to read up on these things.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

```
/dev/sda15 /mnt auto defaults 0 2
/mnt/your/complex/path/to/home/user /home/user none bind 0 0
```




With regards to page 6 post #56


/dev/sda15               /home    ext3      defaults     0 0 
Since this is working, what if any, problems may or may not arise from using a scheme such as this?



What appears to you to be a complex path is my using the label of partition #15 ie.

DistroHood is just the Label of /dev/sda15 they are if I am correct interchangeable they refer to one and the same thing, that is to say

/dev/sda15 is one and the same thing identically with /DistroHood it being only a Label assigned to this partition.

Which in relation to your example would become if I did not use my Label

/mnt/your/complex/path/to/home/user /home/user none bind 0 0     

to

/mnt/sda/dev15  /home/user  none bind 0 0    

or rather depending on your inclusion of the /mnt at the beginning


sda/dev15  /home/user

which in fact is what I have less user    none   and bind  from my example

```
/dev/sda15                  /home    ext3      defaults     0 0
```
and this IS working

---

### Post by JASONFUSARO on 2011-07-20
Off topic question


The newest post I have put up regarding the usermod command oddly seems to have no responses. 

I have searched for information regarding that command including manpages and it lacks in examples anywhere which appears to an often not used command, the synopsis offers little help acking in examples of its usage.

I tested it and ended up with an infinite regress of boot directories.




What I need is when I change a username: from jason to jasonTRX the corresponding home/jason changes along with it becoming home/jasonTRX while leaving the original home/jason intact as a backup.


Then I can copy jasonTRX to partition #15 (the location of Distro user directories).



Thank you

---

### Post by JASONFUSARO on 2011-07-20
> **JASONFUSARO said:**
> With regards to page 6 post #56


/dev/sda15               /home    ext3      defaults     0 0 
Since this is working, what if any, problems may or may not arise from using a scheme such as this?



What appears to you to be a complex path is my using the label of partition #15 ie.

DistroHood is just the Label of /dev/sda15 they are if I am correct interchangeable they refer to one and the same thing, that is to say

/dev/sda15 is one and the same thing identically with /DistroHood it being only a Label assigned to this partition.

Which in relation to your example would become if I did not use my Label

/mnt/your/complex/path/to/home/user /home/user none bind 0 0     

to

/mnt/sda/dev15  /home/user  none bind 0 0    

or rather depending on your inclusion of the /mnt at the beginning


sda/dev15  /home/user

which in fact is what I have less user    none   and bind  from my example

```
/dev/sda15                  /home    ext3      defaults     0 0
```and this IS working


Now after reviewing your link

```

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
```

I fail to see anywhere an explanation of why it is used

/mnt/sda/dev15  /home/user  none[COLOR=Red] bind [/COLOR]0 0    


and further searching by google

linux bind option explained

comes up short on why it is needed or for that matter used or how to use it nor its necessity of being included, as I stated previously most searches come up short on clearcut examples of command usage, a synopsis to a new user pretty much says nothing without some definite examples of how the command should or might be used. Running into this problem consistently. 

```

[LIST]
[*]sync/async - All I/O to the file system should be done (a)synchronously.
[*]auto - The filesystem can be mounted automatically (at bootup, or  when mount is passed the -a option). This is really unnecessary as this  is the default action of mount -a anyway.
[*]noauto - The filesystem will NOT be automatically mounted at  startup, or when mount passed -a. You must explicitly mount the  filesystem.
[*]dev/nodev - Interpret/Do not interpret character or block special devices on the file system.
[*]exec / noexec - Permit/Prevent the execution of binaries from the filesystem.
[*]suid/nosuid - Permit/Block the operation of suid, and sgid bits.
[*]ro - Mount read-only.
[*]rw - Mount read-write.
[*]user - Permit any user to mount the filesystem. This automatically implies noexec, nosuid,nodev unless overridden.
[*]nouser - Only permit root to mount the filesystem. This is also a default setting.
[*]defaults - Use default settings. Equivalent to rw, suid, dev, exec, auto, nouser, async.
[*]_netdev - Used for network shares (nfs, samba, sshfs, etc), mounting  the network share is delayed until after the boot process brings up the  network (otherwise the mount will fail as the network is not up).
[/LIST]

```



Which I think relates to the following comment.

>   					Originally Posted by **bodhi.zazen** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11066211#post11066211") 				
  				One problem you have, you either need to ask or need to read up on these things.

---

### Post by bodhi.zazen on 2011-07-20
bind is an option for mount.

If you read the fstab page you understand the format of fstab, which is used as a configuration file form mounting partitions (file systems).

device mount_point file_system **[color=darkred]options**[/color] ...

For a full listing of options see man mount

[http://manpages.ubuntu.com/manpages/oneiric/man8/mount.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/mount.8.html)

The details of the bind option is covered there.

[see also](http://lmgtfy.com/?q=how+to+fstab+bind+option)

---

### Post by JASONFUSARO on 2011-07-20
> **malspa said:**
> Yes, that would simplify things, but in reality, it doesn't work like that. Different distros have in their repos different versions of apps like Thunar, Dolphin, and KSnapshot. The config files won't be the same. As far as I know, running an app from one distro inside another distro doesn't happen. Someone can correct me if I'm wrong about that, though.



What I mean is when a package is downloaded it would not be installed dirctly into that particular distro but elsewhere and some sort of link set up wheras if it is called by Distro A its configuration is made availabe to Distro A, and susequently when it is selected by another Distro for installation what would normally be called or downloaded would in fact not be except for what is necessary to the requesting Distro and if differences exist with regards to configuration then that is stored and usable only when Distro B calls it. The uderlying software does not change according to its being run just it's configuration in relation to the particular Distro and that it seems is what is needed by each Distro to be saved for that Distro accordingly.

---

### Post by JASONFUSARO on 2011-07-20
> **malspa said:**
> Yes, that would simplify things, but in reality, it doesn't work like that. Different distros have in their repos different versions of apps like Thunar, Dolphin, and KSnapshot. The config files won't be the same. As far as I know, running an app from one distro inside another distro doesn't happen. Someone can correct me if I'm wrong about that, though.

> **bodhi.zazen said:**
> bind is an option for mount.

If you read the fstab page you understand the format of fstab, which is used as a configuration file form mounting partitions (file systems).

device mount_point file_system **[COLOR=darkred]options[/COLOR]** ...

For a full listing of options see man mount

[http://manpages.ubuntu.com/manpages/oneiric/man8/mount.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/mount.8.html)

The details of the bind option is covered there.

[see also]("http://lmgtfy.com/?q=how+to+fstab+bind+option")


I am looking at it now, thank you


I have a tendency to go back and modify and edit prior posts, is this a good habit or bad, I am thinking maybe bad for current correspondence and possibly good for someone who starts reading a thread fresh, what is your opinion?

---

### Post by JASONFUSARO on 2011-07-20
> **JASONFUSARO said:**
> I am looking at it now, thank you


I have a tendency to go back and modify and edit prior posts, is this a good habit or bad, I am thinking maybe bad for current correspondence and possibly good for someone who starts reading a thread fresh, what is your opinion?




From what I can gather from the bind option if I delete change the name or move the user directory in home then bind becomes unnecesssary and useless since the move actually and really places it on /dev/sda15 and is no longer required within the Distros home folder, which is similar to if when I had installed selected the option to place the home folder on its own partition.


Is this a correct understanding I have?

---

### Post by JASONFUSARO on 2011-07-20
> **JASONFUSARO said:**
> I am looking at it now, thank you


I have a tendency to go back and modify and edit prior posts, is this a good habit or bad, I am thinking maybe bad for current correspondence and possibly good for someone who starts reading a thread fresh, what is your opinion?

I have modified #64,#65,#66 and others and I am unsure if you have re-read them bodhi




From what I can gather from the bind option if I delete change the name or move the user directory in home then bind becomes unnecesssary and useless since the move actually and really places it on /dev/sda15 and is no longer required within the Distros home folder, which is similar to if when I had installed selected the option to place the home folder on its own partition.


Is this a correct understanding I have?

---

### Post by malspa on 2011-07-20
> **JASONFUSARO said:**
> What I mean is when a package is downloaded it would not be installed dirctly into that particular distro but elsewhere and some sort of link set up wheras if it is called by Distro A its configuration is made availabe to Distro A, and susequently when it is selected by another Distro for installation what would normally be called or downloaded would in fact not be except for what is necessary to the requesting Distro and if differences exist with regards to configuration then that is stored and usable only when Distro B calls it. The uderlying software does not change according to its being run just it's configuration in relation to the particular Distro and that it seems is what is needed by each Distro to be saved for that Distro accordingly.

On this, sir, someone else will have to step in, unless your own research turns up something. I've never heard of this being done. I've been multi-booting several distros for some years now, and I don't think something like this can be done.

---

### Post by JASONFUSARO on 2011-07-20
I just completed Chakra Distro, see ScreenShot

The only problem with this solution is that they can be accessed and viewed no matter which Distro I am using, which is not a major problem, I would have prefered just having access to the particular Distros folder.



The process I have to use is:

Load Distro

Change the username to coincide with the distro

make a copy of boot, home and within home the user directory which because
I am the only user jason it is the same on all unchanged distros and this would cause confusion if simply copied to partition #15 (DistroHood) can't have all jason's, could have if I went the Distro subdirectory route.

open terminal

login as root

start dolphin or any file manager I have on that distro

open the home folder

select the user folder (ie. jason in my case)  rename it to coincide to the distro
ie. Chakra jasonCkra, CtkArch jasonCtk etc..

select copy


select partition #15 (DistroHood) from the places list


paste it there

copy it and put it in the backup folder

select the folder and change permisions, this is easy if running dolphin or thunar as root, apply it recursively to all subdirectories because the copy and paste done using thunar or dolphin as root applies root to everything and this causes a problem if you try and login to the distro without changing it back to your user

open etc/fstab and I add this:
```
/dev/sda15               /home    ext3      defaults     0 0
```

reboot and select the distro from the menu



Changing permissions without using thunar or dolphin I do in terminal as root

cd to the home folder

```

chown -R jasonXXX jasonXXX

```

and

```

chgrp -R jasonXXX jasonXXX

```

change the group and ownership to coincide with the changed username




This process has been working fine so far

---


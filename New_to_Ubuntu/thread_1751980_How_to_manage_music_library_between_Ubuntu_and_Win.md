---
title: "How to manage music library between Ubuntu and Windows 7?"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by computerandu on 2011-05-07
Hi,

I have windows 7 and ubuntu in dual boot. I have pretty good music library in windows 7. I wan them in my banshi music library as well...Copying all the songs in ubuntu is an option but then i'll face the problem of synchronizing two libraries (a newly added album needs to be copied in both...:( )

How do you guys manage your music library between Ubuntu and Windows?
Any suggestions?

---

### Post by Nickjpost on 2011-05-07
You can mount your windows partition and perhaps import the files that way without having to copy them into Ubuntu

---

### Post by computerandu on 2011-05-07
> **Nickjpost said:**
> You can mount your windows partition and perhaps import the files that way without having to copy them into Ubuntu

Th partition needs to be mounted each time i login in to ubuntu....and thus i have to add them again and agin to music library....and scanning 10 Gb in each login is a frustrating thisg to do...

---

### Post by powerpleb on 2011-05-07
> **computerandu said:**
> Th partition needs to be mounted each time i login in to ubuntu....and thus i have to add them again and agin to music library....and scanning 10 Gb in each login is a frustrating thisg to do...

Add it to fstab then you won't need to manually mount it.

Go to a terminal, type "blkid", note down the UUID of your Windows drive
Then enter "gksu gedit /etc/fstab"
Put an entry like thus: "UUID="insert the uuid here" /mnt/win7 ntfs defaults 0 0"
Save and exit

back in terminal enter "sudo mount -a"

It'll automatically mount every reboot now. You can also run a symlink to your home folder by going "ln -s /mnt/win7 ~/win7"

EDIT: What I did was delete the Music folder in my Ubuntu Home folder then symlink the music folder from my Windows partition to my home directory as my Music folder. That means when you open file manager and click on the Music folder down the side you are already there.

---

### Post by klytu on 2011-05-07
> **computerandu said:**
> Th partition needs to be mounted each time i login in to ubuntu....and thus i have to add them again and agin to music library....and scanning 10 Gb in each login is a frustrating thisg to do...

You can add an entry in /etc/fstab to mount your partition automatically 
at login. For example, here's a line I added to my fstab to do this for an
NTFS partition named "Music" where I have my music library:

```
/dev/sda1 /media/Music ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

For more information:

```
man fstab
```

Or post if you have questions.

---

### Post by computerandu on 2011-05-07
Thanks for your suggestion guys...now I'm working on it....hope it will work without any problem...:P

---

### Post by Not unique on 2011-05-07
Another option but a complicated one would be to create a third partition for all your files (in ntfs) and make it your default My documents for Windows and same/similar for home in Ubuntu as every thing is set to look in My documents or Home by default this works well apparently.

---

### Post by computerandu on 2011-05-09
> **powerpleb said:**
> Add it to fstab then you won't need to manually mount it.

Go to a terminal, type "blkid", note down the UUID of your Windows drive
Then enter "gksu gedit /etc/fstab"
Put an entry like thus: "UUID="insert the uuid here" /mnt/win7 ntfs defaults 0 0"
Save and exit

back in terminal enter "sudo mount -a"

It'll automatically mount every reboot now. You can also run a symlink to your home folder by going "ln -s /mnt/win7 ~/win7"

EDIT: What I did was delete the Music folder in my Ubuntu Home folder then symlink the music folder from my Windows partition to my home directory as my Music folder. That means when you open file manager and click on the Music folder down the side you are already there.


Starnge...but blkid returns nothing ...:(

---

### Post by compmodder26 on 2011-05-09
Did you try with sudo?

```
sudo blkid
```

---

### Post by computerandu on 2011-05-09
> **compmodder26 said:**
> Did you try with sudo?

```
sudo blkid
```

So stupid of me....it does work now...oops...made a booboo..

---

### Post by Dreigo42 on 2011-05-09
I have a setup for you that I use that would be perfect. I have a Win7/Ubuntu dual boot as well but I have an additional NTFS partition that is my personal files (Documents,Music,Pictures,ect). In Windows, This partition (set up as the U:\ Drive) is the location of my home folder. Ubuntu however can not use a NTFS partition as a home so I replaced the existing home folders with symbolic links that then route to the appropriate NTFS folders. 

To make the partition mount automatically, I used pysdm.
install using 
sudo apt-get install pysdm 

and set the partition to mount to /mnt/users with the default options 

This is the thread I started when I was working on this
[http://ubuntuforums.org/showthread.php?t=1724016](http://ubuntuforums.org/showthread.php?t=1724016)

---

### Post by Hedgehog1 on 2011-05-10
> **Not unique said:**
> Another option but a complicated one would be to create a third partition for all your files (in ntfs) and make it your default My documents for Windows and same/similar for home in Ubuntu as every thing is set to look in My documents or Home by default this works well apparently.

Like **Dreigo42** and **Not unique** I also use a separate NTFS partition for holding all my Music and Video Files.  It is set to auto mount using an entry in /etc/fstab and makes all 3,700 songs available from either Windows 7 or Ubuntu. 


***The Hedge***

:KS

---

### Post by computerandu on 2011-05-10
> **Dreigo42 said:**
> I have a setup for you that I use that would be perfect. I have a Win7/Ubuntu dual boot as well but I have an additional NTFS partition that is my personal files (Documents,Music,Pictures,ect). In Windows, This partition (set up as the U:\ Drive) is the location of my home folder. Ubuntu however can not use a NTFS partition as a home so I replaced the existing home folders with symbolic links that then route to the appropriate NTFS folders. 

To make the partition mount automatically, I used pysdm.
install using 
sudo apt-get install pysdm 

and set the partition to mount to /mnt/users with the default options 

This is the thread I started when I was working on this
[http://ubuntuforums.org/showthread.php?t=1724016](http://ubuntuforums.org/showthread.php?t=1724016)

Hi,
I have many partitions on my 320 Gb hard disk...that goes something like this:

110 MB system reserve
110 GB Windows7 installation drive
105 GB NTFS
43 GB NTFS
20 GB Linux ext4 (root)
3 GB Swap
39 GB Linux ext4 (supposed to be home drive...but it needs to be mounted every time I login to ubuntu)...


In my 39 GB there are several directories which are not accessible to me...like lost+found, ..i tried formatting the drive last night and now there is an error...

Error: Unknown device type
Grube rescue


:(

---

### Post by Jagoly on 2011-05-10
How much was set up in Ubuntu? If it wasn't to much, with a re-install you could easily get everything auto-mounted and what-not. If the home directory had to be manually mounted on every boot, than /home could not have been there. There are settings in your home directory necessary for Ubuntu to start. In my opinion, if you only have one hard drive, separating /home from / seems sort of pointless. I also don't recommend a separate partition for shared files. Just use you windows drive. This is what I used to do.

On the subject of grub rescue, was grub installed onto that drive by any chance?

---

### Post by computerandu on 2011-05-10
> **Jagoly said:**
> How much was set up in Ubuntu? If it wasn't to much, with a re-install you could easily get everything auto-mounted and what-not. If the home directory had to be manually mounted on every boot, than /home could not have been there. There are settings in your home directory necessary for Ubuntu to start. In my opinion, if you only have one hard drive, separating /home from / seems sort of pointless. I also don't recommend a separate partition for shared files. Just use you windows drive. This is what I used to do.

On the subject of grub rescue, was grub installed onto that drive by any chance?

When I first installed Ubuntu ...it used to mount the root and home partition all b y itself ...and then i tried a clean install of Ubuntu 11.04...after several re-installation i am this stage...

do you think this way of using different drive partitions for root, swap and home is not good?? (I found it on a tutorial to install a dual boot system...and it worked quite effectively..)


about grub...i really have no idea whether or not it was installed on ubuntu...and since i cannot boot into either of windows or ubuntu...i simply cannot know it..

am i clear in explaining the things?

---

### Post by pSYcl0Ne on 2011-05-10
You can fix grub with the live CD - there are literally MILLIONS of how to's all over the web. It all can seem a bit frustrating at first but you'll get the hang. just try comparing a few how to's before picking and choose for yourself.

As suggested by quite a few others - having a separate partition formatted to NTFS or FAT is a good idea - other OS's can read and write and also - if ANY of your OS's mucks up or you need to upgrade - you are keeping it all your media/documents etc separate and safe.)

As for someone previous suggesting having a separate / and /home being redundant on a single drive - like I said - to keep all your docs etc safe when upgrading might be a good reason. Some even prefer to have separate /boot and /temp partitions also.

> **computerandu said:**
> When I first installed Ubuntu ...it used to mount the root and home partition all b y itself ...and then i tried a clean install of Ubuntu 11.04...after several re-installation i am this stage...

do you think this way of using different drive partitions for root, swap and home is not good?? (I found it on a tutorial to install a dual boot system...and it worked quite effectively..)


Sounds like during the fresh install you didnt tell it to use the old installs home folder as /home - you can do this without reformating it. use the advanced tab when doing a fresh install. 

That 100 Gb NTFS partition (the one that is not the Windows install) is a good place to put all your music etc.

---

### Post by computerandu on 2011-05-10
> **pSYcl0Ne said:**
> You can fix grub with the live CD - there are literally MILLIONS of how to's all over the web. It all can seem a bit frustrating at first but you'll get the hang. just try comparing a few how to's before picking and choose for yourself.

As suggested by quite a few others - having a separate partition formatted to NTFS or FAT is a good idea - other OS's can read and write and also - if ANY of your OS's mucks up or you need to upgrade - you are keeping it all your media/documents etc separate and safe.)

As for someone previous suggesting having a separate / and /home being redundant on a single drive - like I said - to keep all your docs etc safe when upgrading might be a good reason. Some even prefer to have separate /boot and /temp partitions also.

I'll use super grub disk tonight...

As you can see i have two separate NTFS partitions...i can use them for storing my docs and musics...right?

>  As for someone previous suggesting having a separate / and /home being redundant on a single drive - like I said - to keep all your docs etc safe when upgrading might be a good reason. Some even prefer to have separate /boot and /temp partitions also.

so you say its a good idea to have root swap and home on different partitions...am i right?

---

### Post by Jagoly on 2011-05-10
> **pSYcl0Ne said:**
> As for someone previous suggesting having a separate / and /home being redundant on a single drive - like I said - to keep all your docs etc safe when upgrading might be a good reason. Some even prefer to have separate /boot and /temp partitions also.

I suppose. I never actually use windows anymore, so it only contains my itunes music library. I moved all of my documents and (non-itunes) movies to my ext4 ubuntu partition just last night.

---

### Post by Jagoly on 2011-05-10
> **computerandu said:**
> I'll use super grub disk tonight...

As you can see i have two separate NTFS partitions...i can use them for storing my docs and musics...right?

so you say its a good idea to have root swap and home on different partitions...am i right?

just put of curiosity, do you know why you have two large ntfs partitions?

---

### Post by pSYcl0Ne on 2011-05-10
> **computerandu said:**
> I'll use super grub disk tonight...


I'd consider using the Ubuntu Live CD and doing a fresh install - like I said - it appears that the latest install is not using the /home partition properly - back up any stuff you dont want to lose


> **computerandu said:**
> As you can see i have two separate NTFS partitions...i can use them for storing my docs and musics...right?

Yep - maybe even delete the smaller one and expand the the larger so you only have one free NTFS partition for all that stuff

> **computerandu said:**
> 
so you say its a good idea to have root swap and home on different partitions...am i right?

Yep.

---

### Post by computerandu on 2011-05-10
> **Jagoly said:**
> just put of curiosity, do you know why you have two large ntfs partitions?

well...i partitioned them that way...105 GB to keep movies and music files....43 Gb to keep softwares and other random stuffs...

---

### Post by computerandu on 2011-05-10
> **pSYcl0Ne said:**
> I'd consider using the Ubuntu Live CD and doing a fresh install - like I said - it appears that the latest install is not using the /home partition properly - back up any stuff you dont want to lose




Yep - maybe even delete the smaller one and expand the the larger so you only have one free NTFS partition for all that stuff



Yep.

Last time when I was trying a clean install of Ubuntu 11.04...I formatted all the linux drives...i.e. 20+3+39...but still something went wrong and now its going this way.,...i'll try a new install tonight and then come back again to with the findings...:P...beauty of linux ...u keep on messing with the system..and u still like it...:)

---

### Post by pSYcl0Ne on 2011-05-14
it's not so much the formatting of the drive (you should def. format / ) but after choosing the file type eg. ntfs or ext4 - with the ext partitions u must flag it to 'use partition as / or /home etc. It sounds like this is where you're going wrong.

---

### Post by computerandu on 2011-05-15
> **pSYcl0Ne said:**
> it's not so much the formatting of the drive (you should def. format / ) but after choosing the file type eg. ntfs or ext4 - with the ext partitions u must flag it to 'use partition as / or /home etc. It sounds like this is where you're going wrong.

I did choose the / and /home...
in any case i have a fresh install now...without any problem...
the problem, i guess, was i already had ubuntu 11.04 but it was not working properly and was hanging at the startup...i thought of installing it again and their (i guess) i chose replace the existing ubuntu ..or something like this (not "do something else")...and this is why it there was some problem with it...

---


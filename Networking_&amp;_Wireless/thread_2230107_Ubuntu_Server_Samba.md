---
title: "Ubuntu Server Samba"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by Harpz on 2014-06-17
Hi All

Ive been using unRAID for my server for few years now but have decided to move it onto Ubuntu Server + snapRAID, before i do this for real though I'm playing / learning in Virtualbox.

Ive been able to install Ubuntu server 14.04 without any issues and have been able to create / format (ext4) and mount automatically 4 virtual disks to play with, Ive set a Static IP for the Virtual Server and now I'm looking at setting up the shares.

The idea is I want to be able to create disk shares and a few other shares that can only be accessed by my main machine (user:mike pw:***) and then using mhddfs to create a virtual mount point for TV_Shows, Movies and Music and have these access by my htpc (user: xbmc pw:****) and any other user that i specify. There will also be a couple of shares that will be open to all on the network.

For the open shares Ive had a look at [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html) and think i understand what i need to do without to much of a problem, but I'm having a problem understanding how i setup the restricted shares as stated here [https://help.ubuntu.com/12.04/serverguide/samba-fileprint-security.html](https://help.ubuntu.com/12.04/serverguide/samba-fileprint-security.html)

I consider myself still quite new to Ubuntu (keep coming and going) but have lernt a lot and not afraid to try, if someone could break down what i need to do in baby steps with maybe a small description of the steps i would very much appreciate it.

---

### Post by bab1 on 2014-06-17
> **Icerat said:**
> Hi All

Ive been using unRAID for my server for few years now but have decided to move it onto Ubuntu Server + snapRAID, before i do this for real though I'm playing / learning in Virtualbox.

Ive been able to install Ubuntu server 14.04 without any issues and have been able to create / format (ext4) and mount automatically 4 virtual disks to play with, Ive set a Static IP for the Virtual Server and now I'm looking at setting up the shares.

The idea is I want to be able to create disk shares and a few other shares that can only be accessed by my main machine (user:mike pw:***) and then using mhddfs to create a virtual mount point for TV_Shows, Movies and Music and have these access by my htpc (user: xbmc pw:****) and any other user that i specify. There will also be a couple of shares that will be open to all on the network.

For the open shares Ive had a look at [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html) and think i understand what i need to do without to much of a problem, but I'm having a problem understanding how i setup the restricted shares as stated here [https://help.ubuntu.com/12.04/serverguide/samba-fileprint-security.html](https://help.ubuntu.com/12.04/serverguide/samba-fileprint-security.html)

I consider myself still quite new to Ubuntu (keep coming and going) but have lernt a lot and not afraid to try, if someone could break down what i need to do in baby steps with maybe a small description of the steps i would very much appreciate it.

It will be easier to provide examples if you provide what you want to accomplish.  The link shows you all the user security types and specifically talks about *security = user* to define ownership and permissions.  How are you managing your Linux user accounts? 

Essentially you can have private shares (restricted to 1 user), semi-private (restricted to 1 or more groups) or public shares (open to all users).  You can accomplish this with all the security = <something> as that only tells Samba where and how to access the user information.

Samba only provides access security..  The Linux system provides the authorization.  I'm not sure how the Linux ownership and permissions scheme is implemented on the various aggregated partitions.  What happens if the ownership of the root directory of one partition is different from another?

---

### Post by Harpz on 2014-06-17
> **bab1 said:**
> It will be easier to provide examples if you provide what you want to accomplish.  The link shows you all the user security types and specifically talks about *security = user* to define ownership and permissions.  How are you managing your Linux user accounts? 

Essentially you can have private shares (restricted to 1 user), semi-private (restricted to 1 or more groups) or public shares (open to all users).  You can accomplish this with all the security = <something> as that only tells Samba where and how to access the user information.

Samba only provides access security..  The Linux system provides the authorization.  I'm not sure how the Linux ownership and permissions scheme is implemented on the various aggregated partitions.  What happens if the ownership of the root directory of one partition is different from another?

Maybe I was over thinking this or not understanding what I want to do.

Basically I have 9 disks, on these disks there are folders named TV_Shows, Music, Movies, I was planning to use mhddfs to join all theses TV_shows, Movies and Music folders to a single virtual mount point names TV_shows, Movies and Music.

Have i misunderstood what mhddfs can do? I was then planning to share these 3 amalgamated folders with my main win8 machine and my htpc machine which runs win7 + xbmc.

I also have a folder called backups which I only want to be able to access from my main machine and none of the other machines in the house, the kids also have a folder and i would only like them to be able to access this folder and nothing else.

Maybe im just over complicating the issue and should just create open shares as explained here [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html) but I would still like to restrict access to certain shares on the network to just my main machine ie backups and I don't really want the kids to be able to access the htpc TV_Shows, Movies and Music shares from there laptops either.

With my current unRAID setup i have a user mike (me) and i have full read write access to all shares, the kids can only access there kids folder and don't have access to anything else, the wife has full read write access to her area and has read only access to the rest, the htpc has read only access to TV_Shows, Music and Movies and cant access anything else.

I hope this makes sense.

---

### Post by bab1 on 2014-06-17
> **Icerat said:**
> Maybe I was over thinking this or not understanding what I want to do.

Basically I have 9 disks, on these disks there are folders named TV_Shows, Music, Movies, I was planning to use mhddfs to join all theses TV_shows, Movies and Music folders to a single virtual mount point names TV_shows, Movies and Music.

Have i misunderstood what mhddfs can do? 

I think you have the idea correct.  It will make a pool of disks (actually their partitions) appear as one large partition.  In Linux terms, file systems organized on partitions.  The drive is the physical device.

The problem I see is that you don't really know how the file system is going to be organized.  Neither do I.  I've never used mhddfs.  In addition, as mhddfs is not a kernel based file system you better have a pretty healthy CPU and fast drives (I/O) or performance is going to be pretty slow.  Not good for a HTPC.

I would talk to @rubylaser of this forum.  He deals with large disk arrays and is familiar with mhddfs.

To me the alternative to mhddfs is lvm2.  You can pool disks (devices) and format them as one partition (the pool).  The disks can be of any size and you can add to it later.  I create mine with no data on them.  I don't think you can use disks with data and save the date.  But then again you do have all the data backed up.  I share various directories using Samba using LVM2 to manage the disk pool (array).
> 
I was then planning to share these 3 amalgamated folders with my main win8 machine and my htpc machine which runs win7 + xbmc.

Once you have your disk pool set up we will deal with it as a single file system.  As I said, you can share individual directories with no problems.  The share is not aware of where the data is ultimately located.  That's the job of the OS and the FS setup.
> 
I also have a folder called backups which I only want to be able to access from my main machine and none of the other machines in the house, the kids also have a folder and i would only like them to be able to access this folder and nothing else.

Samba can restrict access by machine, but I like to be able to access data from any machine.  I'm the system administrator and I should have access from my kids machine.  They on the other hand should not.  I suggest you limit access by user name rather than by limiting any machine.
> 
Maybe im just over complicating the issue and should just create open shares as explained here [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html) but I would still like to restrict access to certain shares on the network to just my main machine ie backups and I don't really want the kids to be able to access the htpc TV_Shows, Movies and Music shares from there laptops either.

With my current unRAID setup i have a user mike (me) and i have full read write access to all shares, the kids can only access there kids folder and don't have access to anything else, the wife has full read write access to her area and has read only access to the rest, the htpc has read only access to TV_Shows, Music and Movies and cant access anything else.

I hope this makes sense.
This all can be done by  user and group access limits.

The part that needs to be looked at first is creating the data pool. Whether you use mhddfs, LVM2 or something else you need to get the pool set up first.  You also need to judge whether your sever has enough CPU and disk capacity if you decide to use mhddfs.  I would see if I could get ahold of @rubylaser and have him participate in this thread.

Have you seen [this blog post ]("http://zackreed.me/articles/84-snapraid-with-mhddfs")by @rubylaser ?   Read the comments by him.

---

### Post by Harpz on 2014-06-18
You say that mhddfs  needs a healthy CPU so that may put me off this project as i built my sever on  budget but works great with unraid:

**Case**: MS-Tech CA-210 (3x X-Case 5in3) | **PSU**: Antec 520W High Current Gamer Modular
**MB**: Asus M5A78L-M LX V2 | **CPU**: AMD Sempron X2 190 2.5GHz | **Memory**: Crucial 4GB
**PCI-e Controller card**: IBM ServeRAID M1015/LSI SAS9220-8i
**Parity**: TOSHIBA_DT01ACA300 | **Cache**: 250GB-VB0250EAVER | **Data**: 1x 3TB-WD30EZRX, 2x 2TB-WD20EARX, 1x 2TB-WD20EARS, 1x 2TB-SAMSUNG_HD204UI, 1x 1TB-WD10EARS | 1x 500GB-SAMSUNG_HD501LJ | 1x 2TB-Toshiba DT01ABA200, 1x 1TB SAMSUNG_HD103SJ
**UPS**: APC Smart-UPS 1000

The project was to use Ubuntu server as a base + snapRAID for parity protection then use mhddfs for the pooling.

I'm guessing i need to fire up the Ubuntu server VM and have a play with samba first though to see if i can get the same config as the SMB shares on my unRAID box.

Limiting access by user name rather than by machine sound just what i want to do, i can then log in on any machine at home and have full access to the server. Are you able to provide any pointers on how to do this?

In the post you linked he says that *"Even my wimpy Celeron 847 reads from the pool over NFS about 60-65MB/s and writes to it between 30-60MB/s"*  and his i3-2100 *"reads and writes about 125MB/s or as fast an individual disk is"*, this is a lot more then i get writing to my unRAID box, 45MB/s tops, i think reads are around the 100MB/s mark. I have no issues streaming a 1080p mkv from server to the xbmc htpc.

If i look at the pass mark scores for the Intel Celeron 847 @ 1.10GHz it gets **979** my AMD Sempron X2 190 gets **1514** and his Intel Core i3-2100 @ 3.10GHz gets **3617** so in theory i should get better write performance then I'm getting at the moment and read performance should be around the same as current.

---

### Post by bab1 on 2014-06-18
If you don't mind I'm going to move the  paragraph order around a little bit.  I won't address the storage pool aspect as I have no real world experience with either snapRAID or mhddfs.  The only thing I can say about the hardware is use what you have.  That should dictate what software solution you use.  kernel based file systems are a lot more efficient than userspace file systems.

I urge you to PM [@rubylaser]("http://ubuntuforums.org/member.php?u=1115132") and get him involved with your issues here.

> **Icerat said:**
> You say that mhddfs  needs a healthy CPU so that may put me off this project as i built my sever on  budget but works great with unraid:

**Case**: MS-Tech CA-210 (3x X-Case 5in3) | **PSU**: Antec 520W High Current Gamer Modular
**MB**: Asus M5A78L-M LX V2 | **CPU**: AMD Sempron X2 190 2.5GHz | **Memory**: Crucial 4GB
**PCI-e Controller card**: IBM ServeRAID M1015/LSI SAS9220-8i
**Parity**: TOSHIBA_DT01ACA300 | **Cache**: 250GB-VB0250EAVER | **Data**: 1x 3TB-WD30EZRX, 2x 2TB-WD20EARX, 1x 2TB-WD20EARS, 1x 2TB-SAMSUNG_HD204UI, 1x 1TB-WD10EARS | 1x 500GB-SAMSUNG_HD501LJ | 1x 2TB-Toshiba DT01ABA200, 1x 1TB SAMSUNG_HD103SJ
**UPS**: APC Smart-UPS 1000

In the post you linked he says that *"Even my wimpy Celeron 847 reads from the pool over NFS about 60-65MB/s and writes to it between 30-60MB/s"*  and his i3-2100 *"reads and writes about 125MB/s or as fast an individual disk is"*, this is a lot more then i get writing to my unRAID box, 45MB/s tops, i think reads are around the 100MB/s mark. I have no issues streaming a 1080p mkv from server to the xbmc htpc.

If i look at the pass mark scores for the Intel Celeron 847 @ 1.10GHz it gets **979** my AMD Sempron X2 190 gets **1514** and his Intel Core i3-2100 @ 3.10GHz gets **3617** so in theory i should get better write performance then I'm getting at the moment and read performance should be around the same as current.

The project was to use Ubuntu server as a base + snapRAID for parity protection then use mhddfs for the pooling.

I have two storage servers I built with P3 CPUs and 500MB RAM.  They have SATA cards that I attach the disks to.  They support both NFS exports and Samba shares with no problem.  Both machines use ext4 file system formatting.  Disk I/O is what is important here.  Both of these machines have on occasion streamed HD movies.
> 
I'm guessing i need to fire up the Ubuntu server VM and have a play with samba first though to see if i can get the same config as the SMB shares on my unRAID box.

Limiting access by user name rather than by machine sound just what i want to do, i can then log in on any machine at home and have full access to the server. Are you able to provide any pointers on how to do this?

I can provide you with a complete step by step solution for each share you want.

I assume you have installed the package samba on Ubuntu 14.04 ```
sudo apt-get install samba
```
The following is just an example```

# Check to see if user has been added
  sudo pdbedit -L  
#Add the user <username> to the users group
  sudo adduser <username> users
#Check to see if <username> is in the users group
  getent group users    
#Create the share root directory
  sudo mkdir -p /srv/samba/public
#Set the group inheretance for the directory
  sudo chown root:users /srv/samba
  sudo chmod 2775 /srv/samba/public
#Check the dirctory settings
  ls -ld /srv/samba
    
#To create the share you add this to the bottom of the smb.conf file

[public]
	comment = Shared Data
	path = /srv/samba/public
        browseable = yes
        guest ok = yes
        writeable = yes
        force group = users
        create mask = 0664
        force directory mode = 775       
        
#Restart the smb daemon
  sudo service smbd restart
  
# If this Ubuntu 13.10, we need to take care of a bug in Nautilus permissions.  Luckily there is a repair already available. See # here  for the answer at post#23 and on:
#    https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686
  
# The package is for Trusty (14.04) and is backwards compatible to 13.10, which is the only version that has this problem. 
```
This is only an example for you to think about what to do.  It does work.  I will help you set up your network.  I suggest that you use at least 3 groups.  Something like: *kids, users, * and * backup. *  You and your wife will be in *users*.  The kids will be in * kids* and you will use the group *backup* exclusively.  In addition there is a built in group named *[homes] * that when you configure, automatically makes available a private share for the logged in user.

I would start this part of the sharing by making sure that all mortal users (humans) have an identical username on all of the computers the they will use.  I'd create user accounts for you (and maybe your wife) on the kids machines and make sure that you your account (username = mike) is on ALL machines (yours, your wife's and the kids machines)  As far as the Samba server you also need to have accounts for you, your wife and each kid as both an Ubuntu user and a Samba user.

Ask all the questions you want.  No question is silly.  I'd rather make everything clear before we have to clean up a mess  Then we will settle on a sharing scheme that works for you.

---

### Post by Harpz on 2014-06-23
Thanks for the info **bab1**

Actually had a chance to have a play with this in the VM this weekend and surprised myself :)

I set up 4 virtual drives 2x 5GB and 2x 8GB, created the partitions and formatted then to ext4. then i created the mount points in /mnt/*disk_serial_number* and got them to auto mount by adding the disk UUID and relevant options to the fstab.

Next i created 4 shares to share the mount points for disks with samba using the example on [https://help.ubuntu.com/14.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/14.04/serverguide/samba-fileserver.html)
```

[share]
    comment = Disk 1 Share
    path = /mnt/disk1serial
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

```
This worked out great and i was able to see the shares on the network via my win 7 box and drop files to the shares.

On 2 of the disks i created a folder named TV_Shows and the other 2 disks i created a folder called Movies, I put a couple of shows in the 2x TV_Shows directories and a couple of movies in the 2x Movies directories.

Now i wanted to test the pooling, i installed mhddfs  with
```
sudo apt-get install mhddfs
```
Created a mount point for each of the pools with:
```

sudo mkdir /mnt/TV_shows
sudo mkdir /mnt/Movies
```
Then i edited the fstab again and added the appropriate paths to pool the folders i want pooled:
```

mhddfs#/mnt/disk1serial/TV_Shows,/mnt/disk3serial/TV_Shows /mnt/TV_Shows fuse defaults,allow_other,nonempty 0 0
mhddfs#/mnt/disk2serial/Movies,/mnt/disk4serial/Movies /mnt/Movies fuse defaults,allow_other,nonempty 0 0

```
This worked as expected so i shared the pooled mount points with samba and was able to see and browse them over the network from my win7 box.

My next task it to get my head around share permissions and groups, how do i add users, add users to a certain group and then allow only a certain group to access a specific share?

With the little reading Ive done am i correct in saying that samba has its own username / password store, I mean if i add a user to samba that user cant log on to the server with the same user name and password? The only person i want to be able to log into the server is me, if anyone other then me tries to log into the server they are unsuccessful.

I think i understand the concept of what i want to do, add a user, add that user to a group, tell samba only allow access to a certain share from a given group?
```

force group = users
```
Have i got the right idea or am i way off?

---

### Post by bab1 on 2014-06-23
> **Icerat said:**
> 
My next task it to get my head around share permissions and groups, how do i add users, add users to a certain group and then allow only a certain group to access a specific share?

I provided you the steps needed in my last post.  Just under the sentence: *The following is just an example*.
> 
With the little reading Ive done am i correct in saying that samba has its own username / password store, I mean if i add a user to samba that user cant log on to the server with the same user name and password? The only person i want to be able to log into the server is me, if anyone other then me tries to log into the server they are unsuccessful.

There are mortal users (with login) and system users (no login).  Create Linux system users with no password and Samba users with a Samba login password.
> 

I think i understand the concept of what i want to do, add a user, add that user to a group, tell samba only allow access to a certain share from a given group?
```

force group = users
```
Have i got the right idea or am i way off?
Yes, the idea is to have a common group so that all users in that group have read/write permissions.  I go a step farther then *force group *as I have Ubuntu users who access those directories via NFS.  I use sgid (set group bit) on the directories to create group inheritance as well.

---

### Post by Harpz on 2014-06-23
> **bab1 said:**
> I provided you the steps needed in my last post.  Just under the sentence: *The following is just an example*.
Ah ok i see that bit now, means nothing at the moment will probably mean more when i play.
> **bab1 said:**
> 
There are mortal users (with login) and system users (no login).  Create Linux system users with no password and Samba users with a Samba login password.
This bit lost me, so I have to create the user twice. Whats the diffrernce bewtween a Linux system users and Samba users with a Samba login password?
> **bab1 said:**
> 
Yes, the idea is to have a common group so that all users in that group have read/write permissions.  I go a step farther then *force group *as I have Ubuntu users who access those directories via NFS.  I use sgid (set group bit) on the directories to create group inheritance as well.
Think i understand the group concept now.

I  would be a member of all the groups i create so i get full access to all the shares i create? The wife would be the same but she wouldn't get access to the backup backup group and share and the kids would be a members of there own group and only be able to access the kids share?

---

### Post by bab1 on 2014-06-23
> **Harpz said:**
> 

> There are mortal users (with login) and system users (no login). Create Linux system users with no password and Samba users with a Samba login password.
This bit lost me, so I have to create the user twice. Whats the diffrernce bewtween a Linux system users and Samba users with a Samba login password?

You are not creating users.  You are creating **user accounts**.  So the proper answer is: yes you need to ave both a Linux user account and a Samba user account.  If you don't want the user to be able to login and that user has no need for a home directory then you can create an account like that .  These accounts are called system user accounts.  To see all the users on your Linux machine you can use this command```
getent passwd
```...as you can see there are more system users than mortal users (humans that login).  The system users never login to the server. 
> 
Think i understand the group concept now.  I  would be a member of all the groups i create so i get full access to all the shares i create? 
The wife would be the same but she wouldn't get access to the backup backup group and share and the kids would be a members of there own group and only be able to access the kids share?
Yes this is correct.  It will be clearer if you create a user group and setup a share that limits access by group.

Just a few things for you to think about:

The Samba user only gains access to the Samba resources.  The Linux user of the same name gains authorization to use these resources as they are really Linux files and directories.  Samba can restrict the user from resources but it can never give you permission to something the Linux has not allowed first.

Don't place shares inside other shares.  This will cause no end to permissions problems.  If you do not want anyone in your backup share then  the file hierarchy should look something like this```

/srv/samba/backup

/srv/samba/kids

/srv/samba/movies

/srv/samba/music
```...this way the share directories show up as //server/backup or //server/kids or //server/movies or //server/music.  The Windows Sharing/Samba notation is always //server/share.

For example,  if you want to have R rated and greater movies shared to you only, you shouldn't make that share under /srv/samba/movies.  It is far easier to administrate the separate share at /srv/samba/restricted-movies (//server/restricted-movies).

---


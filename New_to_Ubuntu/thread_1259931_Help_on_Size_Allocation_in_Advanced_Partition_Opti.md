---
title: "Help on Size Allocation in Advanced Partition Option"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by chandru155 on 2009-09-06
Hi Guys,
       I use Dual boot Windows and Ubuntu(Windows installed First). Now i am using Wubi. I was recommended not use Wubi to get good performance. So i am planning to install Ubuntu using Advanced Partion Option. My Hardware Configuration as follows

160GB HardDisk
P IV Processor
512MB Ram
NVIDIA 5200 256MB Graphics Card

I am going to allocate 20GB for ubuntu. How much space should i allocate to '/',Home and swap. I googled and got that, for swap size=2*RAM. I may use Hibernation.  For Home, its our choice. And i dont know about '/'. How much space should i allocate? I am the only user going to use. Shall i allocate swap and '/' alone or swap+home+'/'? which will be good?

Another Doubt:

[LIST=1]
[*]If i have separte Home and if i reinstall Ubuntu, can i get the old files(Documents,videos,pictures etc) in the new fresh install of ubuntu?
[*]If i reinstall Windows Xp, how can i boot to Ubuntu?
[/LIST]

---

### Post by nandemonai on 2009-09-07
> **chandru155 said:**
> Hi Guys,
       I use Dual boot Windows and Ubuntu(Windows installed First). Now i am using Wubi. I was recommended not use Wubi to get good performance. So i am planning to install Ubuntu using Advanced Partion Option. My Hardware Configuration as follows

160GB HardDisk
P IV Processor
512MB Ram
NVIDIA 5200 256MB Graphics Card

I am going to allocate 20GB for ubuntu. How much space should i allocate to '/',Home and swap. I googled and got that, for swap size=2*RAM. I may use Hibernation.  For Home, its our choice. And i dont know about '/'. How much space should i allocate? I am the only user going to use. Shall i allocate swap and '/' alone or swap+home+'/'? which will be good?

Another Doubt:

[LIST=1]
[*]If i have separte Home and if i reinstall Ubuntu, can i get the old files(Documents,videos,pictures etc) in the new fresh install of ubuntu?
[*]If i reinstall Windows Xp, how can i boot to Ubuntu?
[/LIST]

My suggestion:

SWAP = 1G
/ = 6G
/home = all remaining space within the space you set aside

Questions:

1. Yes, provided you remount it at install and DONT select the check to format the /home partition

2. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by chandru155 on 2009-09-07
Thanks. I shoudl format as Primary or Logical. I installed Windows(in C Drive) as Primary one. So should i install '/' as Primary? or Logicall is fine?

---

### Post by nandemonai on 2009-09-07
Up to you. If the windows partition is on the same drive you'll just fit them in.

General rule of thumb is:

4 primary partitions = Full partition table.
3 primary partitions + 1 extended partition = Full partition table.

Logical partitions go inside a extended partition (you can have an unlimited amount of logical partitions within a extended partition).

You could have one primary one extended then any extras as logicals inside.

If you're certain you need no extra partitions than Win, swap, / and /home then may as well go all primaries.

---

### Post by chandru155 on 2009-09-07
Reply soon. Urgent. In which order should i create? root,swap and home or ? Reply soon. I am installing now.

---

### Post by nandemonai on 2009-09-07
> **chandru155 said:**
> Reply soon. Urgent. In which order should i create? root,swap and home or ? Reply soon. I am installing now.

Doesn't really matter, personally I go /boot, swap, /, /home but that's me ;)

---

### Post by Paqman on 2009-09-07
> **chandru155 said:**
> I was recommended not use Wubi to get good performance.

Sorry to say it, but you're unlikely to see any performance improvement by moving to a dedicated partition. While it's true there is a slight disk performance hit with Wubi, it's so small you're highly unlikely to notice it.

The real drawbacks of Wubi are:
[LIST=1]
[*]No support for hibernation
[*]Poor tolerance of power interruptions
[/LIST]

Otherwise, a Wubi-installed system will perform just as well as a traditional install.

---

### Post by chandru155 on 2009-09-07
Hi Guys,
      I installed successfully. I have one doubt. In home folder under my user directory, i saw lots of hidden files(some settings of the softwares i installed like flash etc). What will happen if i reinstall Ubuntu? Can i get back all the files in the home directory. The user  Nandemonai told me that i can get my old Home with unchecked option for Foramt in /home while installing Ubuntu(he told me in this thread only,2nd post). If so, what will happen to this hidden files(.flash folders and other . folders). Will they present in my New Ubuntu?

Now, I have /home/chandru(Current user name is chandru). If i give user name as "sekar" in new fresh install of Ubuntu, what will happen? if both chandru and sekar present, will i be able  delete the user directory "chandru" of past installation of ubuntu? or just "sekar" alone present in the new installation of ubuntu? if sekar alone, how can i get the files in old ubuntu home? 

Sorry, if you cant understand what i am trying to say

---

### Post by nandemonai on 2009-09-07
> **chandru155 said:**
> Hi Guys,
      I installed successfully. I have one doubt. In home folder under my user directory, i saw lots of hidden files(some settings of the softwares i installed like flash etc). What will happen if i reinstall Ubuntu? Can i get back all the files in the home directory. The user  Nandemonai told me that i can get my old Home with unchecked option for Foramt in /home while installing Ubuntu(he told me in this thread only,2nd post). If so, what will happen to this hidden files(.flash folders and other . folders). Will they present in my New Ubuntu?

Now, I have /home/chandru(Current user name is chandru). If i give user name as "sekar" in new fresh install of Ubuntu, what will happen? if both chandru and sekar present, will i be able  delete the user directory "chandru" of past installation of ubuntu? or just "sekar" alone present in the new installation of ubuntu? if sekar alone, how can i get the files in old ubuntu home? 

Sorry, if you cant understand what i am trying to say

The hidden files are settings files which will mean when and if you reinstall all your application settings will carry through to the new install (you'd still have to reinstall the applications themselves though).

If you're reinstalling the same version of ubuntu then it's safe and handy to keep those files but if you're reinstalling a newer version it's usually better to remove these hidden files as they can sometimes cause conflicts if installing newer versions of said applications.

As for the other question, if you use a different username that's ok, the files in /home will still be there. You'd just have to move and take ownership of what you want into the new user directory.

---

### Post by chandru155 on 2009-09-07
Thanks

---


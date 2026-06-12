---
title: "hi im going to partition my hard drive for a new install of 9.10 help"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by blake7 on 2009-11-07
hi can u suggest a good set for the size for the os, home folder and documents

i have  never do this be for so all your help and advice would be appreciated 

thank you very much

ps i have 160gb hard drive with my ibm x60s

---

### Post by ArrSea on 2009-11-07
blake7, are you installing ubuntu for the first time?
or partitioning to make a new /dev for ubuntu 9.10?
Are you installing from a CD? DVD?

hope I can help you,

ArrSea

---

### Post by LewRockwell on 2009-11-07
partitioning ideas:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

---

### Post by blake7 on 2009-11-07
hi i used ubuntu for a long time but never partitioned before so any sujestion would be welcome even the obvious 

cheers
ps i have the 9.10 cd 




blake7, are you installing ubuntu for the first time?
or partitioning to make a new /dev for ubuntu 9.10?
Are you installing from a CD? DVD?

hope I can help you,

---

### Post by ArrSea on 2009-11-07
Ok, if you have boot from CD as first in your BIOS settings ( I can explain that if you need)
then you should be able to just put the CD in, restart your computer.

When the CD runs it will show a menu and ask what you want to do (use it as a LiveCD, install, etc.)

If you select install, you should be asked if you want to create a new partition for the install. 

Hope that helps,

ArrSea

---

### Post by blake7 on 2009-11-07
yea so how much spaace is needed for 9.10 for and regular user

also is thier simple way to take a snape shot of all my programs

thank you

---

### Post by kansasnoob on 2009-11-07
Have you tried the Live CD yet?

That's the first thing I'd do before even thinking about installing.

Also is Ubuntu going to be the only OS on this machine or is it going to be a dual-boot?

If it's going to be a dual-boot what is the other OS?

Will the machine have more than one hard drive?

---

### Post by raymondh on 2009-11-07
> **blake7 said:**
> yea so how much spaace is needed for 9.10 for and regular user

also is thier simple way to take a snape shot of all my programs

thank you

-10-15GB for root (/)
-as much as you can afford for /home
-swap at least 1-2GB (really depends on your hibernation habits and system usage)

Do you plan to create the partitions beforehand of do it during the install?
Do you plan to dual-boot with another OS?
How many HD's?

As for "snapshot" of your regular programs .... are you asking what's installed as of now?  A quick way os to look at synaptic and check the installed programs.  Or, are you referring to something else like cloning or transferring apps to the new version?

---

### Post by ArrSea on 2009-11-07
> **blake7 said:**
> yea so how much spaace is needed for 9.10 for and regular user

also is thier simple way to take a snape shot of all my programs

thank you

checking that out for you,
 will get back to you in a bit,

ArrSea

---

### Post by blake7 on 2009-11-07
oh so i can do all this as i load 9.10???
if so that sounds the esayest way 

no im just going to load 9.10 

cheers

---

### Post by blake7 on 2009-11-07
where will synaptic load all the programs to and iplayer???

cheeer

---

### Post by dewbuntu on 2009-11-07
To get a list of currently installed packages, I use - 

dpkg --get-selections >installed-apps

This creates a file showing all packages installed.  Hope this helps!

Dewayne

---

### Post by blake7 on 2009-11-07
how can i referring to something else like cloning or transferring apps to the new version?


thank you

---

### Post by blake7 on 2009-11-07
what do i do with this

dpkg --get-selections >installed-apps

sorry

---

### Post by kansasnoob on 2009-11-07
I'm still a bit unclear on this. Is there any OS installed on this machine at this time?

Are there files and stuff you'd like to save?

Is this a new hard drive?

And what's happening to the old hard drive?

And, I didn't bother Googling, is this a Desktop computer or a Laptop?

---

### Post by blake7 on 2009-11-07
yea i have saved my home folder so thats all nice and safe
im got 9.04 and iam going to load 9.10 on to the same drive but this time i want tput my home folder in it own partitiion on my lap top

thanky you for your time

---

### Post by ArrSea on 2009-11-07
Yes, you can partition as you install.
About creating a snap shot of your programs, I don't rally know. 
I just wrote a list of all the programs I used and then used Add/Remove Applications (or Synaptic) to install them. 
I am not sure about how much space you need. It should show you how much space needed for the default install, just increase that by however much more space you need. 

Hope that helps,

ArrSea

---

### Post by dewbuntu on 2009-11-07
The procedure I use to install same apps on new system as old is - 
On old system run
       dpkg --get-selection >installed-apps
This creates list of all installed packages/applications, copy this file to new system.  On new system run -
       dpkg --clear-selections
       dpkg --set-selections >installed-apps
       sudo apt-get dselect upgrade

This will install all the packages listed in file created of installed packages.

D

---

### Post by kansasnoob on 2009-11-07
> **blake7 said:**
> yea i have saved my home folder so thats all nice and safe
im got 9.04 and iam going to load 9.10 on to the same drive but this time i want tput my home folder in it own partitiion on my lap top

thanky you for your time

Well, unless Home is on a separate partition it's not "nice and safe"! In fact during any repartitioning or reinstall nothing is "nice and safe" unless it's backed up somewhere other than the computer you're working on.

Since you're currently running 9.04 would you be so kind as to post a screenshot of gparted?

If it's not installed just go to terminal:

```
sudo apt-get install gparted
```

It'll then show up in System > Administration > Partition Editor and you can use the paper clip icon at the top of the forum form to attach that screenshot.

---

### Post by blake7 on 2009-11-07
no sorry my home folder is nice and safe on an external hard drive

thank hyou

---

### Post by blake7 on 2009-11-07
one last thing what is a swap memory

thank you

---

### Post by kansasnoob on 2009-11-07
OK, all you need to do is boot the Live CD and choose "try with no changes.........".

Once you're in the live desktop try a few things, like opening Firefox to be sure you can connect to the web, and anything else you commonly use.

Everything will run slower because it's running from RAM and the CD drive which is slower than your hard drive. If it seems OK go to System > Administration > GParted.

Post a screenshot and I'll tell you how to proceed!

---

### Post by kansasnoob on 2009-11-07
> **blake7 said:**
> one last thing what is a swap memory

thank you

You must have a SWAP partition! It should be slightly larger than the system RAM, but only seldom is more than 1 GB needed.

---

### Post by phillw on 2009-11-07
> **blake7 said:**
> one last thing what is a swap memory

thank you


Swap is an area of your hard drive that the system can use if it runs out out RAM (memory chips)

The general view is that you want 1GB of swap if you have less than, or upto 1GB of RAM installed, if you have more than 1GB of RAM, make your swap area equal to your RAM.  

All bets go off for servers, heavy photo editing etc, but that is pretty decent 'rule of thumb'.

As Linux is very good at memory usage, you should rarely see the swap area being used - It's just to have it there .... like backups are always good to have ;):D

If you want to read up on the subject, head over here -->>  [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Phill.

---

### Post by kansasnoob on 2009-11-07
> **phillw said:**
> Swap is an area of your hard drive that the system can use if it runs out out RAM (memory chips)

The general view is that you want 1GB of swap if you have less than, or upto 1GB of RAM installed, if you have more than 1GB of RAM, make your swap area equal to your RAM.  

All bets go off for servers, heavy photo editing etc, but that is pretty decent 'rule of thumb'.

As Linux is very good at memory usage, you should rarely see the swap area being used - It's just to have it there .... like backups are always good to have ;):D

If you want to read up on the subject, head over here -->>  [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Phill.

And, since it's a laptop, it can effect suspend and sleep!

---

### Post by blake7 on 2009-11-07
is that where i should load 9.10???? 


im sorry i put this message in the wronge place earilyer

ps is their somewhere that tell me all this

pss what is the mount point;boot and is that where i should put 9.10

---

### Post by tommynz1975 on 2009-11-07
> **raymondhenson said:**
> -10-15GB for root (/)
-as much as you can afford for /home
-swap at least 1-2GB (really depends on your hibernation habits and system usage)


Thanks for your post

as this is info I was looking for, for my next dual boot project.
a.k.a the mother.

---

### Post by kansasnoob on 2009-11-07
> **blake7 said:**
> is that where i should load 9.10???? 


im sorry i put this message in the wronge place earilyer

ps is their somewhere that tell me all this

pss what is the mount point;boot and is that where i should put 9.10

Huh, what?

No screenshot!

How can we possibly help?

---

### Post by ArrSea on 2009-11-08
Hey, blake7 if you're still looking for something to take a "snapshot" of your programs, you might want to google "aptonCD" It sounds like what you're looking for.

-ArrSea

---


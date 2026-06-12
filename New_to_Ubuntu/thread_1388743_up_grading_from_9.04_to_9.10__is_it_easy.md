---
title: "up grading from 9.04 to 9.10 ? is it easy?"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by beanco on 2010-01-23
I assume it is as easy as hittin the link on update manager...

wonder if it will resolve my WiFi pro lmes at work....

[http://ubuntuforums.org/showthread.php?t=1311273](http://ubuntuforums.org/showthread.php?t=1311273)


Thanks 

Rob

---

### Post by baltadt on 2010-01-23
As far as I know the update did fix the wifi problem for some computers. 

[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

It all depends on your brand of wireless adapter. But yes if you click the link in update manager it will be automated. Some features will not be added though like EXT 4 file format. To get thatyou must do a clean install or change it manually (not for beginners).

---

### Post by Gone fishing on 2010-01-23
> **beanco said:**
> I assume it is as easy as hittin the link on update manager...

Possibly - however, backing up everything in /home and doing a clean install might give better results

---

### Post by J V on 2010-01-23
Which is why everyone should use a seperate /home, saves a LOT of time in fresh upgrades.

---

### Post by ratcheer on 2010-01-23
Upgrading 9.04 to 9.10 worked just fine, for me. There were a couple of minor configuration issues, but they were easily found and fixed.

Tim

---

### Post by warfacegod on 2010-01-23
Doing an upgrade is not entirely automated. It may need to ask you a few questions. Bear in mind that upgrading is not reversible if you don't like the results. But to answer your question, yes, as a whole an upgrade install is very easy. If you have a slow internet connection, however, I recommend a clean install. (Actually, I always recommend a clean install.) If your connection isn't all that fast then expect a long, long operation. Several hours at least.

---

### Post by Wataru8675 on 2010-01-23
Alright, bear with this message, but I'm really still not too familiar with the terminology...

> **J V said:**
> Which is why everyone should use a seperate /home, saves a LOT of time in fresh upgrades.

What do you mean by this?  Should I put everything I want into a compression, like .tar.gz, and put it in /home?  And then when I do a clean install (I presume this means burn the 9.10 .iso to a disc and install it over 9.04), will everything in /home stay there for me to decompress?

EDIT:
Meant to quote this:
> Possibly - however, backing up everything in /home and doing a clean install might give better results.

But for the first post, what do you mean by creating a separate /home?

---

### Post by rogue_0111 on 2010-01-23
If you leave it in your current "/home" folder "all is lost" with 9.10 fresh install. 

Put the backed up/ compressed "/home" on an external or on a separate partition or DVD's then do the fresh install.


good luck

---

### Post by Wataru8675 on 2010-01-23
> **rogue_0111 said:**
> If you leave it in your current "/home" folder "all is lost" with 9.10 fresh install. 

Put the backed up/ compressed "/home" on an external or on a separate partition or DVD's then do the fresh install.


good luck

When I tried to make an archive of my /home folder, it told me that permission was denied.  I just went to the folder, right clicked, and did "Create Archive."  Is there another way to go about it in the terminal with a sudo code or something?

---

### Post by natravis on 2010-01-23
> **Wataru8675 said:**
> When I tried to make an archive of my /home folder, it told me that permission was denied.  I just went to the folder, right clicked, and did "Create Archive."  Is there another way to go about it in the terminal with a sudo code or something?

You cannot do that as the folder would be in use. If you want to back it up that way, use a live cd to mount the drive and back up in that manner. The /home references people are making refer to partitioning your hard drive to have a /home parition, / (root) partition, and swap. There are countless threads devoted to that so use the search or google it.

---

### Post by beanco on 2010-01-24
I have made clean installs before, then I backed up everything, etc and did the new .iso then installed that....

I was just wondering how much faster it might be if I try going through the  update manager.

I do not have the time in the up coming days to deal with tweaking an upgrade to get the settings I need, or to try and find whatever was not installed, etc.

I will be using the net at work a lot next week. I would prefer to do the work in Ubuntu, but if you folow the link in my OP, you will see that I cannot access the WiFi at work on this computer from Ubuntu. So I will have to use the XP partition and do my work.

One day when I have to time to do a clean install I will do that and if I can get the WiFi to work, I will do away with XP.

Thanks

Robi

---

### Post by ratcheer on 2010-01-24
Never mind.

---

### Post by KegHead on 2010-01-24
very easy.

---


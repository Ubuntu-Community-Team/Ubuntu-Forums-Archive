---
title: "Installing Ubuntu 10"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by markymark64 on 2011-04-11
Ok, let me give you some basics first.

I have a second hard drive that I have set aside with a partition for ubuntu. That partition has about 200 GB of space. I want to dual boot between Windows and Ubuntu.

I've read on other forums that you should have two partitions for ubuntu so that if one partition gets corrupted you always have the other to trouble shoot from.

I have an AMD 64 pc and have 4 GB of memory.

Since I want to do a dual boot but would like to use the partition I've set aside, how would I proceed? Do I need to repartition this drive so that a small part of is is used for the loader?

I am brand new to ubuntu and linux and don't want to screw up my system which is why I have set aside this second partition.

Oh, and when I try to install I get the infamous message "no root file system is defined. plese correct this from the partitioning menu. I believe I just need to change the partition.

Oh, and did I mention that I've already formatted my 200 gb partition as ext 3? I did this so that I could easily recognize and select it.

I realize my plea for help probably seems jumbled but I'm hoping you can make sense of it. 
 

If anyone can help me I would greatly appreciate it. I need to know if I should repartition this 200gb so that one smaller partition holds the swap file. If so, will Ubuntu take this partition that I specify and format it accordingly or do I need to decrease the size so that it will create a second partition that I can use for my swap file?

---

### Post by TeoBigusGeekus on 2011-04-11
Boot up with the installation cd.
The installation is pretty straight forward (use small caps for your user name and choose a good password). The only part to which you should pay a bit more attention is the partitioner.
When you reach it, select manual partitioning.
Select your 200gb drive, right click it and create 3 partitions:
1)Swap partition: ~1gb
2)Root partition: ~20gb (as you've got plenty of space). Format:ext4, Mount point: /.
This is where your system is going to be installed. 
> no root file system is defined
You've probably forgotten to set the mount point on your first attempt.
3)Home partition: The rest of your hd. Format:ext4, Mount point: /home.
This is where your user settings will be held. It's useful to have a separate home partition: in case of a reinstallation, you can keep the same home partition and salvage all your settings/tweaks.

---

### Post by markymark64 on 2011-04-11
Teo, thanks for your message but I'm still stuck. I want to install ubuntu alongside windows but when I go through the installer I get two usable options: install alongside windows or manually choose partitions. If I choose the windows option I then have to choose advanced. When I right-click on the partition I only get an option to change the partition. Is this what you were speaking about?

---

### Post by TeoBigusGeekus on 2011-04-11
No, I meant manually choose partitions.

---

### Post by markymark64 on 2011-04-11
I think I may need to use another partitioning product to create these partitions in first because Ubuntu isn't giving me the options required to split this one partition into 3 like you recommended. I'll try paragon first since I have a licensed product and see if that will get me up and running.

---

### Post by markymark64 on 2011-04-12
Teo, you da man. If you lived closer to me I'd give you a great, big bear hug. Thanks for your help m8. I got everything working fine including audio and video playback. Woot woot. Now if I could find a legit driver for my printer I'd be in ubuntu heaven. Oh well, I am downloading vmware player so maybe I can install my printer on a virtual drive and use it from their. Time will tell. Anyway, thanks again for your help. I really appreciate it especially since I've been struggling for two days to get ubuntu installed.

---

### Post by TeoBigusGeekus on 2011-04-12
> **markymark64 said:**
> Teo, you da man. If you lived closer to me I'd give you a great, big bear hug. 

A cheque would be fine ... :biggrin:

---

### Post by mastablasta on 2011-04-12
post in a separate post about your printer issue. make sure you give the correct printer name, model... as much data as possible. perhaps driver is easier to find than you think.

---


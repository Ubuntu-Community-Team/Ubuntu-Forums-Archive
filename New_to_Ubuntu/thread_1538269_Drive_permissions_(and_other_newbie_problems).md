---
title: "Drive permissions (and other newbie problems)"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by L2U2K2E on 2010-07-24
Hello, I am a long time windows user and recently made the jump from vista to ubuntu 10.04 (32 bit). I am running on a MSI GX630 laptop and mostly things seem to be going great, I have a few problems I can't seem to figure out though. any advice at all (even unrelated tips for a newbie) would be appreciated.

1. First, I do plan to put vista back onto my laptop at some point, so I made 2 partitions and left enough space to clone my vista file back on when I need to. The problem is that I have my normal ubuntu partition and then I created a second partition for my data formatted ext4). This big partition is totally empty, and when I try to copy files into it from my external hard drive I am told, *"The folder "X" cannot be copied because you do not have permissions to create it in the destination"*. 
     My first thought was to look under properties->permissions, and sure enough the owner of the file is root. also, at the bottom of the page it very clearly states *"You are not the owner, so you cannot change these permissions"*
I'm stumped, what do I do?


2. Second question is more of an opinion poll. What do you use to play/organize music? I find myself missing winamp, and rythmbox seems mediocre at best.


3. I have an AMD64 CPU but I am running the 32 bit version of ubuntu. should I use the 64bit instead? I use my computer mostly for video, music, Internet and word processing.


4. Ubuntu runs on GNOME (right?). I don't know if I fully understand the difference between this and KDE, but I heard you can boot with KDE even in ubuntu. is this true? how?


5. If I move vista back onto my laptop what do I need to do to set up a dual-boot?


6. I had planned to have my data set up on a second partition from my ubuntu install so that I can also access my data from windows if I need to. Is this a good/bad idea? also, is it possible to change the shortcuts in the "places" menu (and other shortcuts) to direct to this secondary partition rather than the operating system partition?


7. Last, My laptop seems to be running really hot for one reason or another. I'm fairly confused about this. any ideas?


thank you in advance for having patience with me  :]

---

### Post by MooPi on 2010-07-24
You may want to address each of your issues in separate posts, as all of them together kinda overwhelm. I'd like to address your hard drive problem. You can move and copy files to the partition by tempoarily becoming root with either gksu or sudo. This is slightly bothersome. My solution would be to create a folder in media and make certain that you are the owner. In terminal ```
sudo mkdir /media/folder2Bnamed
```
```
sudo chown -R yourname  /media/folder2Bnamed
```
Edit fstab so that the drive mounts on the new folder. Start the edit process by getting some info. In terminal ```
sudo blkid
```This will list the UUID for all drives and partitions. Find the partition in question and add the UUID info to a line to /etc/fstab. This is a similar partition scenario from my computer.First my UUID info: ```
/dev/sda3: LABEL="BigBin" UUID="819005e9-fd37-4f2a-91ef-162b7fe9e400" TYPE="ext3"
``` Then my fstab file:
```
# BigBin /dev/sda3
UUID=819005e9-fd37-4f2a-91ef-162b7fe9e400 /media/BigBin ext3 defaults 0 0
```

---

### Post by L2U2K2E on 2010-07-24
That was kinda over my head, but I think I figured it out. however, the file "/ect/fstab" is also owned by root and I can't edit it. same problem...   :/

---

### Post by MooPi on 2010-07-25
Sorry should have included that you need to be in sudo or gksu to edit fstab. ```
gksu gedit /etc/fstab
```

---

### Post by Anuovis on 2010-07-25
> **L2U2K2E said:**
> 
1. The problem is that I have my normal ubuntu partition and then I created a second partition for my data formatted ext4). This big partition is totally empty, and when I try to copy files into it from my external hard drive I am told, *"The folder "X" cannot be copied because you do not have permissions to create it in the destination"*. 


You could also try opening the terminal and typing:
```
gksudo nautilus
```This will open your file manager as root. Maybe you will be able to change the permissions then. I think I did something similar when I had some problems with permissions. This is a simple way, you might need something more sophisticated. But never hurts to try.

Another thing though, I am not sure whether Vista can read ext4 systems. XP could ext2 and ext3 if you installed some additional drivers but that was slow and painful. You might consider making the shared partition into NTFS to be accessible from both systems. Search for more info about this.


     > 2. Second question is more of an opinion poll. What do you use to play/organize music? I find myself missing winamp, and rythmbox seems mediocre at best.I like Exaile. You might also try Banshee or maybe Amarok. Amarok seems to be liked by many, it is not a native Gnome app but can run nonetheless. You can find all of them in *Ubuntu Software Center*.


> 4. Ubuntu runs on GNOME (right?). I don't know if I fully understand the difference between this and KDE, but I heard you can boot with KDE even in ubuntu. is this true? how?Yes, it is true. Gnome and KDE are just graphical environments that run on the top of the same Ubuntu system. You will be able to choose one or the other at the login  screen. 

Check this link out: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
It also has many other tutorials for beginners.

> 
5. If I move vista back onto my laptop what do I need to do to set up a dual-boot?There are many tutorials about this, check the above psychocats and google some more. Different ways of doing this are possible, some of them don't require a dual-boot (like using a virtual machine).

---


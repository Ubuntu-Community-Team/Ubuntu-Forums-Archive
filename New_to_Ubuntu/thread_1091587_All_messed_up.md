---
title: "All messed up"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by BJH44 on 2009-03-09
I had a slow and old Dell desktop that had XP and I installed Ubuntu also and liked it. I removed the HD and put it in a faster HP. Problem is; it want boot. Dell will not let it work on the HP. I get nothing except "can't find OS". I don't want to format and loose all my windows stuff. I have Ubuntu on another HD and that is what I'm using now. I have the XP-Ubuntu HD set as a slave, but don't know to with it. I can see the old Hd under my computer, but it shows 40gb(empty).  Any idea on how to start this thing up. Thanks.

---

### Post by avtolle on 2009-03-09
No hardware expert am I; wondering if there needed to be something changed in the BIOS so the new HDD is recognized?

---

### Post by Bölvaður on 2009-03-09
1. please have more descriptive title of your threads, "all messed up" is as good description of a very hungry gorilla as it is to your problem. This will be the last ill titled thread I will visit ;)


If I get you right you removed the original hard disk drive where you had xp and ubuntu and replaced it with an empty one, am I correct?
If so then I would suggest to you to put it back in.

If you just added the new hdd then you must put the original as master (if it is connected via ata cable, if it is sata I belief there should be no problem regarding this).

Can you give us more detailed description on where the hdds used to be and where they are now, in a very clear manner.

---

### Post by bailbath on 2009-03-09
Or put a live Ubuntu cd in and use it to install to the new hard drive.
Or If you want to put xp back as well use the xp cd first then the ubuntu cd after you have fully installed windows.
Ian

---

### Post by lindsay7 on 2009-03-09
If I understand you, you had a computer with a working hard drive that was used a the boot hd for the system. If you take that out of that computer and put it into another computer, the chances that it will boot are very unlikely.  Why? Because that hard drive is configured for the bios and hardware of the original machine. There is a remote chance that it will boot in a new machine, but it will be messed up a best. The only time I have had any success doing this is when I moved it over to another computer with the same or very similar motherboard and that was still a problem. 

If you put the drive with your os and other data in a new machine, if it is configured so that it is not the boot hd, you should be able to see and access the data on it.  That is going to be about all you can do with it. At some point you can format that drive and use it for whatever you want.

---

### Post by BJH44 on 2009-03-09
1. All the info you ask for is my first post. I took the IDE HD that was in a dell and installed it in a HP. The HD had XP and Ubuntu installed on it. It would not boot in the HP because dell installs something in the bio's that want allow there HD to work in another system. Now I have Ubuntu on a new HD which is working and the old XP-Ubuntu HD as a slave. Yes the new one is the master and old one is the slave. The master and slave shows up in my bio's (HP) and on the ubuntu Computer. Hope this is clear enough for you.

2. If you noticed, I posted as a new beginner and was asking for help. This is a help forum isn't it? What difference does the title make any way. It wasn't suppose to be a novel.
You, my sarcastic, smart mouth friend, doesn't ever have to read my post again. As a matter of fact please DON'T. If there is anyone on this forum that has the desire to help, wonderful, if not, I will go back to Windows.
I have been on Win. forums hundreds of times and never came across a smart mouth such as you. 

Mr administrator, I apologize for this out burst and if you want to band me from this forum, I understand.

---

### Post by BJH44 on 2009-03-09
Thanks for all others that replied as to help someone.

---

### Post by jerome1232 on 2009-03-09
A title is where you have a few choice words to attract the right kind of help. I will browse these forums looking for title I think I can help with, one's titled "need help here" or "all messed up" for the most part get skipped over because I can't tell from the title what's going on. For example "Switched Hard Drives and laptop says no os" for  example might've been a better choice.

Your problem is there is no Os on your second hard disk drive, you would need to install your OS onto the new hard drive or another solution would be to clone the old drive to the new drive and then resize your partitions to fit the new disk.

---

### Post by bailbath on 2009-03-09
You know we are all here to help you free of charge but it would help us to help you if you put a descriptive title. We are a community and we need rules so sorry if the guy upset you but he was only trying to help you and us. If everyone used a descriptive title it would be great, that won't happen but maybe next time you will!
Oh and I don't care if you go back to windows or stay with Linux that's up to you.
Ian

---

### Post by BJH44 on 2009-03-09
With the attitude most of you have on here, that will probably happen. Your expert from Iceland could have said; IF you would please use a better title description, we could probably help you more. Instead of chewing me out like he did. All the years past, me and thousands more sometime leave titles like that. No one has ever been so upset as you people are. If there is a post, must need help,uh.

---

### Post by BJH44 on 2009-03-09
> **jerome1232 said:**
> A title is where you have a few choice words to attract the right kind of help. I will browse these forums looking for title I think I can help with, one's titled "need help here" or "all messed up" for the most part get skipped over because I can't tell from the title what's going on. For example "Switched Hard Drives and laptop says no os" for  example might've been a better choice.

Your problem is there is no Os on your second hard disk drive, you would need to install your OS onto the new hard drive or another solution would be to clone the old drive to the new drive and then resize your partitions to fit the new disk.

You can go to Computer in ubuntu and find the slave HD with all my files and folders including XP and Ubuntu.

---

### Post by bailbath on 2009-03-09
> **Bölvaður said:**
> 1. please have more descriptive title of your threads, "all messed up" is as good description of a very hungry gorilla as it is to your problem. This will be the last ill titled thread I will visit ;)

 This is what he said it's a shame you did not take it in the humour it was obviously used. PC's are full of chips it's a shame you managed to get one on your shoulder!
So that's two people who were prepared to help you and are not going to now!
Ian

---

### Post by hyper_ch on 2009-03-09
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Bölvaður on 2009-03-10
What a disaster of a thread, I was expecting this to been solved within an hour.
So here is my solution (with no humour at all this time)


The problem can be identified with more detailed about the computers (not going to ask for it though).

Let's begin with the solution:

1. Insert an live cd into the cd drive and copy all the data you want to save onto a removable hdd.
After taking backups you should first install xp and then ubuntu. After that process you can safely copy the data back to the hdd on the HP computer. Then move the hdd back into the HP computer.
After taking backups you should first install xp and then ubuntu. After that process you can safely copy the data back to the hdd on the HP computer.

or
2. Move the hdd back into the old computer and take backups of all the data you wish to keep.
After taking backups you should first install xp and then ubuntu. After that process you can safely copy the data back to the hdd on the HP computer.


Plausible problems:

- Different CPU architecture (32 bit, 64 bit)
- OSes are not set up for the current hardware (this may lead to halt in boot up)
- RAID (I do not know exactly how this may affect you, perhaps your hdd is set up with some special RAID and the HP computer doesnt get it)
- A very hungry gorilla is living in the BIOS. (feed him (his name is Joe) some bananas) &#8592; this is not a joke ;);) (yes it is)

---

### Post by upchucky on 2009-03-10
Ok lets give the gorrilla a banana and a good kick and try to get this back on track.

if any hdd will boot, boot it then download this,

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh

```

post the results here.

if neither hdd will boot then boot using the live cd, then do the above.

also you can use knoppix to find/edit files such as menu.lst needed to boot, and advanced supergrub disk to fix the master boot loader.

In future, everyone here offers help on a friendly basis, no one is obligated to do anything, but they all choose to try.

I too am known to skip over posts that are not titled a bit effectively, simply because it indicates to me that the poster has not read the instructions for posting, and that usually indicates that the poster is not gonna follow or read instructions either, this save me time and effort in trying to respond to someone who will not listen, time is better spent in helping those that are really trying.

With all due respect, we all mean well

good luck.

---

### Post by tarps87 on 2009-03-10
HP or Dell should not lock the hard drives and it could be a cable select issue or the MBR not being read properly, if both of these are correct and working you can use the new install to boot xp of the old hard drive. Bare in mind that changing xp from on machine to the other may not work due to it only having the drivers from the dell installed.
You should be able to boot the xp partition using the grub settings on the first/new hard drive. If you want to set this up please post the output of ```
sudo fdisk -l
```
and also the file /boot/grub/menu.lst on the old dell hard drive.

There are a few things you should bare in mind when using this form:

Everyone here is a volunteer and are therefore not paid so helping out by using descriptive titles just makes it easier for everyone.

For a lot of members here English is not their first language so things that you may see a harsh/sarcastic may not be meant in that way. Also some thing may be said/meant in good humour but may not read that way.

---


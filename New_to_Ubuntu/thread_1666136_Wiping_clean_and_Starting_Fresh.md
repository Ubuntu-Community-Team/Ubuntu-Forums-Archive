---
title: "Wiping clean and Starting Fresh"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by groover on 2011-01-13
Hi, 
I've been working with Ubuntu since last October and I really do like it. 
I'm ready to take the plunge and take Windows off of my hard drive and run solely linux. I've been having trouble with the sound on my computer in Ubuntu and I figured it'd give me an excuse to do what I've been needing to for a long time- clean up the computer and start absolutely fresh. 
 
My computer is relatively old and I've been a big fan of the things I've seen about UberStudent "flavor" of Ubuntu. I'm a student and I like all of the gizmos that come pre-attached. 
 
I just bought a new harddrive last night to back up all of my data and and files on. Ive backed up my school documents, pictures, and music. 
 
My question is this:
What is the best plan of action? I plan to download a DVD install of the UberStudent. How should I go about ripping Windows out or can I format the harddrive in the Install? What about undoing partitions/deleting partitions? Are there any other documents I need saved on an external harddrive before I format the harddrive?

---

### Post by 0N3 on 2011-01-13
I would go with a fresh install but i'd partition my HD in 3 partitions

/(root)
/home
and a swap partition

/(root) ideally 10GB
swap roughly 2-3GB
and /home the rest of the partition
that way when you have to do fresh install all your pics, music & docs will be stored in your home partition and always will be there and all your settings remembered even if you do a fresh install later on as you dont format the /home partition.

---

### Post by candtalan on 2011-01-13
Welcome!
If you are still configuring audio on your PC in Ubuntu I would suggest a little caution before a full jump, but it is your choice of course. It would be logical to get audio really sorted out, and also to be in a situation where you really know that you have not *used* Windows for xx time period and so you will then be confident in getting rid of it. In my case, and I was desperate to loose Windows, that took quite a while.
keep in mind the facility of both ubuntu one and also such as dropbox for off site storage of some chosen fils. One backup of data is  not really enough if it is important, you need at least two.

One possible and easy approach might be to consider just retaining your old hard drive after data backup anyway, and use only a new hard drive in the PC, and just install Ubuntu into that to 'take over the whole drive'.

With an older PC note that the amount of RAM is probably more important than anything  to help it run well.

I have not tried uberstudent myself, but it is very likely to include an install option 'to take over the whole drive'. If it is a live CD do test that first. If when testing live CD you have the chance to check the DVD for defects (or use md5 facility in various ways) do take effort to do that. An iso image burn is more sensitive to errors than usual CD writes.

hth

---

### Post by groover on 2011-01-13
Let me see if I can understand this. 
 
1) It would be wiser to partition into three parts: one for files (as well as my backup external), one for the operating system and one for...?
 
2) Windows issue- I've got Vista and I've had it for about two years- It's just slow and I'm not a big fan of it. I've enjoyed using Ubuntu and if I change my mind I'll just grab a cheap student copy of Windows 7. 
 
3) Sound issues-- My sound card is connected and the sound works on the Windows partition-- I've messed with some sound thingy somewhere and I don't quite know what I did.

---

### Post by 0N3 on 2011-01-13
Yes it would be wiser to partition into 3 as you said7

1) /(root) for your programs ect....
2) /home for your settings, music, pics ect....
3) swap area if your pc needs extra memory

---

### Post by hansolo4949 on 2011-01-13
I think you should:

1. completely format the hdd (if you're SURE you want to get rid of windows)

2.Install Ubuntu using the normal settings.

3.If you get OSick:D for Windows, just pick up a copy of windows 7 (like you said) and run it on a VM if you're computer is fast enough. I use Windows 7 and Ubuntu, and I do have to say Microsoft did a pretty good job on Windows 7 (although it's mor bloated than ever).

4. Optional: create a "backup" partition on your HDD so that if Ubuntu messes up, you'll still have your files on the HDD, you'll just have to reinstall Ubuntu


hansolo4949

---

### Post by groover on 2011-01-13
Hm. Well maybe I shouldbacktrack a second then. 
 
I can keep both the partitions. I really would like a new flavor of linux, preferably the UberStudent-- Should I just uninstall Ubuntu and replace it with UberStudent? How would I go about doing that?

---

### Post by groover on 2011-01-13
So, can I just delete the old partition? or upon bootup of the new operating system, should I choose to reformat a bit of my partition?

---

### Post by 0N3 on 2011-01-13
Reformat it all and break it into 3 partitions

---


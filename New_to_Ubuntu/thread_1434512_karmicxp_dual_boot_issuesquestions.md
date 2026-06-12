---
title: "karmic/xp dual boot issues/questions"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by stevek123 on 2010-03-20
I searched & read the most recent threads and didnt find answers...
long...sorry...
I use older equip. I'm fairly noob at Ubuntu but have successfully 'built/made' several programs I use - HA = need to rebuild my sound drivers with every kernel update. I'm pretty unfamiliar with command codes - usually using cut/paste from good threads. I run Hardy (ran Gutsy and upgraded to Hardy... for Ubuntu experience perspective) & have an XP machine all virused out and unused - ready for use as parts- set up as a network. 

I just got a 'new' hand-me-down 2.8Ghz dual core 2MB machine & would like to setup XP/Karmic dual boot. The XP OS will NOT be attached to the internet - but I'd like to have it so I can access my mp3 player (the Rockbox hack for mine to Ubuntu is still not done...) plus there are a few printing options M$ offers that are sweet. I understand the new Karmic/ext4 file system will not be inter-compatible with XP. 

grrr...how to describe current setup... one HD = /dev/sda1 = ext3 = Hardy OS + dev/sda2 = extended incl dev/sda5 = linux swap   AND 2nd HD is /sdb1 = ext3 = my home folder + dev/sdb2 is a linux swap.

Questions:
Will my current Hardy be able to share/network with Karmic?

Can I install Karmic using ext3 instead of 4 so that it will be compatible with XP & Hardy? [I assume that Karmic w/ ext4 will be able to handle the older file systems but not the reverse]. If I can do this, what features would I lose from Karmic (if any)?

I suspect a new 'shared' partition using ext3 would solve some of these issues but dont know how to set one up with Karmic...Do I just install Karmic OS & swap on 2 partitions with ext4 and make my 'home' another/3rd partition with ext3? Can I do this directly from custom install? or can/do I need to reform 'home' as ext3 after the install? 

Sorry folks - just trying to wrap my head around this & any advice is welcome.

---

### Post by mikewhatever on 2010-03-21
Right, I am going to break it down to make easier to read and a bit less messy.
> **stevek123 said:**
> ...

I just got a 'new' hand-me-down 2.8Ghz dual core 2MB machine & would like to setup XP/Karmic dual boot. The XP OS will NOT be attached to the internet - but I'd like to have it so I can access my mp3 player (the Rockbox hack for mine to Ubuntu is still not done...) plus there are a few printing options M$ offers that are sweet. I understand the new Karmic/ext4 file system will not be inter-compatible with XP. 

grrr...how to describe current setup... one HD = /dev/sda1 = ext3 = Hardy OS + dev/sda2 = extended incl dev/sda5 = linux swap   AND 2nd HD is /sdb1 = ext3 = my home folder + dev/sdb2 is a linux swap.

So the new machine has it's own hard disk you are going to install to, right? Didn't want to guess, but if that's the case, what does your current setup matter?


> Will my current Hardy be able to share/network with Karmic?
Yes.

> Can I install Karmic using ext3 instead of 4 so that it will be compatible with XP & Hardy?
Yes. The default file system is ext4, but all the rest, ext2, ext3, etc, are still available. 

> If I can do this, what features would I lose from Karmic (if any)?
None. Some tests show faster read/write speeds for ext4. I didn't notice.

> I suspect a new 'shared' partition using ext3 would solve some of these issues but dont know how to set one up with Karmic...Do I just install Karmic OS & swap on 2 partitions with ext4 and make my 'home' another/3rd partition with ext3? Can I do this directly from custom install? or can/do I need to reform 'home' as ext3 after the install? 

What issues are you talking about? Generally speaking, you can create any partition you want using custom/manual partitioning (not custom install), in fact, you'll have to anyway, in order to specify the ext3 file system.

---

### Post by stevek123 on 2010-03-21
Thanks for reply Mike
Yes - new machine will get all new setup. I'd like it to be XP/Karmic dual boot. This machine will be networked thru router to the Hardy machine. Most of the comp use in our house will run thru the Karmic OS - therefore in whatever filesys it is setup with. I want the XP available for several specific apps.

I guess I'm unfamiliar with the use of a new file system. My concern/issue is that the Hardy machine (downstairs) and the XP OS will be able to utilize the files stored in Karmic with ext4. If neither of these OS will work fluidly with ext4 filed data - then I want/need it setup as ext3. It sounds logical and easy enough to do but I was looking for confirmation that it is the right thing to do.

---

### Post by mikewhatever on 2010-03-22
I don't think Hardy has any support for ext4, let alone XP, so you are right, ext3 is the best choice. That said, if your goal is to share files over the network (samba), I don't think the local file system matters much.

> Most of the comp use in our house will run thru the Karmic OS - therefore in whatever filesys it is setup with.

Wouldn't it be better to get all computers connected through the router? In either case, the local file system wouldn't matter.

---

### Post by stevek123 on 2010-03-23
winXP is not networked to Karmic = just a dual boot instead of karmic, but I'll need those files - espec the mp3s.... going to go with the ext3. Should be fine. Thanks.

---


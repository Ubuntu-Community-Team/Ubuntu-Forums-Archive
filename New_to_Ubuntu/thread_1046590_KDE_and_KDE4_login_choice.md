---
title: "KDE and KDE4 login choice"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Bruv on 2009-01-21
I am finally duel booting XP and Kubuntu, my first time to use Linux seriously.
I have installed two desktop environments by mistake, I now have KDE and KDE4 at log in.
KDE4 has next to no applications installed, but is slower to load than KDE which I have had installed for about two weeks.

I would like to use KDE4 and dump the option of KDE. I have tried to re-install to tidy up everything, and start from scratch, but don't see the windows partition when I tried to re-install, it is either showing just the kubuntu partition or is giving me the option to over write the windows section which I want to keep for others who use the PC.
When using KDE I have duplicate applications, such as Dolphin and Terminal as has KDE4,

Is there anyway I can delete these duplicated applications, and desktops safely ?
I would even settle for sticking to the original set up with just KDE, the way it is at the moment must mean a waste of resources.
I know next to nothing, so be gentle with me.

---

### Post by mjheagle8 on 2009-01-21
when you install, you'll want to choose manual so you can select what partitions should be used for what.

---

### Post by Bruv on 2009-01-21
That is part of the problem, when I installed first time I used 'guided' and have no idea what it used.
I have tried to get my head around the terms / var bin etc.etc. and I have no idea what I am looking at when the disk is shown during the partitioning sequence, afraid to loose the entire disk to Kubuntu, and causing a riot in the house.

---

### Post by mjheagle8 on 2009-01-21
ubuntu defaults to one partition. you will be able to tell which partition is the windows partition because it will be formatted as NTFS.  just make sure you dont check the format box next to that partition. you'll specify the other (ext3 or 4) partition to be mounted as '/' if you dont want to do any more complex partitioning.  
google it and you should be able to find an article explaining more to you.

---

### Post by Bruv on 2009-01-21
A little more patience please.
I have googled and found lots of information, but I need someone to hold my hand through this.
I have gone for the re-install and come across this display when choosing what to do next.
The partitioning options are as follows.....

It shows a coloured bar across the top and the description going down the page.

/dev/sda with nothing following
/dev/sda 1 NTFS size 47073 MB Used 24900 MB
/dev/sda7 Ext3 size 31116 MB  Used 3800 MB
/dev/sda 8 swap size 1348 MB Used 0 MB
/dex/sda ext3 size 394 MB Used 394 MB
/dev/sda swap  size 90 MB  Used 0 MB

I tried to tick the first box after NTFS but apart from some activity from the CD drive no tick appeared.

Am I being over cautious ?
Is that the correct display for what I have explained in my first post ?

---

### Post by mjheagle8 on 2009-01-21
you dont want to check the box next to windows! that will reformat it. you do NOT want to do anything to the NTFS partition.  you can delete the ext3 and swap partitions, then create a new swap partition and a new ext3 partition with mount point '/' in the freed space.  
do NOT reformat the windows partition, that would cause you to lose all your data.
also, i forgot this before: BACKUP ANY CRITICAL DATA before editing anything with your partitions.

---

### Post by Bruv on 2009-01-22
After a torrid time the job is done.
I had major problems understanding what was happening.
I tried to delete free space, expecting the adjacent space to fill it, but a new partition was created everytime.
I ended up deleting, and expanding the sections until continuing when the system told me certain sections were not large enough.
I don't really know what I have done to be honest, but everything seems to be working alright.

Thanks for the helping hand.

I know at some stage it will click inside my head,and I will be able to understand how this all works....hopefully sooner rather than later.

---

### Post by mjheagle8 on 2009-01-22
did you eventually get iti working? if not i can try and help more.

---

### Post by Bruv on 2009-01-22
> **mjheagle8 said:**
> did you eventually get iti working? if not i can try and help more.


Good question, the answer is yes and no.
I eventually re-installed kubuntu and posted the post above.
Closed the browser and took the option of updateing.
After updating and before rebooting as it said I should, another window offered to upgrade to jaunty antelope or something.......grrrr....and that is what I did.
It took forever, after the long wait, at the prompt I rebooted.
It only got to the pre-log screen. A grey swirling pattern with the pulsing cursor which stopped pulsing, then the pattern disintegrated leaving a frozen distorted rash of bars across the screen.
I rebooted and tried again, same thing, I took the other option, there appears to be two versions of kubuntu apart from XP so I went with the second version, no I tell a lie, I first tried recovery mode.....then went for the other version.


To cut a long story short....I am now in XP....and considering.......yet another re-install.

I will get it right......maybe.

---


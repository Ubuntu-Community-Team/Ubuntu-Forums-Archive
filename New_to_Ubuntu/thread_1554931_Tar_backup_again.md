---
title: "Tar backup again"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by BobJam on 2010-08-17
I had previously posted [here]("http://ubuntuforums.org/showpost.php?p=9715782&postcount=13"), but I think it was too buried to get a response.  Please read that whole thread (13 posts) to get the flavor of what I'm asking.  Essentially, I'm "bumping" my last post there.

(My problem, detailed in the buried post linked to above, is that I have a separate partition for my /home directory, and my tar backup incorporated both my / and my /home on the same file  and when I restored it, both / and /home were restored to the same partition.)

I want to make a backup (backups?) that when restored will place my /home on it's own partition.  I want to upgrade to 10.04 LTS (from 9.10) but I don't want to do it unless I have a backup via the tar method shown [here]("http://ubuntuforums.org/showpost.php?p=208854&postcount=69") (I think . . . which is why I'm asking this question) . . . in case the upgrade goes south.

---

### Post by jonnywombat on 2010-08-17
I think i must be missing something here but why would you be worried about backing up during update?

The update procedure will not touch anything on your /home partition, and even in the unlikely event that something did go horribly wrong your /home partition would still be intact and accessible from a live cd...

if your / partition gets borked during the upgrade then just have a ubuntu disk handy and do a fresh install, the end result would be the same. you can use your same /home partition and all your settings/documents/music etc will still be there....

---

### Post by BobJam on 2010-08-17
I think I understand what you're saying relative to the update (maybe I should have left that part out as my reason), but I want the backup(s) not only for that but for just flat out having available for things going south for other reasons (like 'sperimenting with my desktop, which a lot of us novices do).

And, your explanation brings to mind another question that I've had for some time.

If I restore / using a liveCD, won't it be missing some of the apps that I have added?  For example, I have gkrellm.  As I understand it, my personal settings for gkrellm (in this example) are indeed on my /home directory.  But wouldn't the guts of that program be on /???

So, I'd have to add all the programs I've added since I installed the first time . . . which is quite a few programs.  A backup of / solves that problem, doesn't it?

In any case, I think I understand what you're saying about the upgrade, but my reasons are more global (as I said, I probably shouldn't have used that as my reason alone).

---

### Post by jonnywombat on 2010-08-17
your right that a fresh install of a cd will not have all your apps included, you will have to add them manually afterwards. I use this method when I break things, I can't see it being any more time consuming than creating a disc image, and restoring. 

For your back up needs why don't you try a tool designed for that purpose such as [remastersys]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") or clonezilla. I have no experience using these tools, but gotta be worth a look]

hth

---

### Post by BobJam on 2010-08-24
Thoughts on my main question of how to do a backup and restore so that my / and /home will be mounted on different partitions (for details of my question see the first link in my OP)?

(BTW, jonnywombat, I tried all the alternative backup/restore methods . . . partitionmagic, clonezilla, rsync. etc. and much prefer the manual tar method I linked to at the bottom of my OP.  And also, reinstalling all my apps because I restored / from a LiveCD IS a lot more tedious than just flat out restoring from a full backup . . . for me anyway . . . I just went through that, and could have saved an entire day if I had had a / backup)

---


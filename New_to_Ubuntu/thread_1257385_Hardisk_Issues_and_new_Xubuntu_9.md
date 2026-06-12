---
title: "Hardisk Issues and new Xubuntu 9"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by SheaMan on 2009-09-03
I am a complete GNU / Linux beginner. I have skimmed through the beginnier stickies here and I am either missing or not finding the information I am looking for. 

I have an IBM "Thinkpad 600X" P3 with a brand new installation of xunbuntu 9.04 (xfce 4.4) and I know for certain that there are some hard drive problems with this machine. There is no windows remaining. I have not installed any of the updates yet because I want to try and look into scanning the HD with something so that the bad sectors don't interfere with the installation any more than what may or may not have happened with the initial install. 

I checked the help and it said to install a program - umm Janitor something. A friend of mine told me to boot from the install cd and run a fsck? something like that. I am going to read more and check back later.

--- edit

Hey! thanks for all the help - for anyone finding this thread in a search there is some great advice and links to using FSCK in this thread!

---

### Post by Paqman on 2009-09-03
You might also want to try Palimpsest, you can get it from System > Admin > Synaptic Package Manager. If you've got SMART enabled on your drive/BIOS then Palimpsest should be able to tell you exactly how many bad sectors you have, and whether they've been remapped. As long as you don't have a lot of unreallocated bad sectors then your drive is ok. The drive manufacturer will also have diagnostic tools available on their site, although some of these may require Windows.

---

### Post by SheaMan on 2009-09-04
Hrm.. you mean the add/remove programs at the top of the applications pile?

I cant make hide nor hair of this here Synaptic Accelerator or whatchacallit.

[IMG]http://i9.photobucket.com/albums/a64/sreinke/synaptic.png[/IMG]

Does mine look like its supposed to? Also... any good resource on how to use this Fsck program - that and is it really all that important to boot from the CD - because that doesn't seem to want to happen.

---

### Post by Paqman on 2009-09-04
> **SheaMan said:**
> 
Does mine look like its supposed to? Also... any good resource on how to use this Fsck program - that and is it really all that important to boot from the CD - because that doesn't seem to want to happen.

Sorry, my fault. That software isn't in the repositories for Jaunty so you can't install it. It'll be well worth while having a play about with Synaptic. It's the main way to install software in Ubuntu. If you're finding it confusing there's a simpler alternative at Applications > Add/Remove.

As for fsck, Google is your friend, or search these forums. Re the CD: yes, it's vital. You don't want to ever use it on a filesystem that's in use (aka "mounted"), the LiveCD doesn't mount any of your partitions (except swap) by default, so it's safe to use fsck.

Take a look at this thread about [bad sectors]("http://ubuntuforums.org/showthread.php?t=309822").

---

### Post by SheaMan on 2009-09-04
what about "[B]$ sudo shutdown -F -h now"

would that work? I don't want to "blindly run commands" but it sounds like what I want to do. Weird things happen when I try and boot from the CD - I don't think that is going to work. 
[/B]

---

### Post by Paqman on 2009-09-04
> **SheaMan said:**
> what about "sudo shutdown -F -h now"


I'm thinking that would just run fsck with it's default settings. Can't hurt though. Incidentally, the automatic disk check that Ubuntu does every 30 boots or so is fsck, you may have noticed it already.

> 
Weird things happen when I try and boot from the CD - I don't think that is going to work. 


What sort of "weird things"? You have to have whatever filesystem you're fsck-ing unmounted. Hence why the LiveCD is recommended.

---

### Post by SheaMan on 2009-09-04
OK, well

I have two copies of the "livecd" both burned. When I try to load from the cd it usually freezes. Somehow this time it worked and I am now booted from the CD. 

I am somewhat concerned that when I shut down normally I return with a screen that says 
"[number, number] System Halted." Do you know what that means? is it normal?

Also ... I booted into the livecd and opened terminal and tried "fsck" and it just returned a version number? There are some parameters I need for this command line thing arn't there. Should I try the Sudo thing from the bad sectors thread?

(thanks for the Help Paqman - I really appreciate it)

---

### Post by kerry_s on 2009-09-04
don't worry about all that, when you format it, bad sectors will be marked and not used. your thinking about it to hard just install and see how it go's. it's easier to deal with problems in a install, live is not the same thing.

---

### Post by Paqman on 2009-09-05
> **SheaMan said:**
> 
Also ... I booted into the livecd and opened terminal and tried "fsck" and it just returned a version number? There are some parameters I need for this command line thing arn't there. Should I try the Sudo thing from the bad sectors thread?


There are indeed parameters, [a great many]("http://linux.about.com/od/commands/l/blcmdl8_e2fsck.htm") in fact. You're probably most interested in the -c option though, as that'll do a non-destuctive read test for bad blocks. For example:
```
e2fsck -c /dev/sda1
```

---

### Post by SheaMan on 2009-09-05
arg. My windows mentality.. I mean I know abit about the windows registry and can msconfig with the best of them, but this command line thing is killing me. 

Ok, the whole story. I installed ubuntu because my system is too archaic to effectively run windows xp. I am superstitiously unwilling to roll back to ME or 98. So pal burns copy of Xubuntu. I install. All manner of catastrophy and uncaptured error messages proceed to occure. So I re-installed xubuntu from scratch and gave it the entire hard drive. 

I know that there are hard drive problems and they caused some form of problem with the initial install. I really want to use the hard drive fixing and bad sector identification system for xubuntu, but the command line thing is killing me. At some point in the last few days (on the first xubuntu install) fsck happened automatically ... and repaired several things. So I am certain that I can get some good out of running it... I just don't know how to do that. Can you direct me to a thread or site that has a "terminal beginner's how to fsck?" or maybe an application that does disk maintenance?

---

### Post by kerry_s on 2009-09-05
chances are your going to need a new drive. you might also have to go even lighter than xubuntu, has anything been upgraded from the stock?

[http://www.thinkwiki.org/wiki/Category:600X](http://www.thinkwiki.org/wiki/Category:600X)

---

### Post by SheaMan on 2009-09-05
The only thing I know has been modified was the RAM was upgraded.

---

### Post by SheaMan on 2009-09-05
I guess what I am really asking.. now that I have fuddled with this is,

What is the command I need to type "Fsck" style to get it to scan and repair my bad sectors on my HD. I have one partition. No windows, and am currently booted from the Live CD.

---

### Post by bodhi.zazen on 2009-09-05
There are much better tools, see :

[http://www.linuxjournal.com/article/6983](http://www.linuxjournal.com/article/6983)

It is a bit old, but the information is accurate.

See also [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

The tools are in the Ubuntu repositories.

---

### Post by SheaMan on 2009-09-05
OK, interesting... I think I have identified another problem though.

I don't know what my HD is named... its not C anymore - I am fairly certain of that. 

When I did the testdisk command it showed up with a "Linux" partition.. is that the HD name? Jeez I must sound like a complete n00b. As I said earlier - I am a fair hand at windows manipulation, but arg Linux strange. Half tempted to go back to win, but... no.

I am commited to figuring this out - and it can. not. be. this. complicated.

---

### Post by bodhi.zazen on 2009-09-05
for an over view of partitioning see :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

for checking the health of your drive see my previous link. Testdisk is more a recovery took then it is for monitoring the hard drive.

---

### Post by SheaMan on 2009-09-05
From reading the article it seems like the only thing that Smartmontools can do for me is tell me "yes there are bad sectors" and were I under a warranty I could then get a replacement HD. Fsck is supposed to actually locate and "correct" bad sectors. 

I know it doesn't "fix" the sectors but it tells the system to avoid them. Smartmontools says nothig about "repair" but Fsck is listed as being able to "repair" disk problems. At this point I am really confused by how to activate the Fsck program. It happened automatically whith the previous install and it was this long crazy thing where my freind said "don't worry just hit enter a bunch" and I figured everything would be fine. 

Now I try ~$ Sudo Fsck /dev/sda (which is what I think the HDs name is - from the testdisk log file). and I get fsck 1.41.4 (27-jan-2009) and the command prompt.

what?

---

### Post by bodhi.zazen on 2009-09-05
What are you wanting to do ? Bad sectors are not really repaired.

Smartmontools will show you the health of your drive and give you an idea of how much longer it may last.

fsck will repair your file system and avoid bad blocks and as the command does not return a problem there is nothing to do. In general you run it from the command line from a live cd (you will get warnings if you run it on a mounted partition)

sudo fsck /dev/sda1

Linux runs fsck automatically, at boot, every 30 times you mount a partition. 

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")  (6th column in fstab entries).

testdisk and photorec are data recovery programs and do not test or repair your hard drive.

Honestly, this is not windows and it is rare, if ever, that as a user of Linux you need to perform these tasks and if they do not work automatically there is not much manually that can be done to repair your hard drive or file system.

See also man fsck

---

### Post by Paqman on 2009-09-05
> **SheaMan said:**
> 
Now I try ~$ Sudo Fsck /dev/sda (which is what I think the HDs name is - from the testdisk log file). and I get fsck 1.41.4 (27-jan-2009) and the command prompt.

what?

Make sure it's:
```

sudo fsck -c /dev/sda1

```

To check the partition sda1 for bad sectors, for example. Linux is case-sensitive, too, so don't use capitals unless they're needed.

---

### Post by SheaMan on 2009-09-05
OK! Something is happening now - and its familiar too. 

error block (numbers) ... ignore error <y> ... I hit enter. 
Force Rewrite <y> ... again I hit enter. 

Badblocks: Input/Output error durring ext2fs_sync_device
Checking for bad blocks read only test. 

And two counters... progress right?

---

### Post by SheaMan on 2009-09-06
Wahooo! It ran and fixed things! Read for yourself

```

ubuntu@ubuntu:/$ sudo fsck -c /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
Error reading block 589825 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  Ignore error<y>? yes

Force rewrite<y>? yes

badblocks: Input/output error during ext2fs_sync_device
Checking for bad blocks (read-only test): ^[[B^[[D^[[C^[[C^[[Clapsed
  4.94% done, 4:18 elapsed
  4.97% done, 13:46 elapsed
  6.20% done, 53:55 elapsed                                           6.20% done, 54:03 elapsed                                            6.20% d  6.20% done, 54:19 elapsed                                        6.21% done, 55:48 elapsed                                           6.21% done, 55:56 elapsed            6.21% done, 56:21 elapsed                       6.21% done, 56:28 elapsed                                            6.21% done, 56:37 elapsed                                            6.21% done, 56:45 elapsed                                            6.21% done, 56:53 elapsed                                            6.21% done, 57:01 elapsed                                            6.21% done, 57:09 elapsed                                            6.21% done, 57:17 elapsed                                            6.21% d  6.22% done, 57:33 elapsed                                       6.22% done, 57:41 elapsed                                            6.22% done, 57:48 elapsed                                            6.22% done, 57:56 elapsed                                            6.22% done, 58:04 elapsed                                           done                                
/dev/sda1: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Group 18's inode bitmap (589825) is bad.  Relocate<y>? yes

                                                    Error reading block 589917 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

^[Error reading block 589918 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 589919 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes


Relocating group 18's inode bitmap from 589825 to 590337...
Error reading block 589825 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  +590337
Fix<y>? yes

Free blocks count wrong for group #18 (31884, counted=31890).
Fix<y>? yes

Free blocks count wrong (8850268, counted=8850274).
Fix<y>? yes

Inode bitmap differences:  +(148609--148624) +(150065--150080) +(151521--151536) +(152513--152528) +(152977--152992) +(154433--154448)
Fix<y>? yes

Free inodes count wrong for group #18 (8176, counted=8080).
Fix<y>? yes

Free inodes count wrong (2264763, counted=2264667).
Fix<y>? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 122725/2387392 files (0.4% non-contiguous), 698352/9548626 blocks

```

---

### Post by Paqman on 2009-09-06
Excellent news, although i'd start thinking about replacing that drive in the not too distant future.

---

### Post by 3rdalbum on 2009-09-06
Replace the drive. If you've just installed Xubuntu and you've presumably booted it 30 times and it's already found that number of errors, then your drive is on its last legs.

As someone said before in this thread, bad blocks are flagged by your drive's firmware, and information about them is stored in a little segment of drive memory. Any bad blocks that have already been flagged by the drive will not be accessed by the drive again, so even if you reformat the disk the bad blocks will stay flagged.

---

### Post by SheaMan on 2009-09-06
Thanks for the help guys! Annoying that this HD is dying fast... the whole reason for this laptop was "cheap" and a new HD is going to be out of the question for a minute.

Other than the links that have already accumulated is there any suggestions or tactics that could extend the lifespan of this HD? hmmm... now the question is how to set the thread to resolved... hmmm...

---

### Post by Paqman on 2009-09-07
> **SheaMan said:**
> 
Other than the links that have already accumulated is there any suggestions or tactics that could extend the lifespan of this HD? hmmm... now the question is how to set the thread to resolved... hmmm...

Not really. It's on it's way to the hard drive graveyard. A replacement drive doesn't have to be expensive, keep an eye out on eBay for a bargain, or check the online retailers. I never buy any electronics from a bricks-and-mortar store, they're always beaten on price by the online stores.

To mark the thread as solved, go to "thread tools" at the top.

---


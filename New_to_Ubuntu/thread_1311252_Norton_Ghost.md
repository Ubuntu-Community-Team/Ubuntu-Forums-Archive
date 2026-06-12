---
title: "Norton Ghost"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-11-02
Before I buy it...
Will it see my dual boot with Linux?
WIll it back that up too?
Is Ghost password protected?

---

### Post by Penguin Guy on 2009-11-02
It can handle ext3 and ext2 filesystems, but not ext4 filesystems according to [this]("http://service1.symantec.com/SUPPORT/ghost.nsf/d87bb6ce0bde286d88256d6a00452701/ea5c1b9e588eb9dd88256ad3005ccde6?OpenDocument"). You can find what type of filesystem you have by [running]("http://www.psychocats.net/ubuntu/terminal") [COLOR="Green"]sudo parted -l[/COLOR].

---

### Post by LewRockwell on 2009-11-02
we swear by clonezilla here at the tech bench

.

---

### Post by kakashi_12 on 2009-11-02
what's an ext? and what's ext 4?

---

### Post by Penguin Guy on 2009-11-02
> **kakashi_12 said:**
> what's an ext? and what's ext 4?
Ext is the Linux filesystem, you get lots of filesystems that store data in different ways. ext2, ext3, and ext4 are all different. [Run]("http://www.psychocats.net/ubuntu/terminal") [COLOR="Green"]sudo parted -l[/COLOR] and post the results back here, I'll tell you if Norton Ghost will support your Linux install or not.

---

### Post by bodhi.zazen on 2009-11-02
Most of us use Gparted :

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Is there something you need that gparted will not do ?

There are a number of rescue disks including the gparted live CD and clonezilla.

ext4 is a file system, and is now the default on Ubuntu and Fedora (and likely most distros).

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by jimmy the saint on 2009-11-02
> **LewRockwell said:**
> we swear by clonezilla here at the tech bench

.

I know I'm spending too much time on reddit when I come here, attempt to help some beginners, see that someone wrote exactly what I was going to say and immediately reach for the upvote button!

Clonezilla rocks.

+1 for you sir.

---

### Post by sloggerkhan on 2009-11-02
3rd person for clonezilla.
In my experience ghost is very awkward and clonezilla has features that you probably would need more than a basic ghost license for.

---

### Post by kakashi_12 on 2009-11-02
awesome. Thanks!
 
Will it memorize all of my settings (such as layout of my toolbars and desktop and permissions)? Will it remember my modified grub loader?

This might seem redundant, maybe even unnecessary, but will it work with RAID too (striped with parity)? But then if I'm using striped with parity, then clonezilla may not be necessary. ?!?!

Well anyway, I can at least use Clonezilla for my laptop (only one drive). For my desktop (which I am building in the future) I can just use RAID. Right? What do you guys think?

---

### Post by kaibob on 2009-11-02
I recently began using clonezilla and like it a lot. The standard version would not work with karmic with ext4, but the karmic-based version works great. I don't know if it will work with raid.

---

### Post by presence1960 on 2009-11-02
> **LewRockwell said:**
> we swear by clonezilla here at the tech bench

.

clonezilla & PING I find are the best for making backup images.

---

### Post by kakashi_12 on 2009-11-02
do they backup to a dvd disc?

---

### Post by presence1960 on 2009-11-02
> **kakashi_12 said:**
> do they backup to a dvd disc?

Your OSs are probably not going to fit on a DVD. Your data will probably take many DVDs. Your best bet is to backup to a separate internal or external hard disk.

---

### Post by NickJones on 2009-11-02
> **kakashi_12 said:**
> awesome. Thanks!
 
Will it memorize all of my settings (such as layout of my toolbars and desktop and permissions)? Will it remember my modified grub loader?



If you take an image of the disk with Ubuntu on it the MBR (Master Boot Record) will give you an exact copy you can later put onto your new PC.
Nick

---

### Post by kaibob on 2009-11-04
> **kakashi_12 said:**
> ...This might seem redundant, maybe even unnecessary, but will it work with RAID too (striped with parity)? But then if I'm using striped with parity, then clonezilla may not be necessary. ?!?!...

I don't know anything about raid but happened upon the following in the Clonezilla FAQ and thought I would post it FWIW:

> Clonezilla does support hardware RAID, if your RAID device is seen as /dev/sda, /dev/sdb, /dev/hda, /dev/hdb, /dev/cciss/c0d0... on GNU/Linux. Clonezilla does support this.
On the other hand, if it's Linux software RAID, no, Clonezilla does not support that.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by kakashi_12 on 2009-12-06
Lets say I have a 100 GB hard drive, but only 10 GB worth of information. When I clone the drive, is it going to clone the free space too? In other words, when the clone is made, will it be 100 GB or 10 GB?
 
Then I also have to leave a couple GB extra for virtual memory. Does Linux require extra hard drive space for something like that?
 
Should I re-create my partitionS FIRST, and THEN restore the clones? So lets say I make a partition of 15 GB and then restore the 10 GB clone on it, does that work?

---

### Post by Locke_99GS on 2009-12-06
For backing up files, a backup utility or *rsync* is better suited. Cloning creates images of entire partitions. A disk image of a partition that had a lot of empty space on it can be compressed into a much smaller file. 

IMO, the best tool for cloning (amongst other things) is *dd*.

---

### Post by kakashi_12 on 2009-12-06
Well. I've already got Clonezilla learned and burned on a disc. I want to just move my files to another drive for now. And make a clone of JUST the OS and all INSTALLED apps. Then I can make a clone of only 10 GB or so or less.
 
PS. I like yur avatar

---

### Post by kakashi_12 on 2009-12-11
You know the rule of thumb... install Windows before Linux.

Well what happens if I go ahead and back these up, and then have to restore one of the partitions. What if I have to restore my Windows partition? Will it screw up because I'm putting it on after linux? Maybe I should backup the entire drive instead of separate partitions.

---

### Post by presence1960 on 2009-12-11
> **kakashi_12 said:**
> You know the rule of thumb... install Windows before Linux.

Well what happens if I go ahead and back these up, and then have to restore one of the partitions. What if I have to restore my Windows partition? Will it screw up because I'm putting it on after linux? Maybe I should backup the entire drive instead of separate partitions.

that is not a rule of thumb, that is a fallacy. You can install windows or Linux first. If you install Windows after Linux on the same hard disk what happens is the windows bootloader overwrites GRUB on the MBR and causes your machine to boot right to windows. All that is necessary is to restore GRUB to MBR.

To restore GRUB 0.97 do this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

To restore GRUB 2 see [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

---

### Post by kakashi_12 on 2009-12-12
ok thanks. i'll keep it on reference in case i need it.

---

### Post by beetleman64 on 2009-12-12
> **Penguin Guy said:**
> It can handle ext3 and ext2 filesystems, but not ext4 filesystems according to [this]("http://service1.symantec.com/SUPPORT/ghost.nsf/d87bb6ce0bde286d88256d6a00452701/ea5c1b9e588eb9dd88256ad3005ccde6?OpenDocument"). You can find what type of filesystem you have by [running]("http://www.psychocats.net/ubuntu/terminal") [COLOR=Green]sudo parted -l[/COLOR].

A quick point: If you're running Ubuntu 9.10 or Fedora 11+ then it'll be ext4 and not compatible with Norton Ghost.

---

### Post by presence1960 on 2009-12-12
> **beetleman64 said:**
> A quick point: If you're running Ubuntu 9.10 or Fedora 11+ then it'll be ext4 and not compatible with Norton Ghost.

Not necessarily true, at least for Ubuntu. If you choose the manual option for installation you have the ability to choose ext 3 as filesystem for Ubuntu. If you did do that when you installed 9.10 then it will be compatible. Just because someone has 9.10 does not necessarily mean they are using ext4, which by the way is the default option. You do have the option of choosing from a few filesystems to use with Ubuntu, you do not have to use ext4. But you must choose the manual option to do so.

I have a whole disk as one partition for data. That is always kept as ext3 so as to not have any conflicts with any Linux distro or back up software. My root partitions are all ext 4 though.

---

### Post by howefield on 2009-12-12
> **beetleman64 said:**
> A quick point: If you're running Ubuntu 9.10 or Fedora 11+ then it'll be ext4 and not compatible with Norton Ghost.

Not exactly, ghost will do a sector by sector backup on ext4, (as will True Image). Possibly not practicable given the resultant backup file may be very big. 

In any case, clonezilla supports ext4 and does a superb job.

---

### Post by kakashi_12 on 2009-12-13
it doesn't matter. i'm using clonezilla. i already studied it and burned it to a disc, it's free. i was just using the term "ghost".

---

### Post by CharlesA on 2009-12-13
I used PING before, but switched to clonezilla due to EXT4.

---

### Post by presence1960 on 2009-12-13
> **kakashi_12 said:**
> it doesn't matter. i'm using clonezilla. i already studied it and burned it to a disc, it's free. i was just using the term "ghost".

How can you make that staement that you were just using the term "ghost"? In your original post you specifically called it Norton Ghost! Need I refresh your memory?

 
> your quote from post #1
Norton Ghost
Before I buy it...
Will it see my dual boot with Linux?
WIll it back that up too?
Is Ghost password protected?

You just wasted 3 pages of thread.

---

### Post by kakashi_12 on 2009-12-14
lol, don't get all bent out of shape about it. These people talked me into Clonezilla. I didn't know it existed before starting the thread. That's what forums are for. Ghosting, cloning, it's all the same when used as a term.

---

### Post by lavinog on 2009-12-14
> **kakashi_12 said:**
> lol, don't get all bent out of shape about it. These people talked me into Clonezilla. I didn't know it existed before starting the thread. That's what forums are for. Ghosting, cloning, it's all the same when used as a term.

lol
I think this is why PING stands for PING Is Not Ghost

I don't thing ghosting is a standard term.
People tend to take things the wrong way when they hear proprietary labels used as terms.

---

### Post by stinger30au on 2009-12-14
i think you will find that "harddisc image software" or "harddisc clone software" is probably more understandable

---

### Post by presence1960 on 2009-12-14
> **kakashi_12 said:**
> lol, don't get all bent out of shape about it. These people talked me into Clonezilla. I didn't know it existed before starting the thread. That's what forums are for. Ghosting, cloning, it's all the same when used as a term.

After reading your original post & then that last statement kind of threw me for a loop. You did originally ask about Norton Ghost, the exact quote was "before I buy it."

It would have been more clear and concise to say someone suggested PING or clonezilla and that you have tried that.

---

### Post by kakashi_12 on 2009-12-14
i know. that called a generic term or brand name used as generic. Like when someone says kleenex instead of tissue.

---

### Post by Locke_99GS on 2009-12-14
Or by saying "Windows Vista" referring to a "Operating System", even though they are talking about "Solaris".

---

### Post by garvinrick4 on 2009-12-14
Norton Ghost see's my partitions and makes an image of each partition not of whole drive.
That is my experience anyway. Do not know what Norton Claims. Does a good job.
Is a whole image and not compressed, need some disc space on back-up drive.
Norton 15 is suppose to do better and fancier things, I have 14.

---

### Post by kakashi_12 on 2009-12-14
> **Locke_99GS said:**
> Or by saying "Windows Vista" referring to a "Operating System", even though they are talking about "Solaris".
 
I've never heard of that one before. Anyone who even knows Solaris exist would probably be a techy and know what vista and windows are. Are you guys done pickin on me yet? I thought we were friends here.

---

### Post by presence1960 on 2009-12-14
> **kakashi_12 said:**
> I've never heard of that one before. Anyone who even knows Solaris exist would probably be a techy and know what vista and windows are. Are you guys done pickin on me yet? I thought we were friends here.

we are friends- friends have fun too, right? This time it is at your expense, maybe next time one of ours. One thing about me you probably do not know: I can disagree with someone wholeheartedly and even vehemently. But that is not a personal attack against that person. it is rather an attack on their idea(s). I can strongly disagree with someone and still like them.

---

### Post by kakashi_12 on 2009-12-17
I'm getting ready to clone very soon. For those of you that use _Clonezilla_ , what happens when I restore... what happens with the system clock. Does it re-sync? Or do you think it is left at the time you cloned it? If you change it, does that mess things up? I think it only messes up your system if you go back in system time. Right?

---

### Post by jamieleshaw on 2009-12-17
> **kakashi_12 said:**
> I'm getting ready to clone very soon. For those of you that use _Clonezilla_ , what happens when I restore... what happens with the system clock. Does it re-sync? Or do you think it is left at the time you cloned it? If you change it, does that mess things up? I think it only messes up your system if you go back in system time. Right?
Pretty Sure, it re-syncs with The BIOS.
Clonezilla IS AWESOME!

---

### Post by cartisdm on 2009-12-17
How does clone softare (Ghost, clonezilla, etc) handle genuine software and licenses? For instance, after restoring my backup does it just ask to validate Windows?

In reference to a Linux OS, if I transfer the backup to one of my other computers, how is it able to change the variations in the hardware? If I could clone one OS and get it all setup how I want and just restore the image on all my machines I could save so much time!

---

### Post by jamieleshaw on 2009-12-17
No, it doesn't cause for windows they assume you have purchased the appropriate license.

---

### Post by cartisdm on 2009-12-17
> **jamieleshaw said:**
> No, it doesn't cause for windows they assume you have purchased the appropriate license.

Hmm, that seems like an easy way to share Windows via torrents, I feel like I'm missing something.  Don't flame me for this, it's just pure observation.

I have always wanted to look into Ghosting my computers (that was before I knew of the freeware versions) but I feel like I change my OS and it's settings so often that I am never satisfied and that makes it hard to justify paying for the Norton Software haha

---

### Post by kakashi_12 on 2009-12-17
I've got it running now. This is sooo swwweeeeet!\\:D/
 
Now... do you think it backed up my swap image in linux? I don't think it did. It only showed sda1 (windows), sda5 (linux), but not sda3 (swap). I just want to know, so that when I restore, I don't end up having a duplicate one if I already set one up... or I end up without one. That's weird. If it does not backup the swap, how am I gonna remake it, then restore the image. Maybe I'll make a swap later.

---

### Post by lavinog on 2009-12-18
> **cartisdm said:**
> Hmm, that seems like an easy way to share Windows via torrents, I feel like I'm missing something.  Don't flame me for this, it's just pure observation.


every time you boot windows, it creates a hash of the installed hardware and compares it with the hash that was created during the first install/activation.  If the hash differs by a certain amount, the system is flagged and you have to re-activate.
Copying an image to another machine will cause the flag to be raised, even if you have the same hardware...it looks at serial numbers and mac addresses too.

---

### Post by Locke_99GS on 2009-12-18
> **cartisdm said:**
> Hmm, that seems like an easy way to share Windows via torrents, I feel like I'm missing something.  Don't flame me for this, it's just pure observation.

Any major hardware change (such as done during a major hardware upgrade) will prompt Windows to revalidate, such as upgrading from a DDR/AGP mainboard, to a newer mainboard with new RAM and a PCIe video card.

Using any Windows install in a machine that it wasn't originally installed in will cause this.

Modern Linux, on the other hand, won't have any problems going from one machine to the next, except for the occasional configuration change. One of my old boxes wouldn't boot from CD or USB. I pulled it's drive, installed it in a newer machine and installed Linux and GRUB onto it that way; verified that it would boot, then moved the drive back into the old machine. Booted up and ran without issue.

---

### Post by walt.smith1960 on 2009-12-19
I use "Image for linux" from [www.terabyteunlimited.com]("http://www.terabyteunlimited.com"). Download the .iso and create a live CD. It'll back up any partition or an entire disk to either CD/DVD or to a file. I also use BootItNG to install various OS's. I'm sure someone with enough knowledge could duplicate the functions of this software without paying for anything. I don't have enough hair left to be tearing it out.:)

---


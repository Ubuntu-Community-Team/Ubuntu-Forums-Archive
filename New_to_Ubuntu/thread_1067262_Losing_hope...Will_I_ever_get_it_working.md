---
title: "Losing hope...Will I ever get it working?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by mrapoc on 2009-02-11
Hey guys

Basically I think my problem all falls down to me having a Windows install on my primary RAID 0 configuration. I have two 10k raptor drives, raid0 is so tempting...speed etc. 

But the thing is

Ubuntu normal install wont detect the raid
It will install to one of my other drives...but i think GRUB likes to be on either the primary hard drive (the raptors..) or it needs to see the raid to actually load windows...gah!

I tried the alternate cd and yes, it saw I had a raid and asked to activate them. I did so and the next step it asks me what I want to do next. I click partition (or any other step actually) and it comes up with either

a) loading partitioner please wait (flashes and then goes straight back to previous menu)

b) same as above only it sticks at about 40 or 50% and screws the whole installation up :confused:

Help is needed, i only want windows for games :(

---

### Post by PoopyTheJ on 2009-02-11
What about moving windows off the RAID to another drive? Aside from that I'm not sure, RAID and ubuntu is a mystery to me and has totally screwed me more than once, so I'll be watching this thread very closely.

---

### Post by mrapoc on 2009-02-11
Hi

Well the whole thing of the RAID0 was to get top speeds on my windows install including all the games on there

Nothing crucial will be kept on there (music etc. are kept on "normal" hard drives) its just I want ubuntu for working on

All I need is to get ubuntu to detect the raid properly or get the alternate cd to work 

The raid is setup in bios and the onboard raid controller (intel something or other on a asus maximus formula x38)

---

### Post by PoopyTheJ on 2009-02-11
AFAIK, the Raid Controller on consumer level controllers aren't true hardware RAID controllers, ie the raid is actually identified and handled through software, so since it's not the hardware accessing the RAID, but software, you're not going to get the same RAID in Ubuntu as in windows. Best bet drop some dough on a high end RAID controller that handles it via Hardware, on our Corporate server using a Hardware SCSI controller, Ubuntu and windows handle the RAID just fine.

---

### Post by mrapoc on 2009-02-11
Im a student and aiming to use ubuntu to save cash and use apps free and legally lol

---

### Post by PoopyTheJ on 2009-02-11
Well then back to my original idea we'll see if someone's gotten good results with windows and Ubuntu side by side via software raid.

EDIT: Just found this, if you install Ubuntu to a different drive, not the RAID drive then this should work for you...

[http://ubuntuforums.org/showthread.php?t=613409](http://ubuntuforums.org/showthread.php?t=613409)

---

### Post by PoopyTheJ on 2009-02-11
There's also the Ubuntu FakeRaid howto...

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by mrapoc on 2009-02-11
Installed on the seperate hdd and running as i speak

however

booting vista as posted in that thread u mentioned, it says error boot mgr missing after selecting vista in the list

also 

annoyingly, starting ubuntu takes a good few minutes due to "buffer I/O error on device sr0, logical block xxxxxx" listed over and over before starting 

Terminal also throws up crap like that

Perhaps i need to re-raid in ubuntu (using true software) - will this be compatible in both ubuntu and vista? How do i do it?

---

### Post by Tatty on 2009-02-11
Did you try reburning the alternate cd?  Locking/crashing part way through an install is often a sign of a bad burn.

---

### Post by cariboo on 2009-02-11
Take the cdrom out of the drive when you're booting and you won't get the error.

Jim

---

### Post by mrapoc on 2009-02-12
So with no cd rom in the drive, i wont get the buffer i/o error?

I just need a bit of help now to get the grub loader to run vista - super grub disk should help me with that?

Is there a proper fix to stop the i/o errors other than not having a disk in? A new drive perhaps? (need an upgrade to a sata one anyway :lolflag:)

---

### Post by hyper_ch on 2009-02-12
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by mrapoc on 2009-02-12
ok :)

Any chance you could change it? I will do in the future

---


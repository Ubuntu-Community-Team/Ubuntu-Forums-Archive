---
title: "Okay so, I'm completely confused with something I may have done with Samba."
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-01-19
To make a long story short, I may have goofed up before, yet I'm not sure. I don't even know what I'm looking for here... Maybe it's just a rant... I don't know.

Before I somehow set up Samba to be mappable network drives. I set up 4 folders.

Jason
Curt
Ty
Mom

Jason = root user of Samba desktop. Curt, Ty, and Mom are Win XP/2000 Pro users on the network. I mapped the drive on each of their windows machines directly to their designated folder so they could drop stuff in to back it up on my spare hard drive in my desktop. Well, I decided to drop 2kpro and go with XP for my windows partition, so I decided to just do a fresh format of my entire system.

So I reinstalled Ubuntu on top of that. I just now went into my spare drive to redo Samba. I successfully got samba working, however instead of going to map a drive, which was a pain in the rear, I just set up a network share name and each user can just do a \\sambadesktop @ the run command and access the computer. Well, in the spare hard drive, Ty and Mom are gone. Yet, Jason and Curt are still there.

I have no idea what I did. It's not a big deal that they're gone, Ty had nothing in his folder and I actually had everything of Mom's backed up on an external hard drive. But I don't see why they were gone. Did I delete them and not realize it? Curt suggested to me that I may have deleted Ty's since he hasn't used his share. On top of that, I may have deleted Mom due to the fact that I had her stuff backed up in my home folder. I may have done that when I was having issues with the mapping network drives in Samba before. I don't know.

Anyway, I just wanted to rant and get this out there to stir up some possibilities so I can hear them and be like, OH YEAH, MAYBE I DID DO THAT. Or something like that. I don't know. Any input? Hahaha... Do you think I deleted them? Or was it possible something else backfired, resulting in the missing folders on my spare internal hard drive?

---

### Post by peabody on 2008-01-19
Couple of things:

[LIST]
[*]Were they perchance accidentally moved into the other folders?
[*]What is the filesystem used on the spare drive?
[/LIST]

disk recovery tools may be able to turn something up as well.

---

### Post by HermanAB on 2008-01-19
Do a double check:

See what is mounted where:
$ mount

for example /mnt/otherdrive

List the schtuff on the drive:
$ ls /mnt/otherdrive

Cheers,

Herman

---

### Post by Roasted on 2008-01-19
Those commands weren't found. *shrug* 

Disk recovery isn't necessary as nothing was lost. My spare hard drive was just acting as a backup drive for the network. My brother Tyler didn't even bother to use it. My mom's stuff is on my external. So even if one of their computers crashed, we were covered.

I just found it odd that only Jason and Curt showed up. I just sincerely can't remember if I deleted it or not. I remember being confused by something and having to do an rm -rf command not so long ago, so that may have been it.

I mean it's as simple as this...

I mount sdb2 to driveb.
Inside driveb is jason, mom, curt, ty
I run an rsync script to /driveb/jason for my backup sake.
I mapped drives through samba on the windows machine for the designated computer, mom, curt, ty.
I didn't format that drive. This drive is a spare one. I formatted the first drive, sda1 I believe, to redo my operating systems. 

I mean, the only logical explanation is that I DID delete them. Right? 

As I said, I remember something getting F'd up with the samba server last time, to the point where I didn't have it active anymore, so it's very possible that I did away with their folders. But if I did, I don't know why I left Curt... blah. What did I dooooooooooooooo. lol

---


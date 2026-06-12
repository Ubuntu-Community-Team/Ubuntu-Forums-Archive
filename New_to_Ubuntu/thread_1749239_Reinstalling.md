---
title: "Reinstalling"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by DaveMcC on 2011-05-04
If I was to reinstall ubuntu same version, back into where it is at, would I loss all my work that I have saved in doc, downloads etc
As I need this computer up dual booting again

Thanks
Dave

---

### Post by madjr on 2011-05-04
well it depends.

if you made the partitions manually and assigned the "home" area into its own partition than it wont overwrite that partition.

but if you did a normal default ubuntu install then, you will need to copy your important stuff somewhere to back them up.

either way, before installing any OS is always recommended that you always have space for backups.

if you need further help let us know

---

### Post by DaveMcC on 2011-05-04
I had a problem with winxp and had to reinstall it...? Now I can't get grub to work as it lives in MBR and I thought if I put ubuntu same version back in I may be able to retrieve all my files
That would be with out having to reset partitions

Dave

---

### Post by TBABill on 2011-05-04
If you put Windows XP on the machine it is likely it used the entire drive and already overwrote your Ubuntu files (and the OS). Can you run the live CD and still see and mount your old Ubuntu partition?

---

### Post by QLee on 2011-05-04
[QUOTE=DaveMcC]I had a problem with winxp and had to reinstall it...? Now I can't get grub to work as it lives in MBR and I thought if I put ubuntu same version back in I may be able to retrieve all my files
That would be with out having to reset partitions

Dave[/QUOTE]

If you used a Windows "restore" partition or disk then I agree with poster TBABill, it probably overwrote everything on the drive.

On the other hand, if what you mean is just installed Windows back to the partition that it previously occupied and left the Ubuntu partitions alone then all you would need to do is restore GRUB and there are step-by-step procedures for that.

One more thing to consider, was it previously a wubi install of Ubuntu. If that was the case then your Ubuntu was contained inside your Windows installation and it would have been overwritten with the Windows install.

As suggested by TBABill, if your Ubuntu partition (if there was one in the first place) still exists, use the live CD to grab and backup your important files for safety before trying anything that might overwrite them.

---

### Post by Techboy26 on 2011-05-04
I have ubuntu 8.10 and the other day my computer froze while my synaptic package manager was doing a partial upgrade and when I restart my computer and went to package manager it told me basically to manually configure -a and so I went to terminal in did what it told me and this is my output:
charles@charles-desktop:~$ sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/updates/0025' near line 0:
 field name `&#1548;' must be followed by colon

*I cant install anything or configure anything I tried apt-get update, apt-get upgrade, apt-get install f, dpkg-reconfigure dpkg and others none work I keep getting the "dpkg: parse error, in file '/var/lib/dpkg/updates/0025' near line 0:"

Do I need to reinstall Ubuntu?

---

### Post by DaveMcC on 2011-05-04
Because I made sure it went back into its 24gb partition, I did not re format any part of the drive, It also left my old winxp work files in place, just as I told? it to do
What I done was a windows only install.

I have ran the LiveCD, its reporting some thing about cylinder  not correct, me thinks me has a second faulty hard drive, cuz when I done a "Disk Utility" check on it, it reported back that the drive was near 4 year old
This is my second drive inside 8 weeks (from the same company) that has failed

I have an old 40gb drive here,
If I set it up, should I then be able to retrieve my files from the one that I think is failing, set it in as slave?

Dave

Should have added that the live cd can not see either hard drive on my computer, I have ubuntu 64

---

### Post by wolfen69 on 2011-05-04
Sounds like you are having serious hardware failure. Btw, what kind of hard drives are they?

---

### Post by DaveMcC on 2011-05-04
Yip
just ran GParted off the LiveCD
entire drive is unallocated, partition, file system the lot
The drive's came from Maplins, will fill in later who made them when I pull it from computer

Seagate
Or should that now read SicK Gate

wolfen69
Just a point of note, you under sign your name with
"I see Ubuntu as an extension of my brain. I can customise, mix and  match and make it work the way I want. I see Windows as an extension of  someone else's brain.

If ubuntu had of done the things I wanted it to do, like by deflate save file's to other drive I would not care how often the main OS drive fails as long as the back-up or saved work drive don't fall off its perch I would b e OK
Every time I set it to save else where, on restart it was back to saving files with-in its self, just as windows does
That is the only thing that pevved me off with ubuntu

Dave

---

### Post by wolfen69 on 2011-05-04
> **DaveMcC said:**
> wolfen69
[B]Just a point of note, you under sign your name with
"I see Ubuntu as an extension of my brain. I can customise, mix and  match and make it work the way I want. I see Windows as an extension of  someone else's brain.

If ubuntu had of done the things I wanted it to do, like by deflate save file's to other drive I would not care how often the main OS drive fails as long as the back-up or saved work drive don't fall off its perch I would b e OK
Every time I set it to save else where, on restart it was back to saving files with-in its self, just as windows does
That is the only thing that pevved me off with ubuntu

Dave
[/B]

Perhaps you should take a new approach to backing up your stuff. I don't even keep important things on my ubuntu drive. I have another drive for this. I even have yet another drive to backup my stuff, just in case the drive with my stuff dies. Don't blame the OS, blame poor planning.

---


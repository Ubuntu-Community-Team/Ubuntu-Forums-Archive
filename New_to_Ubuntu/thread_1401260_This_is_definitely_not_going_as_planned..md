---
title: "This is definitely not going as planned."
date: 2010-02-07
forum: New to Ubuntu
---

### Post by EMABrad on 2010-02-07
So I've had a LITTLE bit of experience in Hardy Heron a while back, but now I've downloaded (and burned to a CD) Karmic Koala.  I want to dual boot Vista and Ubuntu.  So I've freed up 64.8GB of a 287GB drive.

The problem is, when I try to shrink that partition, it only says I can shrink it by 57MB.  I know how to create a new partition, and I know how to install Ubuntu (hell, I just did it for a friend of mine), but I don't know how to make more space available for shrinking.  I'm totally positive I have these 64.8GB free.  I've defragged like 3 times.

Halp?

---

### Post by OrangeCrate on 2010-02-07
> **EMABrad said:**
> So I've had a LITTLE bit of experience in Hardy Heron a while back, but now I've downloaded (and burned to a CD) Karmic Koala.  **I want to dual boot Vista and Ubuntu**.  So I've freed up 64.8GB of a 287GB drive.

The problem is, when I try to shrink that partition, it only says I can shrink it by 57MB.  I know how to create a new partition, and I know how to install Ubuntu (hell, I just did it for a friend of mine), but I don't know how to make more space available for shrinking.  I'm totally positive I have these 64.8GB free.  I've defragged like 3 times.

Halp?

One of the definitions of a genius, is "the ability to avoid work, by doing it right the first time". Take some guidance from here on dual booting:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

Good luck.

:)

---

### Post by EMABrad on 2010-02-07
Why thank you.  I shall look into this.

---

### Post by nhasian on 2010-02-07
are you trying to shrink the partition inside of the windows disk manager?  that is crap, its never worked for me.  instead, boot from the ubuntu liveCD and resize the partition with gparted from System->Administration->Partition Editor (gparted)

> **EMABrad said:**
> The problem is, when I try to shrink that partition, it only says I can shrink it by 57MB.

also see if you can free up more disc space.  web browser cache, downloads, system restore points, windows swap file, stuff in the trash can, i'll bet you can free up a bunch more space.

---

### Post by hemimaniac on 2010-02-07
In order to free up disk space in Vista/Win7 one needs to turn off alot of extra stuff first, 
the following are just a start;

1- System Restore-this actually takes up way more room that it needs to, I believe the average is 20% of the total install (including programs and linked databases)

2- Shadow Copy -when doing a disk clean up as admin, every remember seeing that "clean shadow Copies" in the extra function tab, well this rakes up more room then ever with vista and win7, but unlike Restore this one needs to be disabled via msconfig.

It is imo "good" practice to turn this stuff off before using ANY disk management software, if the space is taken away with out telling windbloze not to look for it, it will really slow down boot ups and other system functions.

Though it is a admirable feature in windows, it is no wonder why alot of us thumb out noses at it.

---

### Post by coldfusion1313 on 2010-02-07
you have to be careful partition windows in gparted. Because NTFS is not a journaling filing system, you can have some files become corrupted. It happened to me last month, the last time I will ever use window$, I was repartitioning in gparted and windows got messed up but idc since I had backed up all my stuff. Thank god for back-ups. So just be careful and back-up your stuff.

---

### Post by kansasnoob on 2010-02-07
> are you trying to shrink the partition inside of the windows disk manager? that is crap,

Nonsense! Resizing Vista or Win 7 with anything but it's own tools is reckless!

---

### Post by coldfusion1313 on 2010-02-07
it is the only way to resize NTFS partitions with out corrupting files.

---

### Post by EMABrad on 2010-02-08
I've got it up to 407MB, and I'm running PerfectDisk because I read that frees up a lot of space.  Any other suggestions?  I'm hoping to get to 40GB or so.

---

### Post by EMABrad on 2010-02-08
Also, sorry for the repost, but I'm reading this on the 9.10 wiki:

> Warning: The Ubuntu Desktop edition LiveCD installer no longer allows a custom installation of GRUB, and it now uses GRUB2 (which is difficult to customize). DO NOT USE the Karmic Koala Desktop edition LiveCD as an installer if you use a boot partition, use more than 2 operating systems, or chainload bootloaders. The Ubuntu installer will overwrite your Master Boot Record and you will later be forced to recreate it. This is a serious flaw in the Karmic Koala Desktop edition installer. Use the Ubuntu Server edition instead (and then later add the ubuntu-desktop).

Is this something for me to worry about?

---

### Post by nhasian on 2010-02-08
> **kansasnoob said:**
> Nonsense! Resizing Vista or Win 7 with anything but it's own tools is reckless!

I would use the Window's Disk manager to resize if it worked, but it doesnt.  It never allows me to shrink a volume as much as i'd like to.  even after doing all those steps that hemimaniac suggested and more.  I've used gparted many many times to shrink NTFS partitions and its worked every time.

> **hemimaniac said:**
> In order to free up disk space in Vista/Win7 one needs to turn off alot of extra stuff first, 
the following are just a start....


yep, i disabled shadow copy, and system restore, and turned off the swap file, and a bunch of other nonsense in windows and rebooted and defragmented 3 times even tho I have over 100 gigs free the windows disk manager tool would only allow me to shrink 30 gigs.  I gave up on it and just used gparted.  gparted is a great tool.  wether you are shrinking your disk in windows or using gparted, make sure you do backups first.

> **coldfusion1313 said:**
> it is the only way to resize NTFS partitions with out corrupting files.

see above.

---

### Post by coldfusion1313 on 2010-02-08
the other option is to delete windows completely and become a linux/open soucre user :) but that is a little extreme for the first time user.

---

### Post by durand on 2010-02-08
> **EMABrad said:**
> Also, sorry for the repost, but I'm reading this on the 9.10 wiki:



Is this something for me to worry about?

Nope, grub 2 will detect your windows installation so it almost definitely will work.

---

### Post by mechro on 2010-02-08
> **EMABrad said:**
> Also, sorry for the repost, but I'm reading this on the 9.10 wiki:

> Warning: The Ubuntu Desktop edition LiveCD installer no longer allows a custom installation of GRUB, and it now uses GRUB2 (which is difficult to customize). DO NOT USE the Karmic Koala Desktop edition LiveCD as an installer if you use a boot partition, use more than 2 operating systems, or chainload bootloaders. The Ubuntu installer will overwrite your Master Boot Record and you will later be forced to recreate it. This is a serious flaw in the Karmic Koala Desktop edition installer. Use the Ubuntu Server edition instead (and then later add the ubuntu-desktop).

Is this something for me to worry about?

Hmmm... perhaps this was a bug that has now been fixed. My karmic with Grub2 installation is chainloaded from a Grub Legacy boot partition and the MBR wasn't touched.

---

### Post by daphnestory on 2010-02-08
Please help me!! I'm really sorry I have to post this here, but can someone please tell me where to click to make my own question? It lets me post a reply, but I don't know where to click to make a new question. If I know, I wouldn't bother you by asking this here.

---

### Post by mechro on 2010-02-08
> **daphnestory said:**
> Please help me!! I'm really sorry I have to post this here, but can someone please tell me where to click to make my own question? It lets me post a reply, but I don't know where to click to make a new question. If I know, I wouldn't bother you by asking this here.

There's a **New Thread** button on every forum's index page e.g. go to Absolute Beginner Talk and the button is near the top of the page.

---

### Post by Hwæt on 2010-02-08
> **daphnestory said:**
> Please help me!! I'm really sorry I have to post this here, but can someone please tell me where to click to make my own question? It lets me post a reply, but I don't know where to click to make a new question. If I know, I wouldn't bother you by asking this here.

Right where it says "New Thread".

[img]http://ubuntuforums.org/attachment.php?attachmentid=146472&stc=1&d=1265673973[/img]

---

### Post by alexfish on 2010-02-08
> **daphnestory said:**
> Please help me!! I'm really sorry I have to post this here, but can someone please tell me where to click to make my own question? It lets me post a reply, but I don't know where to click to make a new question. If I know, I wouldn't bother you by asking this here.

Hi

From the Ubuntu Forum Community Page select the topic ,IE : Absotute Beginner Talk

Near the top of the page there is a button called [New Thread]: Click . and  way you go

screen shot below

Just a bit to late ; just seen above , It sometimes happens

---

### Post by EMABrad on 2010-02-08
> **durand said:**
> Nope, grub 2 will detect your windows installation so it almost definitely will work.

Well, I guess I'm about to find out.

---

### Post by mikechant on 2010-02-09
> I would use the Window's Disk manager to resize if it worked, but it doesnt. It never allows me to shrink a volume as much as i'd like to. even after doing all those steps that hemimaniac suggested and more. I've used gparted many many times to shrink NTFS partitions and its worked every time.

However, lots of people *have* reported problems using gparted to resize NTFS partitions.

There's been a lot of discussion about this over the last few years and I've got these main points out of it:
1/ Make absolutely sure that in gparted when shrinking an NTFS partition the 'Align to cylinder boundaries' box is *NOT* ticked.
This can move the *start* of the windows partition as well as shrinking from the end, and windows does *not* like it.

2/ If windows appears to hang on boot (no errors, blank screen) - leave it alone, if necessary overnight - it may well recover automatically after rebuilding its filesystem pointers (in my case this took about 3-4hours for a 50Gb partition).

3/ If windows produces errors on boot and stops (?ntldr not found etc.) then the windows repair disc may be able to fix it.

4/ Symtoms and risks are different in XP/Vista/7

---


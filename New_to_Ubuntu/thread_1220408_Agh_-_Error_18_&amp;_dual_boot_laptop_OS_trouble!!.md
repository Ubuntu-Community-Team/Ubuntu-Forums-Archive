---
title: "Agh - Error 18: &amp; dual boot laptop OS trouble!!! Works with LIVEDVD but not without!"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by vanco on 2009-07-22
Hi all, 

I am in trouble! I screwed up bigtime!!!

I am getting this error when booting my laptop via GRUB :  
*Error 18*: Selected cylinder exceeds maximum supported by BIOS

I can access both XP and Ubuntu 9.04 when the LiveDVD is inside and choosing "boot from 1st hard disk"
Then it goes to GRUB and I can pick either Ubuntu or XP and it will load.

Can I solve this somehow in grub configuration?? I have no idea how to do this. I never did anything like this. 

I am including all the background and details to my story here to hopefully make it easier for you to guide me. 


I have an old IBM R31 Thinkpad - PIII / 512mb RAM, 30gb hdd

I have been trying to find a solution for the last few hours but keep running into problem after problem.  I have been using 8.10 & Windows XP fine on this laptop for many months. 

Today I decided to do an update to the latest. BAD MISTAKE, since this is the worst possible time for anything to go wrong. I need my laptop for school work & studying and have been delayed trying to figure this out. I came here for some much needed desperate help. I am not very familiar with all the terms and commands. I would be devastated if I have to reinstall my Windows all over. I will lose so much time on this, especially since I can access this from the very first part of my paragraph.


This all happened when I first tried to upgrade via the update manager from 8.10 > 9.04. The first time, my laptop froze in the middle of the final few updates in 8.10. I had to reboot and complete again. Finally after I got 8.10 updated, I had a power outage during my 9.04 upgrade and my installation failed. I had to reboot again. This time, I am stuck at a root@ menu with nothing.

I downloaded the liveCD from a friend's computer and burned to a DVD. 

This was my setup before : (I don't even remember how I did this - it's been so long!)
sda1 (ntfs): XP ~10gb
sda2 (ext3): Ubuntu 8.10 ~10gb
swap : ~2gb
sda6 (ext3) - this was just another partition I made

I initially installed XP , then ubuntu many many months ago on this laptop. It is a single hard disk ~30gbs.


Ok so I put the liveDVD ( I didnt have a blank CD) in and manually deleted partition SDA2 Ubuntu 8.10
I ran the setup and kept everything as Default and mounting option ( / ) with format to that bad ubuntu install. I began installing 9.04 but then I got an error about a faulty drive/cooling problem! 

I am really getting angry at this point since I am supposed to be studying now.

Anyway I took an air duster and moved my laptop to a cooler setting.
Installation went fine this time

Now I went to boot up and got the above error when choosing either OS in GRUB Launcher :
 *Error 18*: Selected cylinder exceeds maximum supported by BIOS

Argghhhhhhh!

So right now it looks like this order from the manual partition :

SDA1 NTFS XP
SDA 7 EXT3 Ubuntu 9.04
SWAP
SDA 5 EXT3



I tried the irc channel first but I was told to come here.

I hope I am not confusing anyone with this. I googled this error message and it all pointed to articles on how I am screwed, I would need my XP cd again, delete master boot records... ahh so confused. I only have an OEM XP disc and this doesn't even have a Recovery Console to do that rmbr command or whatever it was I saw. 

I hope it's something simple that I can change . I didn't want to continue any more ubuntu updates until I got this solved.

Again, I can launch both of these OS's when the LIVEDVD is in and choosing boot from 1st hard disk.


THANK YOU SO MUCH!!!

P.S. I had no idea what to select when I was deleting the old ubuntu partition for the install to 9.04 (there were advanced options that showed hd0,01 or something like that - I didn't know what those were) I bet that was something that added to the problem!
I can get into windows XP fine with the livedvd too and all my settings, files, programs etc etc look as if I was normally using them if I had selected from the grub launcher. I tested ubuntu 9.04 this way and it works too! All only with the Livedvd inside and booting from 1st harddisk option only. Without it, I get the cylinder error message. No problems before prior to upgrading disaster.

---

### Post by Durden on 2009-07-22
Boot the system from a Windows Recovery CD, select "R" for Repair, and then run "fixmbr" (fix master boot record) at the DOS prompt in C:\windows. This will remove GRUB. If you don't have a recovery CD, you can download floppies from Microsoft for XP, see "http://support.microsoft.com/kb/310994".

Read more: [http://wiki.linuxquestions.org/wiki/GRUB#ixzz0M2ALhwL4](http://wiki.linuxquestions.org/wiki/GRUB#ixzz0M2ALhwL4)

This will let you boot windows normally. Additionally you may google "SGRUB" which is a GRUB repair utility I use often. Someone else may have better alternatives than these, but it's what I usually do.

---

### Post by vanco on 2009-07-22
Thanks for the reply!

That was the first link I got to and read - got a little scared because I didn't know what was going to happen. I went to the MS link you sent, and I already have Service Pack 3 installed and don't have a floppy drive... Even if that was the case, what happens once GRUB is removed and my previous Ubuntu installation?


This SGRUB option? What can that do in my situation? 

Also, where or what did I do wrong in the first place to get into this problem so that I never do it again!

---

### Post by Durden on 2009-07-22
Burn scrub to a bootable CD. Allows you to fix GRUB or remove it entirely.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You can read more about it there. I always keep a sgrub cd around just in case.

---

### Post by Choose on 2009-07-22
These pages might be of some help to you
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
good luck ;)

---

### Post by Durden on 2009-07-22
> **vanco said:**
> 
Also, where or what did I do wrong in the first place to get into this problem so that I never do it again!

I have no idea. Did you say it worked before then it just stopped working? Or has it been like this since install?

Error 18 from what I read means the MBR is too small (actual file size) and the recommendations I am reading are making the first partition on the disk just for GRUB. I've never had to do much of this so I'm strictly going off what I found on google here.

---

### Post by vanco on 2009-07-22
My power went out during the upgrade process. So I just went to manually delete the 2nd partition which was Ubuntu 8.10

Both operating systems can be launched now when I have the LiveDVD inside but I have to first boot the cd from power up.
Then select boot from 1st hard disk (I only have one hard disk)
Then the GRUB loader comes up and then I scroll to pick the OS I want and then it loads.


I looked at the links you all had given me, and I'm not sure on how to even approach this, let along what I would have to edit. All these lines in the support documents look very very foreign to me :(

Obviously the LIVEDVD can load my operating systems fine.... 

I'm just shocked at how a botched upgrade has caused my whole day to go off tangent. I'm afraid to save any work or update this laptop now without solving this launching cylinder problem. 

When I used the LiveDVD, I never touched any of the other partitions.
I just deleted the 2nd one and selected " / " as mount and everything else as default. it did however rename my SDA2 to SDA7 if that is any helpful point...

I'm not sure if this is an option that will suit my problem?

[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

---

### Post by Durden on 2009-07-22
Is your linux data backed up? You can just do a fresh install, kill the linux partition and install anew from the dvd. It will install a new grub and all will be well again )aside from the old linux data)

---

### Post by oldfred on 2009-07-22
When you had sda1 & sda2 they were primary partitions. Often swap is added as a extended partition and normally grub can boot from extended partitions (and windows is very difficult). Partitions sda5 & sda7 have to be extended partitions. Some older computers have trouble with the extended partitions and this is what may be the original start of your problems. If you had used manual install to sda2, it would not be a problem. You best bet is to back up all your data, manually partition to keep your windows partition and hopefully not lose it, delete all other partitions, create one primary partition and swap. Then use manual install to install to the new partition. Depending on computer speed you can do the  install in less than half and hour.

---

### Post by vanco on 2009-07-22
This is what I did initially. Ok I dont have anything that I need on the linux partition. I deleted it again (for the 3rd or 4th time today :) )


XP was my 1st. (sda1)
Ubuntu was my 2nd partition. (sda7) 
3rd partition was a SWAP   (sda5)
4th was a EXT3.(sda6)

I went to specify partitions manually and deleted partition #2.
This is where I was confused.

OK, anyways - I am back at this menu with the LiveDVD.
I deleted partition #2 again.

I have a few options for this partition : which ones should I pick now?

Type for new partition : Primary or Logical (initially kept as logical)
New Partition size : I have 100000, so it has 9999 set
Location for new Partition : Beginning or End (initially kept as beginning - maybe this is the problem?)
Use as : Ext3 Journaling system
Mount Point: Should I select "/" or "/boot" ? (maybe this is the problem? I initially chose "/"

I am not touching the other partitions. 
Was there a problem for this partition being named sda7? instead of sda2 like before? I don't see the option to specify this.

---

### Post by vanco on 2009-07-22
> **oldfred said:**
> When you had sda1 & sda2 they were primary partitions. Often swap is added as a extended partition and normally grub can boot from extended partitions (and windows is very difficult). Partitions sda5 & sda7 have to be extended partitions. Some older computers have trouble with the extended partitions and this is what may be the original start of your problems. If you had used manual install to sda2, it would not be a problem. You best bet is to back up all your data, manually partition to keep your windows partition and hopefully not lose it, delete all other partitions, create one primary partition and swap. Then use manual install to install to the new partition. Depending on computer speed you can do the  install in less than half and hour.

I think this is what happened... I kind of mentioned something about that in the previous message.

I deleted the swap file, the other partitions except for windows.
I labeled the one partition as primary @ end in ext3 form
Then set aside ~2gb for the swap 

So now, I have :

sda1 : xp
sda 2 : ubuntu
sda 5: swap

Installing now. Hopefully this will work. My laptop is like from 2000 or 2001 I think.




*************

Update : It seems to work now!!!!! 
Thank you to all the members here for your time and help!
:D

I think I made the mistake of naming my ubuntu partition initially as a logical drive maybe?

I've never been really good at understanding the logical/primary - beginning-end terminology for these partitions.

---


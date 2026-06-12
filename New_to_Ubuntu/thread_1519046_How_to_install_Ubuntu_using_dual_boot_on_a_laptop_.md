---
title: "How to install Ubuntu using dual boot on a laptop with Windows 7 Pro already installe"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by egr9546 on 2010-06-27
I have a new Toshiba laptop with an Intel i5 processor 4 GB RAM and 500 GB HD. I am using 64-bit Windows 7 Pro OS and have lots of programs installed, but still using less than 20% of the on-board HD - I keep non-program data on external HD's. Would like to install a dual boot with the ability to run Ubuntu as alternate boot. Have read the stuff on this site about installing dual boot on an XP system, but haven't seen anything about dual booting a 64-bit Windows 7 Pro i5 system. Can it be done, and if so, how? Thanks for the help. Looking forward to putting some neat Ubuntu apps on my laptop.
 
Best regards,
 
Greg

---

### Post by wilee-nilee on 2010-06-27
> **egr9546 said:**
> I have a new Toshiba laptop with an Intel i5 processor 4 GB RAM and 500 GB HD. I am using 64-bit Windows 7 Pro OS and have lots of programs installed, but still using less than 20% of the on-board HD - I keep non-program data on external HD's. Would like to install a dual boot with the ability to run Ubuntu as alternate boot. Have read the stuff on this site about installing dual boot on an XP system, but haven't seen anything about dual booting a 64-bit Windows 7 Pro i5 system. Can it be done, and if so, how? Thanks for the help. Looking forward to putting some neat Ubuntu apps on my laptop.
 
Best regards,
 
Greg

Are you talking about a real dual boot=separate partitioning or a wubi=inside of windows.

You haven't looked very hard that information is all over the place.

---

### Post by Mark Phelps on 2010-06-28
BEFORE you do anything regarding dual-boot, do yourself a favor and use the Win7 Backup function to create and burn a Win7 Repair CD.  Should you have problems booting Win7 later, that will prove invaluable in repairing the Win7 boot loader.

Also, if you want a traditional dual-boot setup where Ubuntu has its own partition, make sure you use the Win7 Disk Management utility to shrink the Win7 OS partition to make room.  Do NOT use the Ubuntu installer to do the partition shrinking.  Leave the free space as unallocated when you're done.  Then select the "use largest free space" option when installing Ubuntu.

---

### Post by ECET on 2010-06-28
I just did an install like you are talking about. I have windows 7 and ubuntu 10.04 both on my toshiba 505 laptop. All I had to do was download ubuntu to a live cd.....ran ubuntu....selected the install option......and if gives you I think 3 or 4 options to choose from. I chose the dual boot option. I too have a 500G hard drive and I believe it showed me that windows had 202 or so Gig....and ubuntu took 199.7....or something like that. It left some of harddrive space for something else. Now when I turn on laptop I get a screen that has 3 options to load ubuntu.....and 3 to load windows. The options are like safe mode and something else.....sorry about the whole something else thing. I'm not at my laptop now or I would tell you......but I have had NO PROBLEMS whatsoever with this setup.....in fact I use less and less windows now than I thought I ever would.....ubuntu really has it all......I'm still in the very early, infancy, noobe stage, but who cares.....its fun to have something different, more hands on then windows.......give er a try.........):P

---

### Post by waynefoutz on 2010-06-28
> **ECET said:**
> I just did an install like you are talking about. I have windows 7 and ubuntu 10.04 both on my toshiba 505 laptop. All I had to do was download ubuntu to a live cd.....ran ubuntu....selected the install option......and if gives you I think 3 or 4 options to choose from. I chose the dual boot option. I too have a 500G hard drive and I believe it showed me that windows had 202 or so Gig....and ubuntu took 199.7....or something like that. It left some of harddrive space for something else. Now when I turn on laptop I get a screen that has 3 options to load ubuntu.....and 3 to load windows. The options are like safe mode and something else.....sorry about the whole something else thing. I'm not at my laptop now or I would tell you......but I have had NO PROBLEMS whatsoever with this setup.....in fact I use less and less windows now than I thought I ever would.....ubuntu really has it all......I'm still in the very early, infancy, noobe stage, but who cares.....its fun to have something different, more hands on then windows.......give er a try.........):P


Eventually booting Windows will make you feel all icky inside!

---

### Post by egr9546 on 2010-06-28
Yes, separate partition.  Perhaps you could stear me as to where to find info - have found it for XP, but not for 64-bit Windows 7 already installed.  Thanks for any help.

---

### Post by egr9546 on 2010-06-28
Thanks for the info - anything specific about 64-bit Windows already installed - does it make a difference that I am using as 64-bit Windows OS currently?

---

### Post by egr9546 on 2010-06-28
Thanks for the roadmap - appreciate your experience on a similar system.

---

### Post by egr9546 on 2010-06-28
And on the outside . . . ?

---

### Post by oldfred on 2010-06-28
Herman has a variety of graphical examples on dual booting.

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

He says the gparted inside the installer does not cause any issues with win7, but we often suggest using the windows tools to shrink the win partition (leave at least 20-30%) and reboot windows to let it adjust to its new size. It usually runs chkdsk to make sure new size is ok.

Then you can just install to the largest unallocated space left. It will create standard / (root) and swap. 

Only if you want more control you can manually create partitions and then choose sizes and additional partitions. But for a first install that is not required. I ran with the defaults fro 3 years, but did create a shared partition for data that I wanted with both windows and Ubuntu.

---

### Post by sprocket10 on 2010-06-28
I've done this. It's possible.

1) backup windows files
2) make windows 7 recovery cd (as mentioned above)
3) use windows partition tool to shrink windows partition (as mentioned above, you MUST use the windows tool, NOT ubuntu's!!!), making at least room for an ubuntu install. you may want to setup a shared, data partition. it's up to you and there are several threads about it - including one of mine.
4) run ubuntu liveCD or USB and install. Install to the empty partition. If you let it install itself, it'll automatically setup a SWAP for itself. If you wanna do the shared partition thing, then use the "advanced" partitioning tools to setup the ubuntu partition, swap, and ntfs shared partition. 
5) stay in ubuntu and download all the updates in the Update Manager (~ 190MB download for me).
6) THEN restart, and you should see both ubuntu & window7 in the GRUB loader screen!

- The first time I tried this I had trouble w/ the bootloader for windows. The two mistakes I made were using ubuntu's partition tool instead of win7's to shrink the windows partition AND I didn't download the updates the first time! 

BUT, the second time I did my install following these steps and everything worked  correctly! No bootloader errors. No need for the recovery CD.Better safe than sorry though!

Good Luck!

---

### Post by ECET on 2010-06-28
My version of windows is windows 7 home premium 64bit.......so I installed ubuntu 64bit......if you are not sure where to get the live cd???.....just go to ubuntu download page.....click on 64bit live cd.....then, before you install, just run the live cd for a few days and see what cha think....thats what I did, and then I installed it while I was running through it one day and I swear I have not looked back.......

---


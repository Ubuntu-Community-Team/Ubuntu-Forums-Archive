---
title: "Dual boot or Virtual machine installation?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Wayne Twine on 2009-05-18
HI folks
 
I am ready to test the water with Ubuntu and FOSS as an alternative Windows XP and MS software. However, having used Windows all my student & working life, I am a bit nervous about making a clean break from Windows all at once, and would like to rather transition cautiously. I'm sure that once I have finally cut the "umbilical cord", I won't look back, but in the mean time, I want to still be able to access Windows while I learn Linux/Ubuntu. I also use some specialised scienific software that only runs in Windows (I doubt Wine will help).
 
From what I have read on ubuntu formus etc, there seem to be 3 options available to me:
1) Install Ubuntu on my machine as a dual boot, so that I can choose whether to boot up in Ubuntu or Windows.
2) Install Ubuntu on a virtal machine (using Virtualbox) within Windows.
3) Unintsall Windows, install Ubuntu, and then install Windows on a virtual machine within Ubuntu.
 
Number 3 probably makes the most sense in the long term, especially to Ubuntu converts, but it is very scary for the likes of me!
 
Here's my question: 
 
What would you recommend is the best way to make the transition, for somebody who is new to Linux/Ubuntu and is not a computer whizz kid?
 
In addition, would any/all of these options allow me to access my current files once I'm in Ubuntu (e.g. MS Word files which I might want to import into Open Office)?
 
Thanks, and apologies if these are dumb questions.
 
WT

---

### Post by BaldurK on 2009-05-18
First of all, welcome outside the box. It's not long since I set up Ubuntu for the first time (two months) so I'm happy to give you some advice.

The approach you suggest, taking it in small steps, makes sense. I would not recommend a WUBI installation (installing Ubuntu within Windows on a virtual partition) but you don't mention it anyway so it shouldn't be a problem. The transition could be something like this:

1) Try out Ubuntu using the Live CD (burn the CD and choose the option "try out") OR by setting it up in a VirtualBox under Windows. Either way, you'll see whether you like it and if it works with your hardware.

2) If you want to proceed with a real installation (why not?) you can shrink your Windows partition (using Windows) and then set up Ubuntu on a new one (the partitioning step in the Ubuntu installer is quite user friendly). There you have dual boot.

3) If you then feel comfortable with Ubuntu and can live without Windows except for the occasional access to a Microsoft lock-in application (for me it's proper access to Windows Media streams, IE-specific web apps, Office 2007 and Visio) you can indeed let your Windows partition go and set up a VirtualBox with Windows as a guest OS. It's more convenient than always having to reboot to go to the other OS.

I would also highly recommend that you read the Ubuntu Pocket Guide and Reference by Keir Thomas. It would have helped me a lot at the time instead of having to go through all the trial and error. It's available for free as a PDF (just google).

Good luck!
Baldur

---

### Post by Wayne Twine on 2009-05-18
Thanks for the reply.
 
After posting my query, I came across the WUBI option while searching the internet and was considering it, but will take your advice and rather use Live CD or Virtualbox.
 
I'll also check out Thomas' book.
 
And so the adventure continues....

---

### Post by BaldurK on 2009-05-18
You're welcome. 

Come to think of it, Wubi and Ubuntu as a guest OS are not that different actually. The Wubi one will even do more towards trying out your hardware. In either case, just think of it as a trial setup and don't become too attached to it :) since neither will work as a real, full-blown OS for your computer.

-BK

---

### Post by swoody on 2009-05-18
Hi Wayne Twine, and Welcome to Ubuntu and the Forums ):P

I would highly recommend testing out a LiveCD on your computer first, before diving all the way in. This will give you a good estimation of how your hardware will be supported during a full install. When you feel comfortable enough to go ahead with the actual install, I would go for a dual-boot option. Since you are going to be changing your partitions, there is **always** a chance that you may lose data, so be sure to make any backups or copies of anything you don't want to risk losing. When you prepare to install Ubuntu, use Windows to clean up old files, defragment, and then shrink your Windows partition (only available if you're using Vista) otherwise using the Ubuntu install disc to shrink your Windows partition will be a good way to go. I feel a dual-boot would give you the best balance between Ubuntu and Windows, and will be a nice common ground if you decide to get rid of one or the other in the future for whatever reason.

As far as sharing files, I know that it is very easy to share files between Ubuntu and Windows, but I have not done it myself, so hopefully someone more knowledgeable can chime in here with some details about that. 

You may want to check out the first two links in my signature. The first one is to a great resource of vast amounts of info about Ubuntu designed to help beginners. The second link is actually to the Ubuntu pocket guide that baldurK mentioned above. It's a *great* resource to have on hand while you're learning about, and getting used to Ubuntu. It truly does have a great amount of information, and would be great if you could print out a copy to keep on hand near your computer, or just save the .pdf file on your computer to use as a great reference source. 

Again, Welcome to Ubuntu, and if you have any other questions, please don't hesitate to ask :D

---

### Post by Wayne Twine on 2009-05-19
Thanks Baldurk ans Swoody
 
Some more questions:  
 
My PC has 2 IDE drives (each 111 GB).  It boots from the c: and I use d: to backup data.  About 80 GB free on each at the moment
 
1) Should I install Ubuntu on the d: drive, or install it on a new partition on the c: drive?
2) If I have the 2 OS installed on 2 different drives, how do I select which OS to boot in, as I assume it will boot form the c: by default?  (I read some related postings in this and other forums, but they were too technical - I don't know what a GRUB is and have never fiddled with BIOS before - so please be patient with me).
 
On a simpler topic:
 
Being too impatient to wait for my Ubuntu CD to be shipped to me , I have tried downloading the Ubuntu 9.04 .iso from the Ubuntu website, via our wireless internet connection.  After it has downloaded about 60 Mb of the 700 Mb file, it stops and copies the downloaded file to the drive I specified.  Ay idea why it does that?  Could it be a bandwidth problem, my machine, or ....Windows XP... giving the problem?  Any way around it
 
Cheers

---

### Post by sim-value on 2009-05-19
Which browser are you using ?

You might want to try torrent download ...

---

### Post by Wayne Twine on 2009-05-19
Hi Sim-Value
 
Do you mean internet browser - I'm using IE.  Should I try Firefox?
 
Excuse my ignorance, but what would be required for a torrent download?  Do I need to downlaod software to do this?
 
Thanks

---

### Post by BaldurK on 2009-05-19
I agree with those above, try Firefox or torrent download (go to torrentz.com, search, open the file in a program such as uTorrent).

Regarding the partition, I hope there's not any miscommunication, but I would recommend that you keep the D: as an NTFS partition for data, and shrink the C: partition if you possibly can. Then make a new EXT3 (EXT3 is the Linux file system) partition for Ubuntu when you install. You can then use the D: volume as a shared volume for both Windows and Ubuntu quite comfortably.

I also totally agree that starting the Live CD is the quickest way to try Ubuntu hands on and see if it works 100% with your hardware. You can then go right away for dual boot, just make sure that anything that has value is backed up to D: and even a DVD before you proceed with repartitioning C: Things have never gone wrong for me personally but it doesn't mean there can't be some random accident occurring on someone else's disk.

-Baldur

---


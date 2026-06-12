---
title: "Wired network issue, error on file transfer to windows box"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by baconstrip on 2007-05-08
So I have a box set up for a dedicated BT download box using remote desktop and such.   It is an old machine running Feisty, runs pretty slowly but does the job..  P3 800 with 512meg of ram and an 80 GB WD.  The 80 GB has a FAT32 Partition of like 65 GB.

So I've been downloading a lot of shows and stuff onto the machine, and transferring it over the network to my  windows storage box.  Its an NTFS partition..

My main problem is that most of my file transfers to the Windows box end up failing halfway through.  It comes up with an error just saying there is an error.   I've found myself having to transfer only a few files individually at a time, and thats a big pain!  I'm curious as to why my file browser is having difficulty... sometimes it actually just locks up without an error message and  I have to Force Quit.

Anyone know why this is the case?  I've resorted to transferring files onto my 16gb memory stick and then over to my windows box because I can do large scale transfers with no problem to the stick.  Problem is the USB ports are not 2.0... so transferring a full 15ish gigs takes like 5 hours.

Anyone have any clue as to what the problem is?  I'm doubting it has much to do with the fact that the computer is so slow.. the hard drive is still speedy and it shouldnt be the problem. 

Any help would be greatly appreciated... thanks in advance!

---

### Post by spd106 on 2007-05-09
Which protocol are you using to transfer the files?

I have experienced timeouts with SMB and found FTP or SSH to be more stable. SSH will be slower (due to encryption), but I have found it to very stable and it will still be quicker than manual. FTP will probably be the best and quickest, it will take some setting up though.

---

### Post by baconstrip on 2007-05-10
I'm just browsing to my windows box from Places>Network ... and copying and pasting to the windows drive using the default file browser.

I may just have to set up SSH or an FTP..  Hopefully one or the other will allow me to transfer on a larger scale and not a few files at a time.

Thanks!

---


---
title: "Computer does not recognize DVD-R is in drive"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Unstuck on 2009-11-10
I'm trying to burn an ISO image to a DVD, but my computer does not recognize a DVD-R is in the drive.

---

### Post by Mariane on 2009-11-10
If you use k3b try brasero instead. 
First you save the image on your hard disk somewhere
Then you put in the blank disk
Wait a while and it should open a window asking you what to do with it. 
Choose "open in new window" if there is this option
If there is not choose "do nothing"
Go to /media and see if you see the CD
Then you open brasero
You select "burn image"
You open the image file

Mariane

---

### Post by Unstuck on 2009-11-10
The problem is that neither K3B nor Brasero recognize a disc in the drive.

---

### Post by Mariane on 2009-11-10
Maybe something is wrong with the drive? Or with the blank disk? 

If you have KDE, what happens after you insert the disk? 

After you insert, type dmesg|tail and post what it says

Also says what you see in /media

Mariane

---

### Post by Unstuck on 2009-11-10
I tried a few discs, so I don't think it's that.  I've not tried to burn a DVD before, so it's possible it is the drive.

When I put a disc into the drive and close it, you can hear the motor start and disc spin, but it isn't recognized.

---

### Post by Mariane on 2009-11-10
And no windows opens on your desktop when you insert it? 

Before inserting:

Open a terminal window
type
cd /media
ls

and tell what you have there

type
dmesg | tail

and tell what it says

Then you insert the disk and you do both things again

Mariane

---

### Post by Unstuck on 2009-11-10
BEFORE DISC IS INSTALLED

cd /media
ls
> /media$ ls
cdrom  cdrom0  Expansion


DMESG | TAIL
> dmesg | tail
[23320.345357] Buffer I/O error on device sr0, logical block 1447926
[23320.345363] Buffer I/O error on device sr0, logical block 1447927
[23320.345370] Buffer I/O error on device sr0, logical block 1447928
[23320.345374] Buffer I/O error on device sr0, logical block 1447929
[23320.345378] Buffer I/O error on device sr0, logical block 1447930
[23320.345383] Buffer I/O error on device sr0, logical block 1447931
[23320.373560] end_request: I/O error, dev sr0, sector 5791768
[23320.415968] end_request: I/O error, dev sr0, sector 5791704
[23320.420434] end_request: I/O error, dev sr0, sector 5791704
[23320.422769] end_request: I/O error, dev sr0, sector 5791704


AFTER BLANK DVD-R IS INSTALLED

ls
> /media$ ls
cdrom  cdrom0  Expansion

DMESG | TAIL
> dmesg | tail
[23320.345357] Buffer I/O error on device sr0, logical block 1447926
[23320.345363] Buffer I/O error on device sr0, logical block 1447927
[23320.345370] Buffer I/O error on device sr0, logical block 1447928
[23320.345374] Buffer I/O error on device sr0, logical block 1447929
[23320.345378] Buffer I/O error on device sr0, logical block 1447930
[23320.345383] Buffer I/O error on device sr0, logical block 1447931
[23320.373560] end_request: I/O error, dev sr0, sector 5791768
[23320.415968] end_request: I/O error, dev sr0, sector 5791704
[23320.420434] end_request: I/O error, dev sr0, sector 5791704
[23320.422769] end_request: I/O error, dev sr0, sector 5791704


---

### Post by Mariane on 2009-11-10
Thank you. Hum. When I do this dmesg says (last line):
[25889.175005] cdrom: This disc doesn't have any tracks I recognize!

But your dmesg doesn't say anything about it at all... Not even an error... 
Maybe something is wrong with the drive, I hope someone will answer who knows more than I do on this subject. 

Mariane

---

### Post by tacantara on 2009-11-10
> **Unstuck said:**
> I'm trying to burn an ISO image to a DVD, but my computer does not recognize a DVD-R is in the drive.

I had a similar problem when I was trying to copy the Karmic ISO.  Assuming that your drive is capable of recording to DVD media, it may just be a compatibility issue.  When I replaced the non-working DVD media and replaced it with a CD R/W, I was able to copy the image.  At the time, I had a 5-pack of DVD-R from a national retail office supply store (the DVDs were under their brand name).   The CD-RW disks I had available were a name-brand, and I paid a bit more for them.

When you buy "store brand" discs, you're basically rolling the dice and taking your chances, as the disks are normally made by the lowest bidder.

Hopefully this information helps.  Good luck :)

---

### Post by Unstuck on 2009-11-11
The mystery is solved...my CD/DVD drive will write to CD-R(W) but not DVD-R. Oops.

Now, I'm looking at external drives on Newegg.  Do I have to be aware of compatibility issues with an Ubuntu system?

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010100420&bop=And&ActiveSearchResult=True&Order=RATING](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010100420&bop=And&ActiveSearchResult=True&Order=RATING)

---


---
title: "Hard Drive Recovery"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by broken sword on 2009-02-03
A little background:
Saturday, my gf's 160gb usb Maxtor drive crashed.  She uses windows, when the driver is connected, the computer picks it up ( i.e. the "safely remove hardware" icon is available. But, no data could be found.
I used my ubuntu live cd ( intrepid ), booted the computer and connected the drive ubuntu could not pick it up.  I opened the case, and removed the hard driver ( luckily it was an IDE drive, and connected it to the computer).  I noticed that as the ubuntu live cd booted, it picked up I/O errors from the drive.  Which I thought was a good thing, because in a case like that a program should be able to get something from it.  I used ddrescue the first time around, let it run over night and got nothing but 260 KB of data.  And a frozen computer, this is after I compiled ddrescue in the live cd environment.  I figured that it would be better if the program was already installed, I did some research and found rescue remix. I connected the drives and ran ddrescue, now I have a problem.
Here's the setup:
Dimension 2400
160 GB IDE drive ( the bad driver ) set as the primary drive.
1 TB usb drive connected to computer.
1 CD-ROM of course.
I ran the following:
mkdir mnt
sudo mount /dev/sdb1 mnt
mkdir recovery
cd recovery
sudo ddrescue -r 3 /dev/sda1 /dev/sdb1 image log
( i may have left '/dev/sdb1' out, dont' remember clearly, didn't get much sleep last night )
I started this @ 11 pm, let it run till about 8 am.
It's now stuck in a loop.  The msg is constant:
[xx,xx] end_request: I/O error, dev sda, sector xxx
Where 'x' keeps increasing, the text is moving by too fast for me to see, but I can see that is says that roughly 50,000 kb was recovered.  Should I just let it run its course? Or should I give up and try a professional?

---

### Post by Coreigh on 2009-02-03
Sanity check; Make sure the drive is set as single or cable select, is on the cable by itself (no other hard drives on the same cable) and is on the _end_ of the cable.

Then boot the LiveCD, open a terminal and run this command (it reports all drives and partitions it can find):
```
sudo fdisk -l
```

You will probably want to have the external USB drive _dis-connected_ to minimize confusion.

Please post what is found.

---

### Post by broken sword on 2009-02-03
I will do so as soon as I get back to her house.  I did run fdisk -l, and it recognized both drives.  160 GB as /dev/sda and 1000.2 GB as /dev/sdb, but again I will post an exact msg later.

---


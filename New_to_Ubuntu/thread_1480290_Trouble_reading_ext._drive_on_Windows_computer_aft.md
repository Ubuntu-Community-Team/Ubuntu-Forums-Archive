---
title: "Trouble reading ext. drive on Windows computer after retrieving files from Ubuntu"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by Waltermcswartz on 2010-05-11
My skill level with Ubuntu I would rate as being very novice.  I have some basic knowledge, but other than that, I am not very handy with it.

To my problem--

I use my Ubuntu machine as my primary source for downloading files, as it is wired to the network whereas my Windows machine uses a shoddy wireless card that will drop the connection during any downloading requiring any extreme amount of bandwidth.

As my Windows machine is what I'm usually using to screen movies and enjoy other media, I need the files from my Ubuntu machine.  I usually end up getting the files from computer to computer by ferrying my external hard drive between the two whenever it is convenient.  

Up until a few days ago, this had been working fine; no problems.  The transfer and reading of the files was seamless.  However, several days ago, I had dropped an 18GB folder into the external hard drive, but once connected to my Windows machine, the drive merely crashed Windows Explorer and asked if I wanted to reformat the drive.  After several tries, this was the only result.  

The drive still works on the Ubuntu machine, though.


I did post on 4chan's /g/ (Technology) board last night in hopes of a quick fix, but the only helpful response I got, I do not completely understand.

>     >>10374962
    fsck the filesystem
    then sync;
    before you remove it Please lend me a hand with my issue.  Thank you for reading.

---

### Post by mbzn on 2010-05-11
If you are behind a router you could try 'samba' it shares like windows(and is vulnerable) or create n nfs partition and mount that to both win and linux.

As for the external drive (if you are sure you unmounted it). I don't know..

---


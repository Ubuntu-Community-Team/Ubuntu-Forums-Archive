---
title: "changing partition size"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by albert s on 2010-03-16
hi, after having removed an 80g HD from my other machine I put its own 40g drive back in,
XP and Ubuntu 9.10 dual boot.
Ubuntu works perfectly, wi-fi, ethernet,DVD player & graphics all spot on.
XP wont work properly with any of them, this is the machine I was originally given because XP went all funny and wouldnt work properly,
I have re-installed XP onto about 20g of the HD, then installed Ubuntu onto the other 20g with about 10g /   9g/home  and 1g/swap  ,
Im just going to put ubuntu on the whole drive now as it simply works better, and the only reason I kept the XP was for the printer(lexmark), and as I have an HP on its way soon I hopefully wont need it anymore.
OK, so do I just move and then enlarge my partitions using Gparted from the live CD?
(the point at last.!!!)
Im wanting to delete XP completely and use the whole drive for Ubuntu.
thanks, and sorry for rambling.....

---

### Post by tchoklat on 2010-03-16
Just load the liveCD, run GPartEd, highlight the Windoze partition and delete it, then expand the Linux partition to cover the full drive.
 
Should be no problem.

---

### Post by audiomick on 2010-03-16
Hi Albert.
Essentially, yes, that is right.
Here is a short guide
[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)
The only thing is, the bit about editing grub is outdated. I assume you have a fresh-installed 9.10, and not one that was updated from an older version. That would mean you have grub2 on the machine, which doesn't have the menu.lst file anymore. You should be able to fix the grub entries simply by doing
```
sudo update-grub
```
as far as I know.

Have a look also, if you haven't already seen it, at the link at the bottom to "how to partition".

One thing that I don't find all that intuitive is:
When you delete you windows, you will probably have empty space "on the left", ie. at the start of the drive. If you want to add this space to, for instance, the second of the remaining partitions, i.e. one that is not adjacent to the empty space you have to
expand the  partition adjacent to the space into the empty space
shrink it back down to create empty space between the first and second partition
expand the second partition into the empty space.


Hope that all helps you.

---

### Post by aeiah on 2010-03-16
the master boot record might be sitting at the start of the windows partition.. but this is grub2 probably, and things may be different. either way, yes, your method is correct, but you might have to do some grub fixing afterwards to boot into ubuntu. shouldnt really be an issue.

if you havent installed too much stuff, you could always reinstall ubuntu if things go wrong, keeping your home partition as it is.

---

### Post by albert s on 2010-03-16
thanks all, esp audiomick,
yes, I have a new install, just think its a waste of time as my XP is still messed up,
is this a 1st where ubuntu actually works better than windows out of the box?
I will have to move my  / partition left, then reshrink it again then expand my  /home ,
my partitions are XP  /   /home   /swap
thanks for the help.  :D

---


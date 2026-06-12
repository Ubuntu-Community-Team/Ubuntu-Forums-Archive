---
title: "Ubuntu installation partition booch"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by AtariRaccoon on 2009-09-21
Yeah, I just installed Ubuntu and actually quite happy with it.  But OOPS <facepalm> using the disk to install it as a dual boot, I didn't have the option to alter the size of the partition.  And after using it for just a bit, woops, out of space.  So I need to find out the easiest way to enlargen the partition size.  Would Cute Partition manager be sufficient when run on boot time, or is there something I missed on the insalation disk I can still use without reformatting the partition, resizing, then reinstalling Ubuntu.

And yeah, I'm gonna take an aside to say that I am impressed with Ubuntu compared to all my experience with <cough>windows</cough>, but I guess I'll be fine having a dual boot since I do a little bit of gaming and programming with some things that aren't available in Linux :(    I was amazed when Ubuntu, on installation, didn't ask me for drivers for my monitor, audio card, etc etc, and even instantly detected my internet connection.  Wonderful install, aside of the goof up of the partition size x.x .

---

### Post by marshmallow1304 on 2009-09-21
1. Boot into Windows and defrag (at least once, maybe twice)

2. Boot the Ubuntu Live CD and select "Try Ubuntu without..."

3. System -> Administration -> Partition Editor (gparted)

4. Shrink Windows and enlarge Ubuntu.

5. Shutdown, take out the CD, and reboot into Ubuntu.


If you need more help, take a screenshot of your gparted and post it.

---

### Post by raymondh on 2009-09-21
> **marshmallow1304 said:**
> 1. Boot into Windows and defrag (at least once, maybe twice)

2. Boot the Ubuntu Live CD and select "Try Ubuntu without..."

3. System -> Administration -> Partition Editor (gparted)

4. Shrink Windows and enlarge Ubuntu.

5. Shutdown, take out the CD, and reboot into Ubuntu.


If you need more help, take a screenshot of your gparted and post it.

Couple of notes/iterations on above:

1.  Back-up your files
2.  Though I am a fan of gparted, it is suggested to use the Vista disk management tool to shrink a vista partition.
3.  If you use gparted, make sure the partitions are unmounted.  It ought to unmount automatically but just doublecheck by right clicking and if given the option to unmount, do so.  For swap, select swapoff.

All of this is assuming that Vista and ubuntu root are beside each other.  If swap is in between, then there is some "moving" to do.

---


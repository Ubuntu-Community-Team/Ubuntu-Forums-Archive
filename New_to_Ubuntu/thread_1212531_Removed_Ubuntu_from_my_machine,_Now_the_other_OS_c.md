---
title: "Removed Ubuntu from my machine, Now the other OS cannot see the freed space"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by jdarias on 2009-07-13
Hello.
Sadly, I had to remove my ubuntu installation from my dual booting machine to allow for more space in the other OS´s partition.
I deleted both the ubuntu and swap partitions, and then i resized the other OS´s (it´s ntfs). (had some trouble later with GRUB error 22 but I sorted it with the other OS´s recovery options)
Despite all this, the other OS still reports its partition has 9.5 gb, it should be 18-18 gb with the added space.
I did all this with parted magic. Clearly, it is not an Ubuntu issue, but i was hoping someone overhere could help me solve this. Otherwise, deinstalling ubuntu (wich i pondered a lot before making the sad desicion) would be useless...

---

### Post by LewRockwell on 2009-07-13
which OS?

.

---

### Post by Revolutionary101 on 2009-07-13
Deleting Ubuntu and its swap space isn't automatically going to give you extra space in the other partition. You need to resize your other operating system's partition to take up that space that was freed by deleting Ubuntu.

---

### Post by decoherence on 2009-07-13
OP says the "other OS" is using NTFS, so I can only guess it's at least NT ;)

Surely Windows has a utility to resize a partition? I mean, the thing is so damn expensive... it MUST, right?

Despite my 'witty' tone, that's my advice. Resize the partition from within Windows, however you do that. Good luck! (hopefully someone knows better)

---

### Post by lkraemer on 2009-07-13
Well, I'd suggest that you go to [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
and download gparted.  Burn the ISO as Disk at Once (DAO) at the
slowest speed with K3B, and then boot it.

You should see all the partitions.  Original OS size xx, and
possibly the old Ubuntu partition along with the Swap partition,
if those should still exist.  If so, delete them.  (You will have to
turn the Swap partition OFF before deleting it.)  Then you should
have un-allocated space.

Expand (re-size) your Original OS Partition to what is needed.

Reboot, and let the Original OS find the resized partition.

You should be good to go.

An easier solution would have been to purchase a larger Hard Drive,
Use Clonezilla to copy both partitions, make a new Swap partition,
then resize both to what ever sizes you need. ......Done with less
heartburn than you have now, and you would have still had Ubuntu.

Keep in mind the following website when you get your larger drive
and want to go back to dual booting.

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

You might also need the software "Supergrub" to repair your
Master Boot Record (MBR) if it gets messed up.  This makes it
an easy fix.

lkraemer

---

### Post by SunnyRabbiera on 2009-07-13
You could just reformat the blank space as a NTFS drive with Gparted, and give it a label so Windows can see it.
Gparted live or even your Ubuntu disk can do this.
My advise though: get a bigger drive :D

---

### Post by LewRockwell on 2009-07-13
in XP:

Start > All Programs > Administrative Tools > Computer Management

Once in the Computer Management window you will select "Storage" and then from the sub-menu "Disk Management"

Then you can use the "show/hide console tree" to get rid of that annoying tree

From there you'll need to experiment to see what you can figure out

.

---

### Post by wojox on 2009-07-13
What os are you using?

---

### Post by jdarias on 2009-07-13
Got it sorted!
Turns out i needed to do a Check in Gparted on the resized partition, so the other OS do a chkdsk at boot time and recognize the new size of the partition.
So it´s fixed now. And BTW, i love Ubuntu, and free software, but i have this old toaster with just 40 gb of space that i got circa 2001 (I´m a graphic designer, and work has been bad these times). Got to wipe it out to get more space for these large adobe apps. Having both oses was not paying, so i had to favor the one that brings the money onto the table (m$). For the record it was a very sad and hard decision. So no goodbye to ubuntu, just see you later!
I still use Ubuntu Server in an old laptop, and a lot of free softwares in the other OS.

Decoherence: You cannot resize or do anything to the windows partition within the same windows. won´t let you.

Thanks for the link, Ikraemer!

---


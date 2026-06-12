---
title: "Installation trips"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-12-28
HI there,
Sure this has been asked a thousand times, but if I enter setup and there is no side-by-side option, then how can I add a partition to my existing windows (vista) partition to dual-boot? 
Thanks for considering,

---

### Post by plusnplus on 2009-12-28
Hi hungryOrb,
maybe your harddisk don't have empty space for other partition.
first, you need to shrink the windows partition.(back-up your data before do it)
then try install ubuntu again.

---

### Post by wojox on 2009-12-28
You should be able to from 9.10. I can't remember the exact way from vista, but you can shrink the partiton from within vista and add install that way from the CD. 
Make sure you run defragmenter and check disk first.

---

### Post by SPazzo on 2009-12-28
This video should help you: [http://www.youtube.com/watch?v=v9SUEH27EDk](http://www.youtube.com/watch?v=v9SUEH27EDk)
(I hope I posted the right one.  This computer doesn't have speakers.  :P )

---

### Post by hungryOrb on 2009-12-29
here's a screenshots!

Just want to create dual boot.. but how to make a new partition while keeping the old?

---

### Post by thatguruguy on 2009-12-29
Here's a handy tutorial: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Mahngiel on 2009-12-29
your /sda1 partition formatted at fat32 is your windows preload, this is what you use to restore to factory specs.

/sda2 is your windows partitions.

using your disc as a liveCD (not installing inside of windows) open a terminal and 'sudo gparted'.

you can then shrink your /sda2 to a smaller size.
create a new partition formatted ext4 after /sda2 to whichever size you'd like. I'd say about 20 gb is a fair size to try out. then, when you visit the installer again, you can set up a dual boot by installing ubuntu onto the blank partition

---

### Post by Mahngiel on 2009-12-29
by the way, is that an extended harddrive you have connected, or do you have two hard disk drives?

---

### Post by thatguruguy on 2009-12-29
He doesn't need to use gparted to resize his Vista partition; Vista can do it.  [Here's how]("http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista").  He should, of course, back up his data and defrag his drive first, all of which he can do from within Vista.

---

### Post by Mahngiel on 2009-12-29
> **thatguruguy said:**
> He doesn't need to use gparted to resize his Vista partition; Vista can do it.  [Here's how]("http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista").  He should, of course, back up his data and defrag his drive first, all of which he can do from within Vista.

Cool, then. Never used vista, so didn't know it could format the partition it sat on while it was mounted.

---

### Post by hungryOrb on 2009-12-29
Thankyou very much!

---

### Post by hungryOrb on 2009-12-29
Ah guys, seems there isn't enough space free on the main drive, how about if put Ubu on a spare? It connects with USB, and it has a partition available. Can the live cd installation detect the windows partition and install dual-boot with ubu on the separate hard drive?
Thanks for help! invaluable!

---


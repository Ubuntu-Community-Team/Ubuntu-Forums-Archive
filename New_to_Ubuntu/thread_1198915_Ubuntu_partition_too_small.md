---
title: "Ubuntu partition too small"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by geirknappen on 2009-06-28
When I intalled ubuntu on my first computer I had made 30gb free space partition from xp before intall. No problems. Then I decided to install on my laptop too (vista), and I chose the option to install them side by side (did not make partition first). Now ubuntu has less than 300mb free space (not enough to install ubuntu update)

What is the best thing to do? I need at least 2 gb free space ubuntu.

---

### Post by rraj.be on 2009-06-28
Check your Trash Folder.

Delete the contents if you don't need them.

---

### Post by Cato2 on 2009-06-28
Not sure of your setup here - did you use the "Wubi" installer on your laptop, which installs Ubuntu in a big file on top of the Windows filesystem?  If so, I'm not sure how to expand that file - search for Wubi help on this.

Assuming you did repartition your laptop hard disk and it's just that the Ubuntu partition is too small, have a look at this: [http://partedmagic.com/](http://partedmagic.com/) - Parted Magic is a Linux Live CD that's aimed at precisely this problem and is very easy to use.  Once booted, you use the graphical GPartEd tool like this: [http://partedmagic.com/documentation/119-using-gparted.html](http://partedmagic.com/documentation/119-using-gparted.html)

I would recommend you defrag your Windows partition first (JkDefrag is excellent for this, and free - install JkDefragGUI if possible, it will install JkDefrag for you).  Also, please run a disk check on Windows (right-click on the drive icon under My Computer to find this.

Also, PLEASE back up any files on the laptop that you don't want to lose - partitioning always has a small risk of losing the whole disk, though usually it works just fine.

---

### Post by Paul T. on 2009-06-28
> **geirknappen said:**
> When I intalled ubuntu on my first computer I had made 30gb free space partition from xp before intall. No problems. Then I decided to install on my laptop too (vista), and I chose the option to install them side by side (did not make partition first). Now ubuntu has less than 300mb free space (not enough to install ubuntu update)

What is the best thing to do? I need at least 2 gb free space ubuntu.

I had exactly the same problem when installing from the Live CD, I'd allocated a 20+ Gb partition for Ubuntu but it only created a tiny partition for itself. I then attempted to expand the partition by booting from the CD and using Gparted (partition manager on system > administration menu). Although apparently successful Ubuntu wouldn't re-boot..... :confused:
Long story but I finished up by re-partioning drive before installing Ubuntu, took me several attempts to get it right though, and then using the advanced partioning options on Ubuntu install.
Too complex for me to explain on here, but I found "Ubuntu Kung Fu" book helpful.

---

### Post by geirknappen on 2009-06-29
> **Cato2 said:**
> I would recommend you defrag your Windows partition first (JkDefrag is excellent for this, and free - install JkDefragGUI if possible, it will install JkDefrag for you).  Also, please run a disk check on Windows (right-click on the drive icon under My Computer to find this.
 

I used jkdefrag but im not sure if i defragmented the right way. Its a green defragmented area in the bottom, and then a black area, then a red area that was not defragmented, and then a black area again. Chose the analyze, defragment, fast optimization action.

... will try to use re-partition method (but I know very little about defragmentation)

---

### Post by ajgreeny on 2009-06-29
Start vista in safe mode if you can and defrag a couple of times.  Now in vista's own disk management, shrink the vista partition, leaving some free space in front (I hope) of your ubuntu partition.

Now boot the ubuntu live CD and using gparted (System>Administration>partition Editor) resize your ubuntu partition to fill that space, ie move the left end further left as far as you can.  This will possibly take a long time as it is effectively copying and re-writing your whole partition, but it should work without problems.  Backup first, just in case, as you never know what might happen

---

### Post by geirknappen on 2009-06-29
This is how I solved it:

Used super grub cd to remove ubuntu from grub, leaving only vista. Deleted ubuntu partition from vista. Removed 20 gb from vista partition to free space. Used live cd installed ubuntu on to the free space. Chose the -install ubuntu on largest continuos free space- option (instead of the install side by side option. I still have the option to start beteween vista ubuntu at startup).

---


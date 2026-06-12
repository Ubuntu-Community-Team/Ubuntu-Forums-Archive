---
title: "[SOLVED] Defragementation"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by mkvnmtr on 2008-12-23
After doing a bit of work with GParted I noticed that when it is moving apartition at the end of the process it expands the system to fit the partition. I was not sure what that meant. If it is filling the partition with empty space for the system to grow it would make defragementation of no value. I had always assumed that the files in a system were next to each other with no space in between and then as you used your system the bot more and more spread out. But if the Linux way is to fill the partition to start with it certionly makes no sence to defragment. Can anyone that knows shead some light on this. Maybe I am misunderstanding what iI saw in the log of GParted.

---

### Post by Duck2006 on 2008-12-23
10.4 i think this is what your looking for.

[http://tldp.org/HOWTO/Partition/appendix.html](http://tldp.org/HOWTO/Partition/appendix.html)

---

### Post by mkvnmtr on 2008-12-23
Yes that explained it in a wayeven I could understand. I had found I liked to defragment my Mac and was having trouble believing when people said you never need to do Linux. No one had ever explained why you don't need to. Thanks


I don't think I will mark this solved for a while. Other folks should see your link.

---

### Post by Kellemora on 2008-12-23
Hi MK

The simplest way to visualize how the file system works is to think of it as something else.

In Windows NTFS file system.  The files are stored like beads on a string.  Each new file gets added to the string.  Then if you go back and change a file, the changes get stuck on at the end of the string.  So you end up with a file looking something like this.
AAAAABBBBBAAACCCCCCDDDDDBBBCCAACCBBBAAA
Where A is a single file that has been changed 3 times.
B is a single file changed twice, etc.

In Linux the file system is more like a big wall of pigeonholes.
When you save a file, it plugs it into a pigeonhole FAR AWAY from the last pigeonhole that was used.
When you change a file, it gets stuck back into the same pigeonhole it came out of, so it's NOT fragmented.
Files you use most often get written closest to the drive heads and files you use very seldom get moved to the outskirts of town so to speak.  This makes the system run much faster.
If you fill up a pigeonhole, it normally uses the pigeonhole right next to it, so the file still is not fragmented and all together in one place.  
Just having them scattered out all over the hard drive don't mean the files are fragmented, just placed where they can be read the fastest is all, while leaving room for more files to be added, without causing fragmentation of the individual files.

TTUL
Gary

---


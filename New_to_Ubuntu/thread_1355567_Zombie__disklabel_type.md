---
title: "Zombie:  disklabel type"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by gbear14275 on 2009-12-15
Hello,

I am unsure of the way to address dead topics correctly but this user had the same question I had and I haven't been able to find out much more than they were.

[http://ubuntuforums.org/showthread.php?t=338254](http://ubuntuforums.org/showthread.php?t=338254)

In summary:  Could someone please provide information about the other disklabel types and perhaps even a comparison of them?  I would love to know more but have only been able to find scattered and very limited information on them.

List:
msdos (well documented and not interested in further info)
amiga
bsd ([http://en.wikipedia.org/wiki/Disklabel]("http://en.wikipedia.org/wiki/Disklabel")?)
dvh
gpt ([http://en.wikipedia.org/wiki/GUID_Partition_Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table"))
mac
pc98
sun ([http://en.wikipedia.org/wiki/Slice_(disk)]("http://en.wikipedia.org/wiki/Slice_(disk)")?)
loop

Note:  This may be more advanced than this forum is used to but this is the location of the original topic so kept it here.

---

### Post by cariboo on 2009-12-15
DVH is the file system used SGI and it's Irix file system. See the man page [here]("http://techpubs.sgi.com/library/tpl/cgi-bin/getdoc.cgi?coll=0650&db=man&fname=/usr/share/catman/a_man/cat7/vh.z"). More info can be found [here]("http://techpubs.sgi.com/library/tpl/cgi-bin/getdoc.cgi?coll=0650&db=bks&fname=/SGI_Admin/XVM_AG/ch01.html").

PC98 is a filesystem for FreeBSD/PC98, more info [here]("http://www.freebsd.org/releases/6.2R/relnotes-pc98.html").

For more info on the amiga file system have a look [here]("http://en.wikipedia.org/wiki/Amiga_Fast_File_System").

Loop file system also at [Wikipedia]("http://en.wikipedia.org/wiki/Loop_device")

Mac/HFS file system at [Wikipedia]("http://en.wikipedia.org/wiki/HFS_Plus").

---


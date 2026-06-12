---
title: "It's backup time."
date: 2009-02-02
forum: New to Ubuntu
---

### Post by dESAI on 2009-02-02
Greetings all :)

Got my shiney new 8.10 installation all done and looking great. 1,000,000 thanks to everyone who made Ubuntu what it is today. Very impressive :)

Now I have everything I want installed and working perfectly, it's time to backup.

I want to do a full backup. So when things go pear shaped I can just do a full restore like nothing ever happened :)

Suggestions are welcome. External HD is available.

Thanks all! Stay cool.

---

### Post by taurus on 2009-02-02
Partimage is one option.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by dESAI on 2009-02-02
> **taurus said:**
> Partimage is one option.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Looks interesting :)

Any idea if I could restore the Image to a larger HD partition? 

Thanks :D

---

### Post by sydbat on 2009-02-02
I'm looking for something like this too (although for other reasons at the moment). For example, I am removing my XP partition (first on disk) and want to move / into it (currently second on disk). Would this break things?

Then I will expand /home...that's another story...

So, to ask the same question as dESAI, can you put the partimage image into a larger partition? And can it be physically moved to another partition without killing the system completely (I will probably have to reinstall grub).

Thanks.

---

### Post by taurus on 2009-02-02
I've never done it so I don't know.  You just have to look it up at from their site.

 [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

Another option is to use Clonezilla, [http://www.clonezilla.org/](http://www.clonezilla.org/).

---

### Post by sydbat on 2009-02-02
This might answer some of our questions...

From the partimage.org website:> The partition to restore must have the same size as the saved partition. If the partition is smaller than the original one, the operation will fail. If it is bigger, space can be lost. You can read the FAQ of this handbook, for more details about this. FAQ> Can I restore it to a smaller or bigger partition ?

You can't restore to a smaller partition (you will have an error), but it's possible to restore to a lager one. In this case, some space will be lost (I suppose the OS cannot use all the size). Partimage don't have a resize feature, but you can use other tools. I'd like to add this in the future too. It will allow to restore into a smaller or larger partition. Indeed, as Partimage is low level it uses data blocks. So resizing is possible, but that's a complex feature to implement. With some File Systems made to be easily resizable (as NTFS, ext2, ReiserFS), it may be easy, but with FAT, it's hard to do. For example, when resizing from 1,5 GB to 3 GB, you must change FAT16 into FAT32... You can use GNU Parted to do it. 

---

### Post by mdpalow on 2009-02-03
Check out QuickStart. I think it'll serve your purpose and more nicely. Link is in my signature.

mdpalow

---


---
title: "New HD and partitioning"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-09-03
Hi all, hope your all well.

Ok Ive just got myself a nice shiny new 1 TB internal sata HD.
Now Ive just repartitioned it up with Paragon Partition manager in
Vista and setup roughly, 5 x 200GB partitions (in NTFS format).

Well what a shock, Vista cant even see them. So I was wondering
if it was worth re-formatting them into Ext3 and be done with it?

I spend 90-95% of my time in Linux now, but I really want/need
to be able to access my data in both OS's.

(I currently use a 500 GB external drive in NTFS format which
has rapidly filled up).
I'd like to (not have to regularly de-frag) if it was in NTFS but I
can live with it. (Which is another reason for wanting to use
Ext3)

I had read about ext2/3 for Win, I read a few forum threads
where people were 50/50 for/against using it.

So what do yourselves use/do/have setup. (Esp if you dual/multi
boot?)


Thanks in advance for any help.

---

### Post by jimsheep on 2009-09-03
i didn't like the ext2/3 for win because i had to load the module every time i wanted to access an ext* partition.  my recommendation is to back up one of your "data-only" partitions and reformat it to vFAT.  that way you can read/write from both OSs without additional plugins/headaches/et cetera.

---

### Post by mbzn on 2009-09-03
> **jimsheep said:**
> i didn't like the ext2/3 for win because i had to load the module every time i wanted to access an ext* partition.  my recommendation is to back up one of your "data-only" partitions and reformat it to vFAT.  that way you can read/write from both OSs without additional plugins/headaches/et cetera.

What is the diffs between vFAT and NTFS? I would like to know as all my external are running NTFS, Performance- and maintenance- wise?

---

### Post by jimsheep on 2009-09-04
good question...can someone else answer it?  all i know is that vFAT is [http://en.wikipedia.org/wiki/File_Allocation_Table#Long_file_names]("http://en.wikipedia.org/wiki/File_Allocation_Table#Long_file_names") and NTFS is [http://en.wikipedia.org/wiki/NTFS]("http://en.wikipedia.org/wiki/NTFS")

---

### Post by aeiah on 2009-09-04
i wouldnt go with FAT nowadays. it cant handle files larger than 4GB, which is annoying if you deal with DVD.iso files or HD movies, etc.

im pretty sure NTFS will be reliable enough for you under linux. probably a lot more reliable than ext3 under vista.

---

### Post by mbzn on 2009-09-04
After reding that I only came up with another question... Is exFAT better than vFAT/NTFS?

---


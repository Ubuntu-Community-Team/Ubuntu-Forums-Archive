---
title: "unrar seems to be frozen"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Kejing on 2009-02-03
I am trying to use command line to extract a series of compress packages who extension name is r01, r02, ...r94, rar, 95 files in total. In windows, I just double click the last file with rar as extension name, then extract everything, so I run
```

unrar e file.rar

```

at the beginning, everything goes fine, I can see 
```

file.r01 decompressing
file.r02 decompressing
....

```

after a few minutes,  the decompressing speed went down, and then it seemed to be frozen.

All the files are on an NTFS compressed partition, I am not sure if the speed has something to do with the compressed non-linux partition. 

Meanwhile, I also found that, if I copy a big file such as 2G from ext3 partition to NTFS compressed partition, the speed also goes down after a few minutes and freezes.

---

### Post by jerome1232 on 2009-02-03
Well for one thing ntfs-3g can't write to compressed ntfs partitions (if you mean it's compressed on the filesystem level)
[http://www.ntfs-3g.org/support.html#questions](http://www.ntfs-3g.org/support.html#questions)
> Why can't I read or modify some files?
    NTFS supports built-in, transparent compression and encryption of files and directories on the file system level. Reading transparently compressed files are supported but writing of compressed and encrypted files is denied at the moment. Please note that compressed files, like .zip, .gz, .rar, etc, can be freely modified because they are compressed on the file, not on the file system level.

    Workaround: Uncompress or decrypt the files on Windows.

---

### Post by Kejing on 2009-02-03
> **jerome1232 said:**
> Well for one thing ntfs-3g can't write to compressed ntfs partitions (if you mean it's compressed on the filesystem level)
[http://www.ntfs-3g.org/support.html#questions](http://www.ntfs-3g.org/support.html#questions)
Thanks for your help first, but I found I could manipulate some files on the NTFS compressed partition, like copying some small file, like 400 MB from ext3 to NTFS compressed partition. It seems to be inconsistent to the answer you quoted.

---

### Post by szaka on 2009-02-04
> **jerome1232 said:**
> Well for one thing ntfs-3g can't write to compressed ntfs partitions (if you mean it's compressed on the filesystem level)
[http://www.ntfs-3g.org/support.html#questions](http://www.ntfs-3g.org/support.html#questions)
NTFS-3G can write to transparently compressed NTFS volumes. Just the files won't be compressed on the NTFS level. This is completely normal. Windows doesn't compress a lot of files either (needed to boot, make no effect, etc).

---


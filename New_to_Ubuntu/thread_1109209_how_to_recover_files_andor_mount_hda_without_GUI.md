---
title: "how to recover files and/or mount hda without GUI?"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by vhegos on 2009-03-28
Hello all,

Something quite serious has happened to my filesystem (or maybe my harddisk itself) and I am trying to recover a few files before attempting a reinstall of Ubuntu.  Typically to do this I would boot from the live cd, mount the harddisk, and backup files to another location.  This time however the main drive does not show up in the pretty "Places" menu.  The way I understand it, I can accomplish the same thing using mount.  I have been tried the following command:


```
mount /dev/hda1 /mnt/hda1
```

This is supposed to mount the filesystem on hda1 at the point /mnt/hda1 right?

I am getting the error 

```

[ 2297.972000] EXT3-fs error (device hda1): ext3_check_descriptors: Block bitmap for group 0 not in group (block 3952566938)!
[ 2297.972000] EXT3-fs: group descriptors corrupted!


```

This looks cryptic but bad to me.  Is there anything I can try?
  

If I cannot recover the files, it is not that big of a deal, but in general how can I know if my harddrive is toast?


Thanks a lot for any info !!

---

### Post by Eisenwinter on 2009-03-28
Try, as **root**:
```
fsck.ext3 -vfp /dev/hda1
```

---

### Post by vhegos on 2009-03-28
That worked like a charm.  Thanks a lot!  I will definitely add this command to my list of great tricks to know.

---


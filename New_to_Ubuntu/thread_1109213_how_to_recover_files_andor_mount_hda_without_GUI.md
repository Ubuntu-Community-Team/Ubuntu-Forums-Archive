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
/dev/hda1 already mounted or mnt/hda1/ busy
```

I have tried 

```
umount hda1
```

but I get the message the hda1 is not mounted.  I have never seen a directory 'busy' before.  I don't know what that means.

If I cannot recover the files, it is not that big of a deal, but in general how can I know if my harddrive is toast?


Thanks a lot for any info !!

---


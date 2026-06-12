---
title: "Recover ext4 partition that was &quot;shred&quot;ed"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by sundol on 2011-01-05
I did
$>shred -n 1 -v /dev/sda2 # /home partition (ext4)
It gave some error messages and continued. I quit it after several seconds by Ctrl+C.

Then,
$>shred -n 1 -v /dev/sda1 # / partition (ext4)
It made /dev/sda1 full and it give a message of "there are no space at root partition. erase some files..." and system get stuck.

Then, OS was reinstalled (/dev/sda1 as / and /dev/sda2 as /home, which was same to previous partition).

However, /dev/sda2 was not mounted and recognized as "unknown partition" by gparted.

/dev/sda2 have many data (100G out of 240G partition).

How to recover data of /dev/sda2 ?

---

### Post by presence1960 on 2011-01-05
> **sundol said:**
> I did
$>shred -n 1 -v /dev/sda2 # /home partition (ext4)
It gave some error messages and continued. I quit it after several seconds by Ctrl+C.

Then,
$>shred -n 1 -v /dev/sda1 # / partition (ext4)
It made /dev/sda1 full and it give a message of "there are no space at root partition. erase some files..." and system get stuck.

Then, OS was reinstalled (/dev/sda1 as / and /dev/sda2 as /home, which was same to previous partition).

However, /dev/sda2 was not mounted and recognized as "unknown partition" by gparted.

/dev/sda2 have many data (100G out of 240G partition).

How to recover data of /dev/sda2 ?

[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

I have to ask: If you needed the data why did you run the shred command? Here is the man page for shed:
```

NAME
       shred - overwrite a file to hide its contents, and optionally delete it

SYNOPSIS
       shred [OPTION]... FILE...

DESCRIPTION
       Overwrite  the specified FILE(s) repeatedly, in order to make it harder
       for even very expensive hardware probing to recover the data.

       Mandatory arguments to long options are  mandatory  for  short  options
       too.

       -f, --force
              change permissions to allow writing if necessary

       -n, --iterations=N
              overwrite N times instead of the default (3)

       --random-source=FILE
              get random bytes from FILE
 Manual page shred(1) line 1
```

I don't know what you were thinking. Good luck.

---


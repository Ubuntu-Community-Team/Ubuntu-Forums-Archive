---
title: "What does this command do?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by andr3w on 2009-01-30
Hi!
I was browsing, on how to show the exe in a wow cd;
And someone gave this command:

```
mount -t auto -o loop,unhide /dev/cdrom /media/cdrom 
```

The disk was for win/mac; (hybrid)-

I'm just not sure;
What does this command do?

It worked. But I had to restart to be able to open the drive again.
I'm just wondering..

---

### Post by hyper_ch on 2009-01-30
did you have a look at the man pages?

---

### Post by yeats on 2009-01-30
Go ahead and open a terminal and do

```
man mount
```

You'll just see an explanation of what mount does.

---

### Post by andr3w on 2009-01-30
> **hyper_ch said:**
> did you have a look at the man pages?

I wouldn't even know which one to look at. :(

---

### Post by hyper_ch on 2009-01-30
well, the manual pages are (normally) very extensive and they are called:

```

man COMMAND

```

as you wanted to know about the "mount" command you issue:

```

man mount

```

Or you could make it a text file on the Desktop:
```

man mount > ~/Desktop/mount.txt

```

---

### Post by andr3w on 2009-01-30
> **hyper_ch said:**
> well, the manual pages are (normally) very extensive and they are called:

```

man COMMAND

```

as you wanted to know about the "mount" command you issue:

```

man mount

```

Or you could make it a text file on the Desktop:
```

man mount > ~/Desktop/mount.txt

```



oh ok. :)

Well so far I have:
```

 -t vfstype
              The  argument following the -t is used to indicate the file sys&#8208;
              tem type. 

  If  no  -t  option  is  given, or if the auto type is specified,
              mount will try to guess the desired type.  Mount uses the  blkid
              or  volume_id  library for guessing the filesystem type; if that
              does not turn up anything that looks familiar, mount will try to
              read  the  file  /etc/filesystems,  or,  if that does not exist,
              /proc/filesystems.  All of the  filesystem  types  listed  there
              will  be tried, except for those that are labeled "nodev" (e.g.,
              devpts, proc and nfs).  If /etc/filesystems ends in a line  with
              a single * only, mount will read /proc/filesystems afterwards.


-o     Options are specified with a -o flag followed by a  comma  sepa&#8208;
              rated  string of options. 
```

Then there is no option for loop or unhide in the -o, but I'm looking.

---

### Post by hyper_ch on 2009-01-30
hmmm, at the bottom of the man pages there are often examples :)

but "loop" and "unhide" will be explained further down. Simplest thing would be to make it a text file (as shown above) and search for the words ;)

---

### Post by andr3w on 2009-01-30
k, well I got to the end of the manual and I'm not seeing anything.
Can someone help?

---

### Post by hyper_ch on 2009-01-30
well, loop is the device kind... I can't really explain that either... but
```

unhide
    Also show hidden and associated files. (If the ordinary files and the associated or hidden files have the same filenames, this may make the ordinary files inaccessible.)
```

---

### Post by andr3w on 2009-01-30
> **hyper_ch said:**
> well, loop is the device kind... I can't really explain that either... but
```

unhide
    Also show hidden and associated files. (If the ordinary files and the associated or hidden files have the same filenames, this may make the ordinary files inaccessible.)
```

I found the bit about loops after searching through the text file. (lol)

Concerning the hidden files- I wasn't able to see them when doing Ctrl H.
But after this command it showed them..

So, then I'll guess here;

The command did a guess on the type of Filesystem;
Then mounted it on a loop device (I'm not sure why?) (similar to how libdvdcss2 reacts to dvds?)

Then after all that it unhides the files.

---

### Post by hyper_ch on 2009-01-30
well, it did guess the filesystem and then, because it's a cd, it mounted it as loop device and made all files visible :) but yeah, basically you figured it out.

---

### Post by andr3w on 2009-01-30
> **hyper_ch said:**
> well, it did guess the filesystem and then, because it's a cd, it mounted it as loop device and made all files visible :) but yeah, basically you figured it out.

Hm. Ok. Thanks. :)

---

### Post by hyper_ch on 2009-01-30
sometimes the man pages aren't that easy to read but in most cases you get also tons of examples delivered ;) good luck.

---

### Post by andr3w on 2009-01-30
> **hyper_ch said:**
> sometimes the man pages aren't that easy to read but in most cases you get also tons of examples delivered ;) good luck.

Thank you. :)

---


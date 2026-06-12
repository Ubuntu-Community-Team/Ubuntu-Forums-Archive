---
title: "error while copying from command line"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2009-04-23
So I am trying to copy an entire drive to another drive which is blank. 

I mount both drives (vfat, FAT32) as follows in my /etc/fstab
```
/dev/sda1	/media/160gb.w95-os	vfat	iocharset=utf8,umask=000 0 0
```
I perform the following once the drives are mounted,
```
sudo cp -rfp /media/160gb.w95-os/* /media/82gb.w95-os/

```
So that SHOULD be recursive, force, and copy permissions (thus the sudo).

Now I get the following error
```
cp: reading `/media/160gb.w95-os/Copy of Drive   C  06 19 2008/ArtApart.20/AAUninst.exe': Input/output error

``` and it halts. Always at the same place. Now I tried doing directory at a time and realized there are numerous spaces in file names and special characters which linux obviously has trouble with. My question is, how can I force the copy without having to rename each file (multiple thousands).

---

### Post by unutbu on 2009-04-23
```
sudo rsync -a /media/160gb.w95-os/ /media/82gb.w95-os/
```

---

### Post by SuperSonic4 on 2009-04-23
> **DoubleMcLovin said:**
> 
I perform the following once the drives are mounted,
```
sudo cp -rfp /media/160gb.w95-os/* /media/82gb.w95-os/

```
So that SHOULD be recursive, force, and copy permissions (thus the sudo).


The * says to copy all files inside the folder, with copying you don't need this as you're using the -r flag which copies the folder and everything in it. If you change it to

```
sudo cp -rfp '/media/160gb.w95-os/' /media/82gb.w95-os/
``` you should have more luck. Remember that fat32 can only support up to 4gb per transfer

---

### Post by leandromartinez98 on 2009-04-23
> **unutbu said:**
> ```
sudo rsync -a /media/160gb.w95-os/ /media/82gb.w95-os/
```


sudo rsync -avtr /media/160gb.w95-os/ /media/82gb.w95-os/

will be better. Recursive and, if it stops for some error, you can 
try restart it with the same command, and it will only update the
new or modified files.

---

### Post by unutbu on 2009-04-23
From the man page for rsync:
```
        -a, --archive               archive mode; equals -**r**lp**t**goD

```
so the -a option already include the -tr flags.```


        -v, --verbose               increase verbosity
```

The -v flag just makes the command more verbose.

"rsync -a" and "rsync -avtr" can both be restarted and is smart about only updating new or modified files (unlike cp). Thanks for pointing out this last part, leandromartinez98. It is a very good reason to use rsync rather than cp.

---

### Post by DoubleMcLovin on 2009-04-23
Wow... that was epic haha. So I went ahead and ran the command ```
sudo rsync -a /media/160gb.w95-os/ /media/82gb.w95-os/
``` and I end up getting my terminal absolutely FLOODED with spam, I hit CTRL+C to break it, and heres some of the garbage that was flying across the terminal. ```
rsync: readlink "/media/160gb.w95-os/Copy of Drive   C  06 19 2008/DYADGames/Puzz-3DVictorian/ë4&#9567;æd&#9557;&#9560;ú.&#9496;"&#9552;" failed: Input/output error (5)
rsync: readlink "/media/160gb.w95-os/Copy of Drive   C  06 19 2008/DYADGames/Puzz-3DVictorian/]ác>*.&#9617;t=" failed: Input/output error (5)
rsync: readlink "/media/160gb.w95-os/Copy of Drive   C  06 19 2008/DYADGames/Puzz-3DVictorian/&#8319;e&#945;°«n.\#021.&#9569;\#033|" failed: Input/output error (5)
rsync: readlink "/media/160gb.w95-os/Copy of Drive   C  06 19 2008/DYADGames/Puzz-3DVictorian/\#020auu#ùæ&#9579;.qî" failed: Input/output error (5)

```

Like I said, there are a few thousand files with names like that, and those are actual files which for some bizarre reason exist and are apparently needed by a program to run.


I believe I've come up with a solution, I tried zipping a few of the items in that folder, and it creates an archive just fine which I can then copy. I think I am just going to zip the entire drive, then copy the zip and unzip through windows. (windows has a very big problem reading from this drive which is why I am moving things, it is most definitely on the edge of dying, so I would like to avoid any non-essential I/Os on there. But I am still very curious as to how one could overcome this obstacle without creating an archive =\

---

### Post by DoubleMcLovin on 2009-04-23
bump.. the zip method is incredibly horrific in this case as I have several hundred gigs >_> and making 4GB .zip packets is a horribly time consuming and mind numbing procedure.

---

### Post by andrew.46 on 2009-04-26
Hi SuperSonic4,

> **SuperSonic4 said:**
> 
```
sudo cp -rfp '/media/160gb.w95-os/' /media/82gb.w95-os/
```

It is a minor nitpick but would an easier commandline replace:

```
cp -rfp
```

with the following:

```
cp -a
```

I have always been a little wary of -f and I cannot see why it would be necessary on a blank drive?

Andrew

---


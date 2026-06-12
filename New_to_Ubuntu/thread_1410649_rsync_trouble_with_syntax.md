---
title: "rsync: trouble with syntax"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by wannabegeek on 2010-02-19
hi all,

I have decided to learn how to back up more efficiently and stumbled upon
rsync.

I want to backup my music directory, which consists of mostly single files and some directories that contain albums.

I thought it was pretty easy but it seems I'm doing something wrong.Here's what I tried:```
sudo rsync -r ~/Music/*.*  /media/LinuxBU/MusicBU 
```where LinuxBU/MusicBU is my music mack up directory on an external USB drive.
It did copy the files, but not the directories, and when I tried again, it didn't seem to skip
what was already there, and my machine froze up for the first time since installing Ubuntu...

thanks for your help,
wbg

---

### Post by falconindy on 2010-02-19
*.* is a DOS'ism. Specifying the folder alone is enough. I'd also recommend **not** doing this as root. If you're unable to write to your external drive any other way, you need to solve that problem first.

---

### Post by SecretCode on 2010-02-19
It's good to add the -v parameter so it reports more of what's going on.

Also I think your first syntax will not preserve attributes and timestamps, so on the second run, files don't match and have to be copied again. The -a parameter sorts this out. 

```
rsync -rva ~/Music/* /media/LinuxBU/MusicBU
```

---

### Post by wannabegeek on 2010-02-19
hey, thanks folks...

I saw the preserve time stamp option in the man but thought it was supposed to be default.

I tried the above code and go an error:
rsync: failed to set times on "/home/daniel/LinuxBU/.": Operation not permitted


also, I mount the USB drive on my home directory to avoid sudo...
any ideas? I 

wbg

---

### Post by wannabegeek on 2010-02-19
hi again,
from home dir I tried:
```
sudo rsync -rsv Music/Mozart LinuxBU
```

and it seems to have to copied the files with time stamps...
gonna try the whole thing again and see if the directories get in there.

wbg

---

### Post by alphacrucis2 on 2010-02-19
If you are more comfortable with GUI apps, there is a graphical front end available to rsync in the repositories called grsync. It doesn't provide all the available rsync features but may do what you want. An advantage of it is that it allows to create "sessions" which you can use again and again to perform the same backup task. The project seems to be in active development with two releases having come out since the version in the karmic repos.

---

### Post by lijcam on 2010-02-19
I use rsync to sync all media between two media centres.

```
rsync -au --compress --stats --human-readable --exclude=.Trash-1000 /source /destination
```[B]
-a, --archive[/B] This is equivalent to -rlptgoD. It is a quick way of saying you want recursion and want to preserve everything.

**-u, --update** This forces rsync to skip any files for which the destination file already exists and has a date later than the source file.[B]

-z, --compress [/B]With this option, rsync compresses any data from the source file(s) which it sends to the destination machine.  This option is useful on slow links.  The compression method used is the same method that gzip uses.
[B]
--stats[/B] This tells rsync to print a verbose set of statistics on the file transfer, allowing you to tell how effective the rsync algorithm is for your data.[B]

-h, --human-readable[/B] Print sizes in human readable format (e.g., 1K 234M 2G)


If you what to automated it with crontab so to make sure that rsync does not run if your hard drive is not plugged create a blank file in the root of your destination and add before your rsync statement.

```
if [ -f /destination/control.file ]
    then echo "Hard Drive connected"
    else echo "Hard Drive not connected" && exit
    fi
```What this does is make sure the file "control.file" exists. If it doesn't the script will quit before running rsync.

---

### Post by rnerwein on 2010-02-19
hi lijcam
this is a good explanaition how to do it.
but "fi" not done  :-)
ciao

---

### Post by lijcam on 2010-02-19
Hey thanks for that rnerwein have made the correction.

Also for got to add while you are playing with rsync make sure you add the dry run switch.

 **-n, --dry-run**               show what would have been transferred.

---

### Post by wannabegeek on 2010-02-20
wow,THANKS lijcam

kick *** reply...

There iseems to be a sublte difference between the two codes below:
```
$rsync -au ../source/  target 
 $rsync -au ../source /target
```

the second command creates a new directory in the target location, while the first
copies into the target like I would have expected.

Am I wrong ?

thanks again,
wbg

---

### Post by Girya on 2010-02-20
man rsync:  

> A trailing slash on the source changes this behavior to avoid  creating
       an  additional  directory level at the destination.  You can think of a
       trailing / on a source as meaning “copy the contents of this directory”
       as  opposed  to  “copy  the  directory  by name”, but in both cases the
       attributes of the containing directory are transferred to the  contain&#8208;
       ing  directory on the destination.  In other words, each of the follow&#8208;
       ing commands copies the files in the same way, including their  setting
       of the attributes of /dest/foo:

---


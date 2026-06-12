---
title: "How to restore files?"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by pkjm17 on 2010-11-25
I accidentally moved my mp3's to the trash and then deleted them. :(
Is there any way to get them back from the trash? Or restore them somehow on my computer?

---

### Post by ChuckyDuckster on 2010-11-25
Try using scalpel. I have had good luck with it in the past.

[http://www.howtoforge.com/recover-deleted-files-with-scalpel](http://www.howtoforge.com/recover-deleted-files-with-scalpel)

---

### Post by oldfred on 2010-11-26
Another tool is testdisk's photorec. Which recovers more than photos.

Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

Recovery does not recover names of files, this helps
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by meadhikari on 2010-11-26
testdisk's photorec just recovered the files but is there a way to make it organized when it extracts I got 1137 folder of unorganized files with random names.

---

### Post by oldfred on 2010-11-26
I started running this on each file but then changed to a bash file. . I manually changed every extension with a replace command and reran it with every extension I was interested in. You could automate the list of extensions and do it all, but I was mostly done before I realized that and hope not to have to do again. the recover folder is on a separate drive that I mounted into my /home.
```
#!/bin/baods
# move files

cd /home/fred/recover
mkdir ods
find /home/fred/recover/recup_dir.1 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.2 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.3 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.4 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.5 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.6 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.7 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.8 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.9 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.10 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.11 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.12 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
  
```

I then used some commands to recover names where possible.
Photo meta data rename
jhead -n%Y%m%d-%H%M%S *.jpg

See link in file for more discussion of flac.
```
#!/bin/bash
#http://ubuntuforums.org/showthread.php?t=625466
#takes a source folder and destination folder as arguments

find "${1%/}" -type f -a -name '*.flac' | while read filename ; do
    metaflac "$filename" --export-tags-to=/tmp/tmp.txt
    album=$(awk 'BEGIN {FS="="; IGNORECASE=1} /^ALBUM/{print $2}' /tmp/tmp.txt | sed 's/\//-/g')
    artist=$(awk 'BEGIN {FS="="; IGNORECASE=1} /^ARTIST/{print $2}' /tmp/tmp.txt | sed 's/\//-/g')
    title=$(awk 'BEGIN {FS="="; IGNORECASE=1} /^TITLE/{print $2}' /tmp/tmp.txt | sed 's/\//-/g')
    tracknumber=$(awk 'BEGIN {FS="="; IGNORECASE=1} /^TRACKNUMBER/{print $2}' /tmp/tmp.txt | sed 's/\//-/g')
    mkdir -p /mnt/foto/Music/"$album"
    mv "$filename" "${2%/}/${album}/$tracknumber - $artist - ${title}.flac"
done
```

---

### Post by philinux on 2010-11-26
I had the same a while back. Here was my solution.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1516744](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1516744)

---

### Post by jackdream on 2010-12-09
> **pkjm17 said:**
> I accidentally moved my mp3's to the trash and then deleted them. :(
Is there any way to get them back from the trash? Or restore them somehow on my computer?
 
I suppose you have to use some music recovery software. And stop putting more files to the disk where your deleted mp3's located. Here are some software for your option.
try [this one]("http://www.disk-utilities.com/photo-recovery/") if you are using Windows
or [this one]("http://www.disk-utilities.com/photo-recovery-for-mac/") if you are running Mac OS
 
**_Note_**: recovery software may won't recover all your deleted ones, but will recover most of them.

---


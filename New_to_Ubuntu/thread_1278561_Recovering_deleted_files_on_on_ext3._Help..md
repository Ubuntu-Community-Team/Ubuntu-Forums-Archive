---
title: "Recovering deleted files on on ext3. Help."
date: 2009-09-29
forum: New to Ubuntu
---

### Post by zayka on 2009-09-29
Hello, first time poster here. Windows guy, so be kind.
So I have 1Tb hard drive formatted in ext2 or ext3 (not 100% sure here), which I use in network media player. Accidentally I deleted quite a folder with quite a bit of music (about 10Gb probably). So I was wondering on how to get my files back. From what I've read I need Linux/Ubuntu live CD and some recovery software. TestDisk and PhotoRec get good reviews. 
1. Do I need to run recovery tools under Linux or Windows?
2. Any suggestions?
Thanks.

---

### Post by LewRockwell on 2009-09-29
[http://partedmagic.com/](http://partedmagic.com/)

Everything you need all on one disk...sweet!

.

---

### Post by zayka on 2009-09-29
Hm, interesting. So is this like live CD with Linux type thing? I see it has TestDisk and PhotoRec. Any pointers would be appreciated.

---

### Post by unutbu on 2009-09-29
This page has information on available tools and how to use them: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

To run photorec, you just type
```

sudo photorec
```
You'll need to specify the partition to recover, and you'll need a partition of equal or larger size in which to save the recovered files.

---

### Post by aysiu on 2009-09-29
> **zayka said:**
> Hm, interesting. So is this like live CD with Linux type thing? I see it has TestDisk and PhotoRec. Any pointers would be appreciated.
Photorec for sure:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

### Post by zayka on 2009-09-29
Nice, will give it a try.
I was running Ubuntu Cd in live session and it was terrible. Selection was extremely slow and unresponsive. Is that normal?

---

### Post by aysiu on 2009-09-29
> **zayka said:**
> Nice, will give it a try.
I was running Ubuntu Cd in live session and it was terrible. Selection was extremely slow and unresponsive. Is that normal?
It's normal if you have 256 MB of less of RAM.

---

### Post by zayka on 2009-09-30
Ok, so I got PhotoRec working. Well, sort of. The problem partition I am working with is 900+ Gb and of course I don't have hard drive of equal or greater size to save my files to as they suggest. So I went into options and told Photorec to recover only mp3s, jpgs and search only unallocated space. I figured it would require about 15 Gb at most. Even though hard drive I pointed to has 90 Gb of free space, PhotoRec says it can't write there, no space or something like that. 
It did recovered some files though. One major turn off for me is that it doesn't retrieve files with original namimg. It's kinda defeats the purpose for me in this case.

---

### Post by LewRockwell on 2009-09-30
> **zayka said:**
> Ok, so I got PhotoRec working. Well, sort of. The problem partition I am working with is 900+ Gb and of course I don't have hard drive of equal or greater size to save my files to as they suggest. So I went into options and told Photorec to recover only mp3s, jpgs and search only unallocated space. I figured it would require about 15 Gb at most. Even though hard drive I pointed to has 90 Gb of free space, PhotoRec says it can't write there, no space or something like that. 
It did recovered some files though. One major turn off for me is that it doesn't retrieve files with original namimg. It's kinda defeats the purpose for me in this case.

agreed

which continually reaffirms our sincere desire to see all valuable data adequately secured before a catastrophy/mistake/error

instead of after

there are additional and varying skill level tutorials and guides describing different experiences with data recovery, Photorec, and Testdisk

(amongst others)

.

---

### Post by zayka on 2009-09-30
> **LewRockwell said:**
> 
there are additional and varying skill level tutorials and guides describing different experiences with data recovery, Photorec, and Testdisk

So I guess PhotoRec doesn't work for me. Are there any other options that handle ext3 and not too labor intensive? What I am looking is at least keep original file naming, even that will be only 50% effective for my purposes. 
I am more and more inclined to just forget about it. I still can pull back about 90-95% data back from various sources. It will take few days, but probably less time than recover-rename-organize.

---


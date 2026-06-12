---
title: "desktop file transfer speed"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by never-never-land on 2011-09-07
hi everyone,
i'm dual booting win7 & ubuntu 11.04 (not WUBI), anyway i've started using ubuntu at about v. 10.04
and ever since than i'm getting slower file transfer rates than my win7.
'till now i thought it was my scr*w*d up hard disk. but yesterday i bought a new one:
"western digital 2tb caviar black, 7200 rpm"
did a new install of win7 & ubuntu 11.04, now, when i'm transferring a file from win partition to ubuntu i get between 30 - 40 MB/sec (usually around 40), and the same files/folders from ubuntu partition to win is around 20MB/sec or less.
I dunno why but for some reason i was under the impression that ubuntu should be much faster at this kind of things or at list equal to win...? or am totally off track here??:?:

btw: on my older hd the rates were as follow: win to ubu between 20-30 MB/sec.
ubu to win: 12 MB/sec

---

### Post by nmanoogian on 2011-09-07
Are you coping data to an external hard drive? Were you booted in Ubuntu or Win for the transfer?

---

### Post by HermanAB on 2011-09-08
Are you using a GUI to click drag drop files, or are you using the command line?

---

### Post by 3rdalbum on 2011-09-08
> **never-never-land said:**
> when i'm transferring a file from win partition to ubuntu i get between 30 - 40 MB/sec (usually around 40), and the same files/folders from ubuntu partition to win is around 20MB/sec or less.

Writing to an NTFS-formatted disk/partition on Linux is slower than writing to a native Linux filesystem. That's normal. Unavoidable.

NTFS write support is not "baked-in" to the Linux kernel, and instead runs as a userspace program. This creates a performance penalty. Also, the developers of the NTFS program have mainly written their driver for accuracy rather than speed, to the point where their NTFS error-correction tools are better than most of the ones you can get on Windows. Yes, you heard right: Linux can understand a Windows filesystem better than Windows can :-)

But yeah, the end result is that it takes a lot of CPU power to write to NTFS on Linux, and the actual slowdown depends on how good your CPU is.

---

### Post by never-never-land on 2011-09-08
thanks for all the replies,
well i don't use external hd, both os's are on my 2tb WD internal HD, & also i'm using drag&drop on nautilus.
3rdalbum:this is not a contradiction but i think its worth to mention: on my old HD i had 2 win (ntfs) partitions, and transferring files from partition C (where win was installed) to D was fast like transferring to linux, on the other hand transfrring files from D to C was slow like transferring from linux to win.
i think i'll examine the behavior with my new HD again tough i don't believe i'll be surprised....
if anyone would like me to post my results, please say  

BTW:Does anyone know a program that can be faster? or maybe explain how to divide my current ubuntu partition (I'd like to experiment this)?

---

### Post by nmanoogian on 2011-09-08
With a constant filesystem, I have noticed better speed when copying with Ubuntu. Copying from one external hard drive to another in Ubuntu has been much faster than copying when booted in Win7. I believe that the Ubuntu method of copying is more efficient; the file system might be holding you back. 

Good Luck! :)

---


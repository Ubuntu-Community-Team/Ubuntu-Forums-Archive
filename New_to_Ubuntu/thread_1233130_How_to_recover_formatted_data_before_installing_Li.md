---
title: "How to recover formatted data before installing Linux"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Shadi Ramadan on 2009-08-06
Hello!

I did the stupidest thing, installing Jaunty on my sisters old laptop.  When I installed I had it entirely format the drive (With windows XP) from a live CD.  What I didn't realize was that she had never backed up all her data (Photos... Music... Other Important Files).

I know its possible to recover data from a formatted drive (Arrays of softwares, data recovery centers, etc.) but is it possible recovering data from a formatted drive installed with ubuntu linux?

The laptop is a dell inspiron with only one drive...

It would be extremely helpful if someone could list possible solutions and how much I can recover (Tons of photos and over 5000 songs etc.).

I'm on the verge of panic so please help
- or my sister will bury me alive!!!

---

### Post by Cheesemill on 2009-08-06
I soon as you started installing Ubuntu on the formatted disk it will have started overwriting the files. You can try using Testdisk or Photorec to see what you can still recover.
 
Most importantly **STOP USING THE DISK IMMEDIATELY**, the more you use it the more old data you will use. You should use the live CD (and turn off it's swap space) to attempt recovery.

---

### Post by bear24rw on 2009-08-06
first get an external harddrive, plug it into your computer then i would load up the livecd and then install photorec

sudo apt-get install testdisk

and then run

sudo photorec

select the drive you installed ubuntu on and tell it to recover to the external

good luck

EDIT:

also if the external drive is not much larger than the laptop drive while it is recovering you can delete the non important stuff that it found to save space

you MUST use a live cd and you MUST recover to an external hard drive

---

### Post by Cheesemill on 2009-08-06
> **bear24rw said:**
> first get an external harddrive, plug it into your computer then i would load up the livecd and then install photorec
 
sudo apt-get install testdisk
 
and then run
 
sudo photorec
 
select the drive you installed ubuntu on and tell it to recover to the external
 
good luck
 
EDIT:
 
also if the external drive is not much larger than the laptop drive while it is recovering you can delete the non important stuff that it found to save space
 
you MUST use a live cd and you MUST recover to an external hard drive
 
Before this make sure you do:
```
 
sudo swapoff

```

---

### Post by Shadi Ramadan on 2009-08-06
Thanks everyone I will get right on it... WISH ME LUCK!

---

### Post by bear24rw on 2009-08-06
> **Cheesemill said:**
> Before this make sure you do:
```
 
sudo swapoff

```

why? the live cd doesnt use swap does it? the live cd shouldnt touch any hard drive by itself..

---

### Post by Cheesemill on 2009-08-06
Yup, if a Live CD finds any swap space on a disk it will automatically use it.

---

### Post by bear24rw on 2009-08-06
oh i didnt know that, nice to know thanks

---

### Post by Shadi Ramadan on 2009-08-06
Also, please note I love ubuntu and everyone associated with ubuntu!!!

You guys reply SO FAST.

---

### Post by mikechant on 2009-08-06
> the live cd doesnt use swap does it?

Yes, it does, if it can find a valid Linux swap partition. This sometimes causes problems when installing from the LiveCD.

If you have a small amount of RAM, the LiveCD might not be able to run usably or indeed at all without swap.
Personally I think the LiveCD should not use swap by default if you have (say) 2Gb or more of memory.

---

### Post by LewRockwell on 2009-08-06
> **mikechant said:**
> 

Personally I think the LiveCD should not use swap by default if you have (say) 2Gb or more of memory.

second that opinion...

the LiveCD should NOT engage swap by default!

.

---

### Post by bear24rw on 2009-08-06
i agree

someone should file a bug report

---

### Post by moodylei on 2009-10-18
[AppleXsoft Data Recovery]("http://www.applexsoft.com/data-recovery-professional-windows.html") , it can recover formatted hard disk and get back lost files from hard drive, recover data from formatted hard disk in FAT and NTFS format. 
 
tutorial: [http://www.applexsoft.com/howto/recover-formatted-hard-disk.html](http://www.applexsoft.com/howto/recover-formatted-hard-disk.html)

---


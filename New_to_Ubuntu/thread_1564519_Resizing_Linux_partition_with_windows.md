---
title: "Resizing Linux partition with windows ?"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by sabenfox on 2010-08-30
Hello All,
 
I have recently installed ubuntu linux 10.4 and i've found it to be a great OS. I've gotten Wow up and running and installed compiz fusion with almost no issues (occasionaly wow crashes). When i initially installed ubuntu i gave it 18 GB of hard drive space. 
 
Now i would like to increase the partition size, and i would like to do it as easy as possible. Windows 7 has a easy partitioning tool and i was wondering if i can use that to increase the size of my linux partition. 
 
I also know ( or think i know) that i should also increase my swap partition size in addition to the actual linux partion. I'm not sure how big to make a swap partition though...or if it is even possible to use windows to do this...
 
Your guys advice is greatly appreciated

---

### Post by kbless7 on 2010-08-30
I don't think you can since ext3 isn't supported in windows.

---

### Post by sabenfox on 2010-08-30
sigh =(
thanks for the response...
 
How can i do this under linux, i read i can use the live cd, but all the sda/1 sda/2 ext partion, ect... tend to confuse me....

---

### Post by M93 on 2010-08-30
> **sabenfox said:**
> Hello All,
 
I have recently installed ubuntu linux 10.4 and i've found it to be a great OS. I've gotten Wow up and running and installed compiz fusion with almost no issues (occasionaly wow crashes). When i initially installed ubuntu i gave it 18 GB of hard drive space. 
 
Now i would like to increase the partition size, and i would like to do it as easy as possible. Windows 7 has a easy partitioning tool and i was wondering if i can use that to increase the size of my linux partition. 
 
I also know ( or think i know) that i should also increase my swap partition size in addition to the actual linux partion. I'm not sure how big to make a swap partition though...or if it is even possible to use windows to do this...
 
Your guys advice is greatly appreciated

u can use gparted...download it from ubuntu software center

---

### Post by sabenfox on 2010-08-30
i have the cd i used to install ubuntu , is that program on that cd ?
 
even if i run the program, i'm not going to have a clue what to do afterwards..

---

### Post by migs73 on 2010-08-30
If you download it from the USC it'll be on your hard drive meaning you can't use to partition your hard drive!! Use a Live CD (either Gparted itself or Ubuntu) and use it to partition your hard drive. There are lots of good guides out there on how to do it.

---

### Post by sabenfox on 2010-08-30
ok thanks a lot, i will go on google and see if i can find a good guide to help me out. If
i get stuck i will repost here with screenshots and hopefully someone can give me more specific help.
 
one more question, i have windows 7 on my computer and i still need to be able to boot into it...if i resize with gparted or ubuntu will this mess up windows and keep me from booting into it...

---

### Post by Mark Phelps on 2010-08-30
> **sabenfox said:**
> ... one more question, i have windows 7 on my computer and i still need to be able to boot into it...if i resize with gparted or ubuntu will this mess up windows and keep me from booting into it...
Messing around with Win7 partitions with GParted or Ubuntu is asking for problems.  If you need to resize Win7 partitions, use the builtin Disk Management utility to do that.

Otherwise, you should be OK as long as you don't mess with the Win7 partitions.

---

### Post by eriktheblu on 2010-08-30
For clarity:
Use Windows to resize your Windows partition(s).

Once you have enough space, boot the live CD, move and expand your Linux partitions with Gparted.

Gparted is simple and intuitive. Avoid the NTFS partition (they're always green to me). Swap should be labeled, and the the rest will be ext3 or ext4 (default for Lucid).

---

### Post by Windows Nerd on 2010-08-30
A more simplified answer:

Use the disk management tool on Windows to shrink your W7 partition the desired amount you wish to gain on Ubuntu.

After this, insert a Ubuntu Live CD. Go to System>Administration>Gparted. From there resize your Linux Partition to fill the unallocated space. 

Note: If you have a separate /home partition an you want more space to hold you music ect, then resize the /home partition. If you do not have a separate one, just resize your root partition (mounted as /)

---

### Post by oldfred on 2010-08-30
A couple of links:


GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by M93 on 2010-08-30
no need to do much u just boot from the liveCD install gparted, switch 'swap' part off (right click it), do ur partitioning then click 'accept all operations'....according to the pc and the hdd it might take ALOT of time
i've just fininshed going through all this and everything is working gr8
win7, ubuntu..all 
good luck , it needs patience :)

---

### Post by sabenfox on 2010-08-31
ok thanks for all the support guys. I tried to do it last night and it didn't work out too well, but i will try again this morning. All the help is much appreciated :D

---


---
title: "Did I partition my HDD right?"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by gogo_t on 2011-04-28
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190253&stc=1&d=1304008126[/IMG]

:) 
> 3 partitions:
1) one for Linux (12 gb),
2) one for my files- music, movies etc (~ GB) and 
3) one with 2gb for "swap"

---

### Post by Dutch70 on 2011-04-28
Looks good! 

:guitar:

One small thing is you've got 2.79GB for swap, instead of 2GB. 
You can shrink swap and grow /home if you want. As you know by now, it's simple enough to do, 
but you have to do it from the live cd/usb.

Edit: The reason I mention that is because with 15GB of storage, that .79GB may be important to you.

---

### Post by grahammechanical on 2011-04-28
You have got the mount points correct also. This also is important.

For future reference, if you need to re-install you set the same mount points and you can mark / to be formatted but do not mark /home to be formatted and then you will not loose any data or settings.

Regards.

---

### Post by gogo_t on 2011-04-28
Yeah, 10x guys. I did that on my virtual pc first, because I wasn't sure how to do it. I've been running Ubuntu on third virtual pc since last month and I love ubuntu, but I weren't sure how to split the HDD untill now :) 

\It was easy to switch from windows to ubuntu, and really fun\ :)

One more question 
Now I have XP with disk C \100 gb\ and D \200gb\. I'm thinking of resizing C and making third partition B \30-50gb\ on which to install Ubuntu later. Should I do any changes to my C and D partitions when installing ubuntu dual boot? Or all I need to change is the "B" disk \spliting it like I did on my first post\ :)

> Edit: The reason I mention that is because with 15GB of storage, that .79GB may be important to you.
I red somwhere that it is possible to mount my windows parition, so I was thinking when I install it for real to mount my disk D, and to use the files on it on Ubuntoo too... it is possible, isn't it?

---

### Post by Dutch70 on 2011-04-28
First of all, C,D,B are windows names of partitions.

You will have to shrink C, I'm not sure of the safe way to do that with XP.

Then you'll have to do the same thing with "B" that you did with the one in the pic. Except, you will probably want all three partitions inside an extended partition.

---

### Post by gogo_t on 2011-04-28
> First of all, C,D,B are windows names of partitions.yeah, I know, but I thought that this way you'll understand my easyer as my english is not verry good, as you can see :D

> You will have to shrink C, I'm not sure of the safe way to do that with XP.I've done it in the past, so won't be a problem 

> Except, you will probably want all three partitions inside an extended partition.but If I couldn't \I'm sure I could but just for being clear\, setting it up as I did on the pic wouldn't be bad\problematic, would it?

---

### Post by Dutch70 on 2011-04-28
There is nothing wrong with your set up. The problem which I really don't think you need to worry about now, but just so you know.

You can only have 4 primary partitions. (that is partitions not inside the extended prtn.)

You can only have 1 extended partition, which will use up 1 one of your 4 primary's.

Inside your extended partition, you can have about 15 partitions, which are called logical partitions. 

So, if you have 2 primary's now (C & B) you can create 1 more & your extended, that will use all your primary spots. 

Primary's will be named sda1 thru sda4. That includes your extended prtn. Logical prtns will be named sda5 and up.

Edit: That is the reason that in your pic, there is sda1, sda2. Then it jumps to sda5, sda6.
sda3 & sda4 are reserved for 2 more primary's.

---

### Post by gogo_t on 2011-04-28
> **Dutch70 said:**
> There is nothing wrong with your set up. The problem which I really don't think you need to worry about now, but just so you know.

You can only have 4 primary partitions. (that is partitions not inside the extended prtn.)

You can only have 1 extended partition, which will use up 1 one of your 4 primary's.

Inside your extended partition, you can have about 15 partitions, which are called logical partitions. 

So, if you have 2 primary's now (C & B) you can create 1 more & your extended, that will use all your primary spots. 

Primary's will be named sda1 thru sda4. That includes your extended prtn. Logical prtns will be named sda5 and up.
10x, i appreciate it

---

### Post by Bucky Ball on 2011-04-28
> **Dutch70 said:**
> 
Inside your extended partition, you can have about 15 partitions, which are called logical partitions. 

> [FONT=Tahoma]**An "unlimited"                          number of logical drives may be created in an extended                          partition**, formatted and assigned drive letters.                          Unlimited is another misleading term used in conjunction                          with logical drives. The reality is you're limited by                          the number of available drive letters and the amount of                          hard drive space available for creating drives.[/FONT]From here:

[http://www.theeldergeek.com/hard_drives_01.htm](http://www.theeldergeek.com/hard_drives_01.htm)

> One of the four partitions on the disk can be the Extended Partition. It can be subdivided into logical volumes. Each logical volume is assigned a disk letter and can be formatted with a separate file system. **There is no limit on the number of logical volumes other than the fact that there are only 26 letters in the alphabet** and A, B, and C have been taken.
From here:

[http://www.yale.edu/pclt/BOOT/PARTITIO.HTM](http://www.yale.edu/pclt/BOOT/PARTITIO.HTM)

Don't know about the drive letters but the available hard disk space is a real limitation. My point: *Theoretically*, you can have an unlimited amount of logical drives (partitions) in an extended partition. ;)

---

### Post by Dutch70 on 2011-04-28
Bucky
We're actually talking about Linux partitions, he is just using windows drive letters cause it's easier for him to understand.

---

### Post by Bucky Ball on 2011-04-28
In that case, OP is only limited by capabilities of hard drive and space. ;)

---

### Post by Dutch70 on 2011-04-28
> **Bucky Ball said:**
> In that case, OP is only limited by capabilities of hard drive and space. ;)

I've read so much on that, some of it old I'm sure. The 15 rule came straight from my "help" files in my system.*(that could be old info too)* 
I used to think it was 64, then I found out that was with and IDE & SATA was supposed to be 15. Now I found out that later kernels may support more than that. So, I'm not really sure what to believe is the max, or if anyone actually knows for sure. 

Check this out if you feel up to it. It is from 2004, but there is some interesting info there. I just skimmed it myself.
[[COLOR="RoyalBlue"]http://www.justlinux.com/forum/showthread.php?t=152404[/COLOR]]("http://www.justlinux.com/forum/showthread.php?t=152404")

Either way, I have no doubt that he can create enough...lol.

---

### Post by gogo_t on 2011-04-28
Yeah don't worry, I wont need so much partitions

---

### Post by Dutch70 on 2011-04-28
> **gogo_t said:**
> Yeah don't worry, I wont need so much partitions

Yeah, but what if you want to install 60+ operating systems? :P

j/k, I do have 10 though. Can't keep up with them, but they aren't using needed space either.

---

### Post by Bucky Ball on 2011-04-28
> **Dutch70 said:**
> The 15 rule came straight from my "help" files in my system.*(that could be old info too) ... *

Or maybe the software calculates that number (15) from the capabilities it figures out from your hardware ... hmmm. 

> **Dutch70 said:**
> I have no doubt that he can create enough...lol.

Me neither! lol

---


---
title: "partition troubles"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by tuahaa on 2009-10-23
I ran Gparted from a live CD so I can make my Ubuntu 9.10 partition bigger. However, it won't allow me to move or resize a partition to the left =(
 
Any ideas?
 
EDIT: I just made a new partition that contains nothing in it, and you can move/resize it to the left. How come I can't resize my Ubuntu 9.10 partition to be bigger? It allows me to make it smaller, but I cant resize it to be bigger

---

### Post by louieb on 2009-10-23
How about posting a screen shot - but 1st a wild guess. is it a logical partition inside an extended partition?

[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by tuahaa on 2009-10-24
Here's a screenshot. Sorry, I don't know what you are talking about, which is why I'm a noob :(

P.S. I am using the Linux Mint 7 Live CD, which includes Gparted 0.4.3

---

### Post by oboedad55 on 2009-10-24
The post above you had it right, extended partition with a logical partition inside it. I believe you can resize the extended partition then resize the logical inside it.

---

### Post by mapes12 on 2009-10-24
> **tuahaa said:**
> Here's a screenshot. Sorry, I don't know what you are talking about, which is why I'm a noob :(

P.S. I am using the Linux Mint 7 Live CD, which includes Gparted 0.4.3You have to resize sda2 first, then resize sda6

---

### Post by tuahaa on 2009-10-24
Ok I'm going to try that... Still on the live CD :)

---

### Post by tuahaa on 2009-10-24
I can't resize sda2. There's no option. Thanks for the fast replies

---

### Post by tuahaa on 2009-10-24
I found out that Sda2 is 'Busy (At least one logical partition is mounted)' according to right clicking sda2>Information.

I don't get it- its not mounted. BTW, if this helps, I installed 9.10 as a dual boot with Linux Mint already on my laptop, and then got rid of mint by deleting it. My current 9.10 partition is an extended partition, if that helps.

---

### Post by louieb on 2009-10-24
Click on the swap partition and select swap off. Guess the live CD is using swap - thats why your extended partition is locked.

or another idea - I alway make a storage partition for my data. You could just create another partition in the unallocated space and use it to store your data too.

---

### Post by tuahaa on 2009-10-24
thanks. will try that. I will leave some unallocated space for storage too.

Thanks again!

EDIT: It works. Thanks heaps!

---


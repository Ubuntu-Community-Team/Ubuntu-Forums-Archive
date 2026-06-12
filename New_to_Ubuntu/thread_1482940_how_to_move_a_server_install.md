---
title: "how to move a server install"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by Franz01 on 2010-05-14
I have an ubuntu server running and I'd like to move it to another machine.

The first idea was to create a bootable image when working live. Following a forum post I investigated about remastersys package but it doesn't work in a server environment. And probably I should umount the devices...

Any suggestion is appreciated. Thank you

---

### Post by Franz01 on 2010-05-14
> **Franz01 said:**
> I have an ubuntu server running and I'd like to move it to another machine.  

in the meantime I have found Clonezilla but suggestions are still appreciated...

---

### Post by jpl888 on 2010-05-14
I'm not going to go too in depth here just give you ideas.

If you have physical access to the machine(s) then booting from a live CD with the hard drive from both machines in you can image from one drive to the other using dd, for instance```
dd if=/dev/sda of=/dev/sdb
```

Will copy the whole of the first drive in your machine to the second (please be careful which is which or you will wipe out the original and it won't work the way you want if the drives differ in size). However I normally resize the filesystems and partitions to the minimum, create partitions on the new drive, dd each partition separately and then resize to take advantage of bigger hard drive in new machine, e.g.

```
e2fsck -f -C 0 /dev/sda1
resize2fs -M -p /dev/sda1
fdisk /dev/sda
```

delete and recreate the partition to a size approximately 1GB larger than the current size of the filesystem (after shrinking) 

Create partition on new drive using fdisk then,

```
dd if=/dev/sda1 of=/dev/sdb1
e2fsck -f -C 0 /dev/sdb1
resize2fs -p /dev/sdb1
```

and repeat for other partitions, except swap (which you can just create).

Moving a machine remotely on the other hand is another kettle of fish. The best way I have come across so far is to have the "sytem" installed within an LXC container which can then be rsynced from IP to IP ad infinitum if necessary.

Oh and please please please be careful running the above commands if you are unsure at any stage post before hitting enter or suffer the consequences.

---

### Post by Franz01 on 2010-05-14
> **jpl888 said:**
> 
If you have physical access to the machine(s) then booting from a live CD with the hard drive from both machines in you can image from one drive to the other using dd, 


Ok, you mean I could clone the partitions using dd.. 

it means I could access the ubuntu server, 
connect a new USB device  to it (the usb device is much bigger than actual HD, so it does't matter the resize),  partition it as explaned below and then run dd... 

is it right?

> **jpl888 said:**
> 
 it won't work the way you want if the drives differ in size.

...

delete and recreate the partition to a size approximately 1GB larger than the current size of the filesystem (after shrinking) 

Create partition on new drive using fdisk then,


Here I am not 100% sure to understand.
Does it mean I must create 3 partitions in the USB drive if I have 3 partitions in linux? 
And the first USB partition must be of exactly the same size of the first linux partition, the same for partition #2 and #3?

Thank you for your suggestion.

---

### Post by jpl888 on 2010-05-14
Yes create 3 partitions if the original had 3. 

The partitions must be the same size or bigger.

Then resize2fs once you have dd'ed to take advantage of the extra space, are we clear?

---

### Post by HermanAB on 2010-05-14
Actually the best way to move a server is to make it a virtual server. Then you can move it to anything.

---

### Post by jpl888 on 2010-05-14
Yes well I was alluding to something like that when I mentioned LXC containers.

Unfortunately if you are using full virtualisation and especially if you don't have hardware virtualisation extensions in your CPU, performance will suffer.

That's why I prefer LXC, full performance and easy to move, best of both.

---

### Post by karatedog on 2010-05-14
I recently upgraded from 9.10 to 10.04 and while the process was not entirely FUBAR, it was just FU.
I'm thinking of installing Ubuntu/Kubuntu from scratch into a new USB drive (leaving the somewhat working version intact), and try to create my working environment there (apps, 10 gigz of mail, etc.), and when finished, move the entire partition to my notebook's HDD.
Will the above mentioned partition copy with 'dd' work this way?

---

### Post by jpl888 on 2010-05-15
Yes but you will be copying from sdb or sdc probably back to sda.

Gparted can copy partitions that might be a more user-friendly way of doing it (although I seem to get errors the odd time with that, especially if resizing prior to copy).

Keep an eye out for issues with fstab and grub because you are changing drive letter.

---


---
title: "Can't install ubuntu 6.04 with XP"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Norman Thom on 2009-05-02
Help!
I am getting extremely frustrated trying to Install Ubuntu 9.04 with my existing Windows XP.  I've been attempting to do this for about 4 days.

I have XP loaded on to an 80GB HD
Using Gparted I created a 2GB Swap partition and a 20GB ext3 partition.  I then tried the install function on the Live CD.  When the partitioner ran it first showed my 160GB HD saying there was no operating system on this computer (my backup disc).The other options are: 
where do you want to put Ubuntu 904?

(RB) Install them side by side, choosing between them each start up
(RB) use entire disc
(HD is specified here)
(RB) specify partitions manually (advanced)

then a blue bar indicating my 160GB HD with a 2.5GB ubuntu partition in it.

NB (RB) = radio button

The only way to have the top blue line indicate my 80GB (OS drive)
is to select use entire disc - not a good option I'd guess

When I selected "install side by side" it overwrote my XP and I needed to reinstall.  Needless to say I am nervous about jumping into this unaided.

Can anyone help me.

Thanks in advance
Norm

---

### Post by nandemonai on 2009-05-02
Just setup the partitions manually so you know exactly what you're putting where.

---

### Post by Norman Thom on 2009-05-02
Nandemonai:

Thanks for your input.
I've tried that, highlighted the appropriate ext3 partition and clicked on "forward"

It then tells me that no root file has been defined and sends me back

---

### Post by nandemonai on 2009-05-02
> **Norman Thom said:**
> Nandemonai:

Thanks for your input.
I've tried that, highlighted the appropriate ext3 partition and clicked on "forward"

It then tells me that no root file has been defined and sends me back

You have to set the mount point to /

At the least you need 2 partitions.

1. / (ext3) 
2. swap (swap) 
3. /home *OPTIONAL* (ext3 - this is for having user files on a separate partition)

---

### Post by Norman Thom on 2009-05-02
Nano-

I think I may have got it.

I changed the mount point of my ext file to "/"
changed the file type to ext4 and clicked on "forward"

it then took me to the next screen  "Who are you?"

Thanks for your help 

Frustrated

---


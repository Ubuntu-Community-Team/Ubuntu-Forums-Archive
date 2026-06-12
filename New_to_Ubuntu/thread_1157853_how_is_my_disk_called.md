---
title: "how is my disk called?"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Franz01 on 2009-05-13
I am trying to copy my full hard disk content into a USB external drive (bit to bit copy).

This is what I did:
I booted the PC with a ubuntu CD. 
I connected an ext drive.
Now I am trying to use the dd command.

**First problem: how is my C: hard disk called? **
I see that my C: Hard disk is /media/SW_Preload in ubuntu. 
it should be  where it is mounted while in /dev I find the actual device.
Now in /dev I see: 
ubuntu@ubuntu:/dev$ ls s*
scd0  sda1  sda3  sdb1       sequencer2  sg1  snapshot  sr0     stdin
sda   sda2  sdb   sequencer  sg0         sg2  sndstat   stderr  stdout

is **/dev/sda1** my c: disk? where do I see the link between the actual device and the mounted point?

**Second problem: the dd syntax**

I am trying with:

ubuntu@ubuntu:/media$ dd if=/dev/sda1 of="/media/My Passport/file"
dd: opening `/dev/sda1': Permission denied

can you suggest something different?

Thank you very much

---

### Post by skymera on 2009-05-13
```
 sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows 
```

Then try DD again with /mediawindows instead of /dev/sda1

---

### Post by Peter09 on 2009-05-13
the command

```
df -h
```

should list your mounted drives

while

```
fdisk -l
```

should show you your partitions

---


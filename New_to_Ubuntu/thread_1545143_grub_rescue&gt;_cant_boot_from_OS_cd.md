---
title: "grub rescue&gt; cant boot from OS cd"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by britstanger on 2010-08-03
I am using an acer aspire 1410 netbook which will not boot from a usb as far as i can figure out. 
I got ubuntu 10.04 nebook remix onto it using a portable cd drive. I set it up to dual boot.
the grub menu used to have:

ubuntu
windows 7 
windows vista loader

why vista is there I don't know as it originally just had windows 7. I accidentally selected the vista option now for some reason whenever I turn on the computer all I get is:

error: no such partition.
grub rescue>

when I type ls I get the list of partitions
(hd0) (hd0,6) (hd0,5) (hd0,3) (hd0,2) (hd0,1)

But I have no idea what to do to get it working again tried some commands from other threads e.g. help but all they seem to result in is

unknown command ' help'

I have tried booting from the CD I used to install ubuntu originally using my portable cd drive but it just doesn't work.

I have tried to follow the instructions I found on Ubuntu website:
1. ls

2. set prefix=(hdX,Y)/boot/grub

3*. set root=(hdX,Y)

4. set

5. ls /boot

6. insmod /boot/grub/linux.mod

7*. linux /vmlinuz root=/dev/sdXY ro

8. initrd /initrd.img

9. boot 

This works up to command 6: insmod /boot/grub/linux.mod when I get the message:
"error: file not found".

I have tried looking for it in the linux partition, I can find the vmlinuz and initrd.img files but I cannot find the linux module. from step 7 onwards I then get error messages "unknown command".

 
Please help!

---

### Post by Keen101 on 2010-08-03
Well, i'm a bit confused by your description. Maybe you can clarify it a bit.

does that menu come up every time?

Ubuntu
Win7
vista

...If it does, then do the other two options work? If they do, then don't try booting "vista" which doesn't exist...

OR are you saying after you tried booting "vista", it screwed up grub completely, and now you cant boot anything at all?

---

### Post by britstanger on 2010-08-04
> **Keen101 said:**
> 
OR are you saying after you tried booting "vista", it screwed up grub completely, and now you cant boot anything at all?

Yes i tried booting vista from the os selection menu now all I get every time I switch on the computer is.

error: no such partition.
grub rescue>

and I cant seem to boot from anything external.

---


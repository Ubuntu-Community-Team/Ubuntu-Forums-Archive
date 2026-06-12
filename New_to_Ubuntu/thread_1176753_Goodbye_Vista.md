---
title: "Goodbye Vista"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-06-02
Hi

I installed Ubuntu as a duel boot with vista by dividing the hard drive in to two equal parts.
I then made a mistake and now vista will not boot but as ubuntu is doing everything I want it to I've decided to dump vista altogether.
How do I do this so that ubuntu has all the hard drive to itself?

Thanks

---

### Post by binbash on 2009-06-02
Download and burn Gparted Live CD.Then boot with it, delete Vista partition and resize Ubuntu Partition.

---

### Post by Tibuda on 2009-06-02
Or use your Ubuntu live CD to do it. Remember to backup your important files in BOTH partitions.

---

### Post by nandemonai on 2009-06-02
First, make sure you have a good backup of your user files. Partitioning isn't 100% safe, say if there was a power outage or some such.

Secondly, boot from the live CD and open up GParted ( System -> Administration -> Partition Editor ).

Thirdly, delete the Vista partition and resize your Ubuntu partition(s).

Lastly, once partitioning is done, reboot into Ubuntu and edit your /boot/grub/menu.lst file:

```
sudo nano /boot/grub/menu.lst
```

Remove the entry down the bottom for Windows. It'll look something like this.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Microsoft Windows RC 7
rootnoverify	(hd0,3)
savedefault
makeactive
chainloader	+1
```

Hope it all works out for you with no dramas.

---

### Post by Mortus Pryde on 2009-06-02
Potentially a stupid question BUT! Does this work with XP and really any other OS? Also would I need to manually remove XP or said other OSs option from the Grub menu or will Grub detect that its gone and do that for me?

If the former perhaps some easy instructions for Anybloodyid, I already figured out how to edit the grub menu when my XP dual-boot snafu'ed.

As a point of curiosity Anybloodyid, what exactly happened/happens when you try to boot to Vista? Also do you use multiple hard drives? I know its off topic but as a beginner myself I like to pry a little into peoples problems that seem like they are similar to those I had.

---

### Post by Mortus Pryde on 2009-06-02
> **nandemonai said:**
> Lastly, once partitioning is done, reboot into Ubuntu and edit your /boot/grub/menu.lst file:

```
sudo nano /boot/grub/menu.lst
```

Remove the entry down the bottom for Windows. It'll look something like this.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Microsoft Windows RC 7
rootnoverify	(hd0,3)
savedefault
makeactive
chainloader	+1
```

Hope it all works out for you with no dramas.

LOL Beat me to asking the question with the instructions. :)

---

### Post by Anybloodyid on 2009-06-03
Ok I followed what you said and I now have this how do I give the unallocated space to Ubuntu?

[IMG]http://www.poem-n-verse.co.uk/Screenshot.png[/IMG]

---

### Post by lisati on 2009-06-03
> **Anybloodyid said:**
> Ok I followed what you said and I now have this how do I give the unallocated space to Ubuntu?

What I would do is click on the Ubuntu partition, then "Resize/Move", then set it so that it had 0 free space both before and after, then "go for it" with "Apply"

---

### Post by Anybloodyid on 2009-06-03
Hi Lisati,

Thanks for the reply, I tried what you suggested but the Move/Resize is ghosted?
Do i need to do this from the live DVD?

---

### Post by cjv8888 on 2009-06-03
> **Anybloodyid said:**
> Hi Lisati,

Thanks for the reply, I tried what you suggested but the Move/Resize is ghosted?
Do i need to do this from the live DVD?

You need to first resize the extended partition sda2 before trying to resize the sda5 partition to fill it, and you do need to do it from the live CD so that all the partitions are unmounted.

---

### Post by mike555 on 2009-06-03
Why not just format the first partition ext3 and use it for backup or storage ....

---

### Post by Anybloodyid on 2009-06-03
Thanks for all the help but I decided to just reinstall the complete thing, nothing lost by doing this as I had only just started with Ubuntu.

---


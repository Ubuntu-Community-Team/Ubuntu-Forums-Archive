---
title: "Not using drive"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by zaivala on 2009-11-09
I just upgraded my Eee PC 901 from ASUS/Xandros to Karmic Koala Netbook Remix.  Everything works fine, except...

The machine has a 20 GB SSD (solid state drive), formatted into partitions of 4 Gb and 16 Gb.  KKUNM loaded to the 4 Gb partition -- and did not format or otherwise use the 16 Gb partition, so my netbook is currently blind to this.

I've looked around everything I know how to look around, and can't find how to format (and use) this 16 Gb.

Any ideas?

---

### Post by Tman5293 on 2009-11-09
This is a very easy answer. Just go to Software Center and search gparted. Install that and use it to partition your drive to whatever file system you want.

---

### Post by zaivala on 2009-11-10
Thanks!  Haven't used GPartEd for a couple years, but it installed easily.  Wonder why they didn't include it in the distro?

---

### Post by zaivala on 2009-11-10
OK, GPartEd shows it formatted and in use, with 5.81 Gb being used out of 15.01,,,  but none of the other stuff related to drives shows /sdb1 at all...  guess I just need to look more... most of these things ask me to use /sda1 or the SD card (8 GB).  Ah, learning curve.  I'm going to have to start studying and stop being such a n00b.

---

### Post by zaivala on 2009-11-10
Not sure if this is solved... the drive is in use, but I don't seem to have access to it... when I download a file or save a picture, I only get asked whether I want to save it on the 4 Gb partition or the 8 Gb SD card, never the 15.1 Gb partition...

---

### Post by zaivala on 2009-11-13
> **zaivala said:**
> not sure if this is solved... The drive is in use, but i don't seem to have access to it... When i download a file or save a picture, i only get asked whether i want to save it on the 4 gb partition or the 8 gb sd card, never the 15.1 gb partition...


bump???

---

### Post by zaivala on 2009-11-25
OK, I'm officially stoopid.  The drive is there, it is formatted, it has files on it.  I still have to type my password to be allowed to view/work with files on it, but that's better than not being there.  Still trying to get help on the passwording thing (see other thread).

Thanks for all your help, I figure this one's closed.

---


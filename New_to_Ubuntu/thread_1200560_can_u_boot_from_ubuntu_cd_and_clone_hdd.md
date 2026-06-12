---
title: "can u boot from ubuntu cd and clone hdd?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by stinger30au on 2009-06-30
i just had an idea

i have finished setting up an 80 gig ide hdd with a dual boot setup running xp pro and 8.04


can i set the hdds up with a master/slave setup and mirror all data from one hdd to the next

the original hdd is 80 gig the new ide hdd is 160 gig?

once done i assume i could resise the partions with gparted as well.

i thought the dd command to copy the data but how?

thanks

---

### Post by louieb on 2009-06-30
dd might work. What I have done in the past is use Gparted (on a live CD) to copy and paste partitions from one drive to the other resizing the partitions as I copy.  

When done copying - change the MBR of the new drive to load GRUB from the new drive.

---

### Post by Paqman on 2009-06-30
> **stinger30au said:**
> 
i thought the dd command to copy the data but how?


If you have a lot of free space dd will be slooooow, because it'll copy all the free space as well.

If you just want to do a one-off copy, then you can just create some partitions and copy-and-paste like louieb says. If you want to update that copy regularly you could set up an rsync job to run through anacron/crontab.

If what you're after is resistance to hard drive faults then you might want to look into RAID1, which is a system of automatically mirroring all data between two drives.

---

### Post by stinger30au on 2009-07-01
its cool i dont need raid. just looking for a cheap alternative to ghost

need a way to copy clients data from smaller hard drives to newer bigger hard drives


i had no idea i could copy/paste with gparted but thanks for the tip i will go and have a look at that

is there a tutorial at all to show how to change the MB to boot off the new hdd


the smaller 80 gig hdd once it is back up to the 160 gig the 80gig hdd is getting removed from the pc all together so is there any need to modify the mbr as suggested by loiueb?

---


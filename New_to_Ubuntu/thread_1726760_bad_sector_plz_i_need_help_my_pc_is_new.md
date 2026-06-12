---
title: "bad sector plz i need help my pc is new"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by magedsoft on 2011-04-11
hay : 

i have problem my hard disk when i open disk utility give me that 
green mark and disk has a few bad sector .
what i have to do to ????????


help me

---

### Post by TeoBigusGeekus on 2011-04-11
Boot up with a live cd/usb and fsck your partitions
```
sudo fsck /dev/sda1
```
Replace sda1 with whatever applicable.

---

### Post by magedsoft on 2011-04-11
thank you too much i will do it and come again .

---

### Post by jerome1232 on 2011-04-11
How many? It's normal for new disk to have bad sectors.

If it has a green check mark then it should be within acceptable limits.

If the count is going up quickly then you may need to contact the manufacture of your drive and make good on it's warranty if it has one.

---

### Post by pricetech on 2011-04-11
> **jerome1232 said:**
> It's normal for new disk to have bad sectors.

Weellll, yes, but your OS should never find them because the manufacturer should have blocked them.

OP:  Use the manufacturer's diagnostics to test the drive.  You'll most likely have to do that to get it replaced under warranty anyway.

---

### Post by Mark Phelps on 2011-04-11
Personnally, I wouldn't trust Disk Utility to flag bad sectors.

Much better approach is what others have suggested -- get disk test utility from the drive manufacturer and run that.

And, BTW, with new disks, you should NOT be seeing any bad sectors. They should have already been flagged and removed.

---

### Post by jerome1232 on 2011-04-11
I guess you guys are right, I had assumed smart would just ask the drive what it's bad sector count was and the drive would give it. 

I guess it only reports re-mapped sectors. I just looked at mine (1 year old) and it has zero so I would be concerned about your disk as well.

---

### Post by magedsoft on 2011-04-12
thank all of you for your concern , i use hdd regenerator , i found zero bad sector , why disk utility say there is a few bad sector

---

### Post by oklokl on 2011-04-12
cd booting
sudo -i
fisk -l
fsck.ext4 -a /dev/sda1
or
fsck.ext4 -c /dev/sda1

HDD Regenerator 
iso booting
restore

---

### Post by rez182 on 2011-04-12
i had a similar problem.

if you think something is not right with your HDD and you have nothing important or can make a backup of ur data, i suggest make your HDD somewhat as good as new by completely erasing everything including partitions with Active Killdisk from killdisk.com 

worked for me...

---


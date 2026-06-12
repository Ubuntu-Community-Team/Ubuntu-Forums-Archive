---
title: "gparted doesn't work"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Cozze on 2010-12-30
I want to resize my root partition as it has become to small, so I installed Gparted. I can get the program running but the option to resize the partition isn't highlighted. I also tried to boot with the gparted iso file burned on a cd but nothing happens (even though cd rom is indicated as 1st choice in the boot menu). Anyone an idea?

---

### Post by IWantFroyo on 2010-12-30
First you have to shrink a different partition, THEN you resize your root partition.

---

### Post by howefield on 2010-12-30
You won't be able to resize a partition that is in use, as seems to to be the case here.

GParted is on the Ubuntu live CD, use that if you have one.

Also before messing around with your partitions, have any valuable data safely backed up elsewhere. :)

---

### Post by Cozze on 2010-12-31
If I understand well I must boot with the ubuntu live cd and follow the installation procedure until I get to the partition part and adapt the partition size there. Won't I be reinstalling then?

---

### Post by wilee-nilee on 2010-12-31
> **Cozze said:**
> If I understand well I must boot with the ubuntu live cd and follow the installation procedure until I get to the partition part and adapt the partition size there. Won't I be reinstalling then?

No. First have you installed Ubuntu inside a live windows environment?

---

### Post by mcduck on 2010-12-31
> **Cozze said:**
> If I understand well I must boot with the ubuntu live cd and follow the installation procedure until I get to the partition part and adapt the partition size there. Won't I be reinstalling then?

No, boot to the live-CD's desktop. You don't need to (and shouldn't ) run the installer.

---

### Post by Cozze on 2011-01-06
I booted with Gparted, but still it is not possible to schrink /home and thus to increase the / partition.

---

### Post by mcduck on 2011-01-06
Without seeing your actual partition layout I can't really help much with that, apart from reminding that you can't edit a partition that is in use at the moment. So make sure those partitions aren't mounted...

---

### Post by srs5694 on 2011-01-06
There's a good chance that swap space is in use and that's causing the problem. There's an option to disable swap space from within GParted, so you could try that. If you still can't figure it out, take a screen shot of the main GParted window and post it here; somebody will recognize whatever icon denotes a problem and be able to advise you further. Also post a clear description of what you're attempting and where it's going wrong (e.g., "I click the Foo icon and select Resize Foo, but it responds 'go away you English pig-dog!'").

---

### Post by hansolo4949 on 2011-01-06
In a nutshell, what you need to do is boot from an Ubuntu livecd, open up gparted from the livecd, disable swap, shrink one of your other partitions, then expand that partition, and remember to unmount the hdd at the time of resizing. Most importantly, don't forget to back up your critical files!


hansolo4949):P

---


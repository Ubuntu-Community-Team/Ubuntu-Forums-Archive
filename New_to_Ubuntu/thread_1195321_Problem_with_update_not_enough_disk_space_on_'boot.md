---
title: "Problem with update: not enough disk space on '/boot'"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by dromichaetes on 2009-06-23
Today when I tried to update my system [Ubuntu Jaunty 9.04 Desktop] I received this message:
```
Not enough free disk space

The upgrade needs a total of 15.7M free space on disk '/boot'. Please free at least an additional 428k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
```When I run 'sudo apt-get clean' in the terminal nothing really happens. I keep getting the above message. What should I do?

---

### Post by Idefix82 on 2009-06-23
Can you open the terminal, type
```
df -h
```
and paste the output here?

---

### Post by dromichaetes on 2009-06-23
Here is the disk usage:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  2.5G   11G  19% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M  100K  249M   1% /var/run
varlock               249M     0  249M   0% /var/lock
udev                  249M  148K  249M   1% /dev
tmpfs                 249M  132K  249M   1% /dev/shm
lrm                   249M  2.4M  247M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda5              31M   15M   15M  50% /boot
/dev/sda7              13G  1.7G   11G  14% /home

```

When I installed Ubuntu I reserved 32 Mb to /boot. Was this a mistake?

---

### Post by Idefix82 on 2009-06-23
> **dromichaetes said:**
> Here is the disk usage:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  2.5G   11G  19% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M  100K  249M   1% /var/run
varlock               249M     0  249M   0% /var/lock
udev                  249M  148K  249M   1% /dev
tmpfs                 249M  132K  249M   1% /dev/shm
lrm                   249M  2.4M  247M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda5              31M   15M   15M  50% /boot
/dev/sda7              13G  1.7G   11G  14% /home

```

The /boot partition is only 31 MB. That's a little bit too little. It's enough to contain one kernel, but as soon as you want to update to a newer kernel, the partition must, at least temporarily, be able to hold 2 kernels. Personally, I actually always keep at least two kernels, in case one of them breaks. I would recommend you give the /boot partition about 100 MB. However, I am not sure if GRUB can break if you change the size of the /boot partition, so you might have to reinstall grub after that.

To change partition sizes, you need to boot from the LiveCD since you can only change partitions that are not mounted.

---

### Post by drs305 on 2009-06-23
The boot partition should not break if the partition is only resized. It should keep the same uuid. However, it would be best to check before and after the resizing:
```

sudo blkid -c /dev/null

```

---

### Post by dromichaetes on 2009-06-23
Idefix82 (just a happy coincidence?!),

thank you for the help. Just to be on the safe side, when I resize the '/boot' partition using the LiveCD I make sure the "format"-button remains unchecked to make sure the Grub will not be deleted. But how do I reinstall Grub if it crashes nonetheless?

---

### Post by drs305 on 2009-06-23
> **dromichaetes said:**
> Idefix82 (just a happy coincidence?!),

thank you for the help. Just to be on the safe side, when I resize the '/boot' partition using the LiveCD I make sure the "format"-button remains unchecked to make sure the Grub will not be deleted. But how do I reinstall Grub if it crashes nonetheless?

You aren't going to use the LiveCd to *reinstall*. Select "try without installing", go to the Desktop, install gparted if it's not there, then run gparted (System, Partition Editor).

Or even better, get the SystemRescueCD .iso and make a rescue CD. It has lots of recovery tools on it and is a good thing to have:
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by dromichaetes on 2009-06-23
> **drs305 said:**
> You aren't going to use the LiveCd to *reinstall*. Select "try without installing", go to the Desktop, install gparted if it's not there, then run gparted (System, Partition Editor).



Thank you very much. :) Not the brightest of my days, isn't it, lol ?

---

### Post by dromichaetes on 2009-06-23
ok, I used gparted to free some space from sda7. But now when I try to resize/move the sda5 it doesn't let me add the free space made available (around 71 Mb). What am I doing wrong?

---

### Post by Idefix82 on 2009-06-23
I guess sda7 sits behind sda5? Then you need to move sda7 to the end of the disk, so that the free space comes right to the right of sda5.

---

### Post by drs305 on 2009-06-23
The free space must be adjacent to the /boot partition and both must be either inside or both outside the extended partition (light blue border).

---

### Post by dromichaetes on 2009-06-23
Solved. Thank you guys for the advice. For any other noob out there, just be aware that you can free disk space either in front of a partition or at the end of it. I was reading what gparted was telling me, but I wasn't really understanding...

One more thing: be prepared for a long wait, especially when the partition you want to move is large. I freed 70 Mb in front of a partition of 12.6 Gb and I had to wait about 50 minutes until the partition was moved to the right. But hey, the update is working fine now with a 100 Mb in '/boot'

---


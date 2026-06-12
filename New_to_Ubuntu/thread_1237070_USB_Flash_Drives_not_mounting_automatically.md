---
title: "USB Flash Drives not mounting automatically"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by Stunt Double on 2009-08-11
I'm running Ubuntu 8.04 on a Dell Dimension 4500. When I upgraded from 2.6.24-19 to 2.6.24-24, the flash drives stopped mounting automatically. It's not the computer because the USB drives still auto-mount in the earlier kernel.
   When I was trouble-shooting the problem, I found that running "lsusb" would mount the drives. 
   Is there a way to auto-mount the drives without the "lsusb"?
Thanks

---

### Post by jerrrys on 2009-08-11
i have had the same problem, last time flash drive would automount was with 8.04.01 which was the 24.19 kernel and gave up looking for a fix. im running a ibm8671 (x235)...

---

### Post by kansasnoob on 2009-08-11
Try installing 'pmount'. It's in Synaptic or can be installed from Terminal:

```
sudo apt-get install pmount
```

If the drive is formatted as ntfs you may also find 'ntfsprogs' to be useful. Also in Synaptic.

---

### Post by Stunt Double on 2009-08-11
I have pmount installed but it doesn't work. Only "lsusb" works.
   I run 8.04 on 6 different computers but only have the auto-mount problem on the Dell Dimension.
   It may be that the update was somehow corrupted but the USB problem is the only one that I have noticed.
   With luck, it will be corrected with the next kernal upgrade.
Thanks

---

### Post by rhythmiccycle on 2009-08-11
i'm not an expert, but
if you think its the kernal why don't you try ubuntu 9? (the newest one)

---

### Post by Stunt Double on 2009-08-11
Update manager says I'm up to date.
I'm staying with 8.04 for the long-term support and knowledge that it is generally trouble-free on all 6 computers, all of which are more than 4 years old.

---


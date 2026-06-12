---
title: "Strange booting between Windows 7 and 10.10, Always in Recovery"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by Aerodynamix on 2010-11-21
So I'm currently dual booting Windows 7 and Ubuntu 10.10. 
I use grub as my bootloader.  The only problem I have with this is that everytime I boot into ubuntu it has to check the check the disks for errors for some reason.  And a lot of times, when I boot into Windows, it decides to run startup recovery.  

Anyone know why this would happen/how I can fix this?  I just updated grub to see if that helped.

---

### Post by drs305 on 2010-11-21
For Ubuntu, you could run a LiveCD and check for errors. 
```
sudo e2fsck -f -y -v /dev/sd**XY**
```
Although unlikely, you could also make sure /etc/fstab isn't set to fsck on every boot (you can change it to 0 0 temporarily to stop scheduled checks).

For Windows, Grub often mislabels the recovery mode as the regular mode. If you have two listings, try the other one to see if it boots into your normal Windows OS.

---


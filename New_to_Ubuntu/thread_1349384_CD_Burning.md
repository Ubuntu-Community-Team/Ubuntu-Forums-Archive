---
title: "CD Burning"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by bestiolinux on 2009-12-08
Plz help!!!
I cannot burn any CD or DVD with my brand new installation of Ubuntu 9.10. I did not have any problem with older ubuntu (9.04), but now if I try, all gets right but in the end I get an error like this : you don't have the permission to the burner! and this makes my CD/DVD unusable!!! Is something in ubuntu 9.10 changed???? I threw away 12 CDs inbetween......
THANXXXXXXXX

---

### Post by ukripper on 2009-12-08
Have you tried using k3b program?

Go to synaptics and put k3b and install it. Then try burning from that.

---

### Post by bestiolinux on 2009-12-08
I've tried with k3b (my favourite) with brasero, with gnomebaker and everything that exists, in my internal and external burner.... ALWAYS THE SAME ERROR! How can I say: "I'm going slightly mad"........ forget the "slightly".... Xcuze me Freddie! ;)
btw... thanx

---

### Post by ukripper on 2009-12-08
can you post output of this command:
```
gedit /etc/fstab
```

---

### Post by SuperSonic4 on 2009-12-08
Do you have cdrkit and dvd+rw-tools installed? These are usually deps of burning programs but you never know

```
sudo apt-get install cdrkit dvd+rw-tools
```

---

### Post by bestiolinux on 2009-12-08
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a122baf8-3f8f-432d-82e9-ec00bb5041af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ada18d89-4081-4fce-ad9f-8bb440c4382e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

nothing new.....

@supersonic: apt-get don't find cdrkit.............

---

### Post by ukripper on 2009-12-08
ok next time when burning cd can you run this command in terminal and then burn cd:
```
sudo k3b
```

This will run k3b with superuser permissions. if this works then it will mean it is definitely permissions issue.

---

### Post by bestiolinux on 2009-12-08
Already done.... after it reminds me thar it will be dangerous for the system to use k3b as SU, I've got the same error, and got another CD to throw away ;)...
I think it'lll be better to re-install the OS.... ****!

---

### Post by ukripper on 2009-12-08
> **bestiolinux said:**
> Already done.... after it reminds me thar it will be dangerous for the system to use k3b as SU, I've got the same error, and got another CD to throw away ;)...
I think it'lll be better to re-install the OS.... ****!

can you post output of this command:
```
dmesg | tail
```

---

### Post by bestiolinux on 2009-12-08
Hi everybody!
thank you very much for the interest! I had to reconfigure my XServer couse malfunctioning and.... I have just burned a DVD with several .avi videos... all well done! I think it was a problem during my installation progress.... I have to try some CDs now, but it seems that I won't have any problems at all. 
Thank you all folks...

---


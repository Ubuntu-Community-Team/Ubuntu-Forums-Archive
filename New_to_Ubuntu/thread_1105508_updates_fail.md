---
title: "updates fail"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-03-24
I have a problem when I try an install updates or even documents it fails...  This is the output from the following command df -h
trinidad@ubuntuser:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             5.7G  5.4G     0 100% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  112K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.9M  2.0G   1% /dev
tmpfs                 2.0G  312K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sda6             5.7G  165M  5.2G   4% /boot
/dev/sda7             121G  2.2G  113G   2% /usr
overflow              1.0M   32K  992K   4% /tmp
/dev/mmcblk0p1        969M  104M  865M  11% /media/disk
/dev/scd0             2.5G  2.5G     0 100% /media/cdrom0
trinidad@ubuntuser:~$ 

can i resize my /user partition and add that to the sda5 partition?  should i reinstall ubuntu?

---

### Post by jakupl on 2009-03-24
Download the Gparted live cd from here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), burn it to a cd as image and boot from it. there you can resize the partitions as you want.

---

### Post by trinidadflores on 2009-03-24
> **jakupl said:**
> Download the Gparted live cd from here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), burn it to a cd as image and boot from it. there you can resize the partitions as you want.

I do have gparted on here would that work or does it need to be the live cd for gparted

---

### Post by drs305 on 2009-03-24
Your problem, as you somewhat touched upon, is that your root partition ( / ) is full. Your /boot partition is much larger than it needs to be (even 1GB would be very large) and the /usr partition is just huge. 

A common misconception with new users is that /usr stands for "user". It actually is "unix system resources" and contains system files. It isn't meant to be used to store an individual user's files. Those are normally placed in the user's home folder or on a separate data partition. 

My advice would be to roll /boot and /usr back into root, or at least make /boot smaller (1GB would be more than enough) and put /usr back into / unless you have a specific need for the separate /usr folder. 

Doing this is going to take a bit of manipulation of these three partitions. I am not a big advocate of reinstalling to fix things. In this case, since you probably cannot move space directly from /usr to /, it may be faster to reinstall if this is a relatively new install on which you haven't spent much time tweaking. Moving the partitions around can be accomplished, some of the operations will just take a bit of time.

Just let us know how you would like to proceed and we can work out a plan. If you want to move the partitions a picture of your partitions displayed in gparted would be helpful.

---

### Post by jakupl on 2009-03-24
> **trinidadflores said:**
> I do have gparted on here would that work or does it need to be the live cd for gparted

you need the live cd, because you can't change file systems that are mounted. You can't repartition something you are sitting on already.

---

### Post by trinidadflores on 2009-03-24
> **drs305 said:**
> Your problem, as you somewhat touched upon, is that your root partition ( / ) is full. Your /boot partition is much larger than it needs to be (even 1GB would be very large) and the /usr partition is just huge. 

A common misconception with new users is that /usr stands for "user". It actually is "unix system resources" and contains system files. It isn't meant to be used to store an individual user's files. Those are normally placed in the user's home folder or on a separate data partition. 

My advice would be to roll /boot and /usr back into root, or at least make /boot smaller (1GB would be more than enough) and put /usr back into / unless you have a specific need for the separate /usr folder. 

Doing this is going to take a bit of manipulation of these three partitions. I am not a big advocate of reinstalling to fix things. In this case, since you probably cannot move space directly from /usr to /, it may be faster to reinstall if this is a relatively new install on which you haven't spent much time tweaking. Moving the partitions around can be accomplished, some of the operations will just take a bit of time.

Just let us know how you would like to proceed and we can work out a plan. If you want to move the partitions a picture of your partitions displayed in gparted would be helpful.

What i was figuring was to have the biggest partition for my files in a ext2 format so that i can access my documents in my windows partition. But i dont want the os accessible through windows.

---


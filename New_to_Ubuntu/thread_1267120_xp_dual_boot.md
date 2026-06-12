---
title: "xp dual boot"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by bholswade on 2009-09-15
I have a Dell 530s w/ 300G HD running XP Pro. I have tried to install ubuntu as a dual boot three times.  Each time after the install I select Ubuntu as OS and the update manager list a a bunch of updates.  When I try to update I get a error message that their is not enough hd space. 
I can't remove Ubumtu without the grubb locking the system up and not allowing XP to load.

---

### Post by halitech on 2009-09-15
Did you use WUBI to do the install?
open a terminal and post the results of
```
df -h
```

---

### Post by RJ12 on 2009-09-15
When installing did you use WUBI?
if not do you choose guided install side by side if so move the slider to the left to give ubuntu some space

---

### Post by bholswade on 2009-09-15
> **halitech said:**
> Did you use WUBI to do the install?
open a terminal and post the results of
```
df -h
```
I used the CD. And I let the CD install without any changes.  IE: first choice.

---

### Post by bholswade on 2009-09-15
> **RJ12 said:**
> When installing did you use WUBI?
if not do you choose guided install side by side if so move the slider to the left to give ubuntu some space
I did use side by side. The last time I screwed with the partition I messed up the whole system and had to format and reload XP and all software.  Took me all day.  Not to quick to mess with anything else.

---

### Post by bholswade on 2009-09-15
> **halitech said:**
> Did you use WUBI to do the install?
open a terminal and post the results of
```
df -h
```
I am now in Win not Ubuntu.  Will lose thread if I change?
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

bart@desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   45M  98% /
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G   92K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  160K  1.6G   1% /dev
tmpfs                 1.6G   84K  1.6G   1% /dev/shm
lrm                   1.6G  2.4M  1.6G   1% /lib/modules/2.6.28-11-generic/volatile
bart@desktop:~$

---

### Post by bholswade on 2009-09-15
> **bholswade said:**
> I am now in Win not Ubuntu.  Will lose thread if I change?
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

bart@desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   45M  98% /
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G   92K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  160K  1.6G   1% /dev
tmpfs                 1.6G   84K  1.6G   1% /dev/shm
lrm                   1.6G  2.4M  1.6G   1% /lib/modules/2.6.28-11-generic/volatile
bart@desktop:~$

Is this what you need?

---

### Post by bholswade on 2009-09-15
> **bholswade said:**
> Is this what you need?

At this point how do I removed Ubuntu and just use Win.  I guess I am not able to follow the cryptic commands. I just want to install in windows again.

---

### Post by halitech on 2009-09-15
what happened is you used WUBI to install and it went with the default size for the install (2.3gig). If you want to use it, go back into windows, unistall it from Add/remomve programs and then run the install again but this time make sure you give it more room, probably around 10-15 gig.

---

### Post by bholswade on 2009-09-15
> **halitech said:**
> what happened is you used WUBI to install and it went with the default size for the install (2.3gig). If you want to use it, go back into windows, unistall it from Add/remomve programs and then run the install again but this time make sure you give it more room, probably around 10-15 gig.
I am trying to install on hard drive as dual boot.  Now I want to go back to install in windows.  Can't figure our how to delete grub.  Their are several lines of instructions if I hit E at boot menu.  Can I delete those to prevent grub from locking up system when I remove partition? Can email with instructions.  I don't seem to be able to connect real time here.  @yahoo.com

---

### Post by halitech on 2009-09-15
I'm not completely sure on the steps to remove ubuntu from the windows boot loader if you used wubi to install but you don't have a linux partition, Ubuntu was installed in a file inside windows.

---

### Post by Zero++ on 2009-09-15
> **bholswade said:**
> I am trying to install on hard drive as dual boot.  Now I want to go back to install in windows.  Can't figure our how to delete grub.  Their are several lines of instructions if I hit E at boot menu.  Can I delete those to prevent grub from locking up system when I remove partition? Can email with instructions.  I don't seem to be able to connect real time here.  @yahoo.com

If you want to completely remove ubuntu boot from your XP CD and go to the recovery counsel. Use the fixmbr command to reload the windows master boot record. [Here's a link to help]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true"). After that you will want to reformat the Ubuntu partition to NTFS so you are not wasting space. I would use [Gparted]("http://gparted.sourceforge.net/") (link encolsed) but you should be able to do it pretty hastle free in XP with something that small.

---

### Post by bholswade on 2009-09-15
> **Zero++ said:**
> If you want to completely remove ubuntu boot from your XP CD and go to the recovery counsel. Use the fixmbr command to reload the windows master boot record. [Here's a link to help]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true"). After that you will want to reformat the Ubuntu partition to NTFS so you are not wasting space. I would use [Gparted]("http://gparted.sourceforge.net/") (link encolsed) but you should be able to do it pretty hastle free in XP with something that small.
I will try this.  But my old brain is moving pretty slow.  I have copied the instructions for recovery counsel as well as master boot record.  Will let you know.  thanks for you help.  If this does not work then I will wipe again and start over.
Bart

---

### Post by bholswade on 2009-09-17
> **bholswade said:**
> I will try this.  But my old brain is moving pretty slow.  I have copied the instructions for recovery counsel as well as master boot record.  Will let you know.  thanks for you help.  If this does not work then I will wipe again and start over.
Bart

Thanks for help.  All of you.  Sorry for delay getting back, but had to see VA. Have removed Ubuntu for hd and installed thru Win.  I know that the purist will scream but hey, mellow.  thanks again

---


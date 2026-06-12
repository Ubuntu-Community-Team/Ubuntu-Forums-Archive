---
title: "How do I load Windows now that I have loaded Ubuntu?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by bowingjalks on 2010-02-14
I'm sure this is a common problem but I can't find the thread.  Maybe someone can direct me.

I have downloaded linux Ubuntu, and it has become the default OS program that boots up.  How do I boot up Windows which was the OS before I loaded Ubuntu?

thanks

Gail

---

### Post by MelDJ on 2010-02-14
you can choose between them at startup.

---

### Post by jimingkui on 2010-02-14
When start your machine,you should see a menu list which is called **grub** there you can select which system to boot up.(Maybe need to press ESC to see the grub)

---

### Post by bowingjalks on 2010-02-14
Hi, thanks for that

I pressed ESC and got
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (rm)
Ubuntu 7.10, memtest86*

---

### Post by SecretCode on 2010-02-14
I see you have an old version of Ubuntu (7.10 from Oct 2007 ... the latest version is 9.10). Did you mean to download that version?

Once you have booted into Ubuntu, please open a terminal window (Applications > Accessories > Terminal), enter ```
df -h
``` and post the results in a new post here. Use [ code ][/ code ] tags to preserve the formatting.

Also post the results of ```
sudo fdisk -l
```
- this command will require your login password, which won't display anything while you type it.

---

### Post by mathfreak123 on 2010-02-14
Try running

```
sudo update-grub
```

Then restart, and see what happens.

Since your grub menu only displays Ubuntu 7.10 stuff, I'm thinking it missed your Windows OS. Running update-grub will have it check other OS's you have installed, so it'll add options for those systems into the grub menu the next time you boot up.

---

### Post by buddhaflow on 2010-02-14
Go into the terminal. Type "sudo gedit /boot/grub/menu.lst"

It will open a text editor. One of the first lines is "Default 0"

Changing the number from 0 to 1 or 2 will change it to the next operating system.

To find which one is Windows, go to the bottom of the file, and you will see your options listed. Remember that it starts counting at 0. 

So if it says:

title    Ubuntu blah blah 
blah blah
blah blah

title    Something Else blah blah 
blah blah
blah blah

title    Windows blah blah 
blah blah
blah blah

You would set it to "default 2" for Windows.

---

### Post by bowingjalks on 2010-02-14
sorry I really dont know what I am doing, but here is the log that you requested.

[code]
gail@mumslaptop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             142G  2.1G  132G   2% /
varrun               1010M  100K 1010M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M   92K 1010M   1% /dev
devshm               1010M     0 1010M   0% /dev/shm
lrm                  1010M   34M  976M   4% /lib/modules/2.6.22-14-generic/volatile
gail@mumslaptop:~$ sudo fdisk -l
[sudo] password for gail:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18704   150239848+  83  Linux
/dev/sda2           18705       19457     6048472+   5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris
gail@mumslaptop:~$

---

### Post by miklcct on 2010-02-14
Your HDD has already messed up. There are no Windows inside.

---

### Post by da burger on 2010-02-14
According to fdisk you haven't got windows installed. You may have accidentally overwritten it when you installed Ubuntu. Was all your important data on windows backed up??

---

### Post by SecretCode on 2010-02-14
I was afraid of this.

Your hard disk only has Linux on it - there are no windows partitions in this machine.

I'm scared to ask - but did you have important files in your windows installation? Do you have any backups?

---

### Post by da burger on 2010-02-14
It might be to late but this is worth a try if you don't have backups of important data: [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Give it a shot and post back here if it works.

---


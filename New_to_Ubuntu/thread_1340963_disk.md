---
title: "/ disk"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2009-11-29
could any one please tell me how to clean up the / disk? i encountered this problem while installing the packages!

---

### Post by 1991sudarshan on 2009-11-29
[quote=1991sudarshan;8406922]could any one please tell me how to clean up the / disk? i encountered this problem while installing the packages!

---

### Post by Virtual Liberty on 2009-11-29
> **1991sudarshan said:**
> could any one please tell me how to clean up the / disk? i encountered this problem while installing the packages!

You encountered .. what problem ?

You can clear the cache ( Aptitude ) by executing the following command:
```
sudo apt-get clean
```

---

### Post by 1991sudarshan on 2009-11-29
but i did that also then too it is showing the same message!

---

### Post by Virtual Liberty on 2009-11-29
> **1991sudarshan said:**
> but i did that also then too it is showing the same message!

Please be more specific. What message ?

---

### Post by halitech on 2009-11-29
what is the message  you are getting? hard to help when all we know is you are getting an error but you don't tell us what the error message actually says

---

### Post by NoaHall on 2009-11-29
Okay, now try ```
sudo apt-get autoclean && sudo apt-get autoremove
```

You'll need to un-install some programs, by the sound of it.

---

### Post by 1991sudarshan on 2009-11-29
it show like this

sreenivassudarshan@sreenivassudarshan-desktop:~$ sudo apt-get autoclean && sudo apt-get autoremove
[sudo] password for sreenivassudarshan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 261 not upgraded.
sreenivassudarshan@sreenivassudarshan-desktop:~$

---

### Post by 1991sudarshan on 2009-11-29
the error message show by the update manager is as follows

[SIZE=4]
"Not enough free disk space"

The upgrade needs a total of 85.1M free space on disk '/'. Please free at least an additional 85.1M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.[/SIZE]

---

### Post by halitech on 2009-11-29
what is the output of
```
df -h
```

---

### Post by 1991sudarshan on 2009-11-29
[SIZE=3]sreenivassudarshan@sreenivassudarshan-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda10            2.3G  2.2G     0 100% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  108K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  164K 1002M   1% /dev
tmpfs                1003M  204K 1002M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/sda5              59G   18G   42G  30% /media/disk
/dev/sda6              64G   34G   30G  53% /media/disk-1
/dev/sda8             2.3G  2.3G     0 100% /media/disk-2
/dev/sda7              67G   26G   42G  39% /media/disk-3
[/SIZE]

---

### Post by 1991sudarshan on 2009-11-29
sreenivassudarshan@sreenivassudarshan-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda10            2.3G  2.2G     0 100% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  108K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  164K 1002M   1% /dev
tmpfs                1003M  204K 1002M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/sda5              59G   18G   42G  30% /media/disk
/dev/sda6              64G   34G   30G  53% /media/disk-1
/dev/sda8             2.3G  2.3G     0 100% /media/disk-2
/dev/sda7              67G   26G   42G  39% /media/disk-3

---

### Post by NoaHall on 2009-11-29
Looks like you need to resize. You should give / around 10GB

---

### Post by 1991sudarshan on 2009-11-29
so how to resize

---

### Post by halitech on 2009-11-29
no wonder its full, you only gave Ubuntu 2.3gig to use
[color="red"]/dev/sda10 2.3G 2.2G 0 100% /[/color]

you can try using the info here to resize your partition

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by 1991sudarshan on 2009-11-29
**System** > **Administration** > [B]Partition Editor


this is not available in my menu
[/B]

---

### Post by Virtual Liberty on 2009-11-29
You should do all the partitioning from the LiveCD ( so that none of the partitions would be mounted ). 
Anyway, for the future reference, you need GParted.

```
sudo apt-get install gparted
```

---

### Post by halitech on 2009-11-29
you may need to install it but you can't do it on a mounted drive, you will need to boot from the live cd to resize the partition

---

### Post by 1991sudarshan on 2009-11-29
buti was given only one cd! will it act as as a live cd?

---

### Post by 1991sudarshan on 2009-11-29
actually my system had window xp and kubuntu 9.04 and windows has crashed and so i installed ubuntu and another problem which is face with firefox and i'm not able to nagivate the browser properly!

---

### Post by NoaHall on 2009-11-29
Yes.

And as to your second problem - make a new thread with that in it.

---

### Post by Virtual Liberty on 2009-11-29
> **1991sudarshan said:**
> buti was given only one cd! will it act as as a live cd?

Can you boot into Ubuntu from the CD ( *Try Ubuntu before installing* menu item ) ?

> **NoaHall said:**
> Yes.

Not always. Alternate and Minimal CDs will not act like a LiveCD.

---

### Post by NoaHall on 2009-11-29
> **Virtual Liberty said:**
> Can you boot into Ubuntu from the CD ( *Try Ubuntu before installing* menu item ) ?



Not always. Alternate and Minimal CDs will not act like a LiveCD.

I doubt he was given the alternate/minimal cd.

---

### Post by 1991sudarshan on 2009-11-29
ya i will do it in few day i'm planning to switch over too mas os! what is your stand on this? is it possible to operate mac and ubuntu side by side?

---

### Post by NoaHall on 2009-11-29
> **1991sudarshan said:**
> ya i will do it in few day i'm planning to switch over too mas os! what is your stand on this? is it possible to operate mac and ubuntu side by side?

You can't install Mac OS on non-mac os hardware. And yes they can operate side by side.

---

### Post by 1991sudarshan on 2009-11-29
but most of my friends are using it on non mac hard disk

---

### Post by NoaHall on 2009-11-29
> **1991sudarshan said:**
> but most of my friends are using it on non mac hard disk

This is against the rules/law. And how are you sure it's Mac OS ? It could easily be Linux. Mine is often mistaken for Mac OS X.

---

### Post by 1991sudarshan on 2009-11-29
mac os 10 or 9 MY FIREND said that he will give the cd

---

### Post by NoaHall on 2009-11-29
> **1991sudarshan said:**
> mac os 10 or 9 MY FIREND said that he will give the cd

Please don't talk about this here. It's against the rules.

---

### Post by Virtual Liberty on 2009-11-29
> **1991sudarshan said:**
> mac os 10 or 9 MY FIREND said that he will give the cd

Offtopic.

---

### Post by 1991sudarshan on 2009-11-29
sorry let us stick to the topic some times back my firefox too crashed! ls help

---

### Post by NoaHall on 2009-11-29
> **1991sudarshan said:**
> sorry let us stick to the topic some times back my firefox too crashed! ls help

Wait, first, have you resized your / ?

And like I've said, make a NEW THREAD for the FIREFOX PROBLEM.

---

### Post by Virtual Liberty on 2009-11-29
> **1991sudarshan said:**
> sorry let us stick to the topic **some times back** my firefox too crashed! ls help

If it's not broken as you type, there's literally no way we could help you with that.

---


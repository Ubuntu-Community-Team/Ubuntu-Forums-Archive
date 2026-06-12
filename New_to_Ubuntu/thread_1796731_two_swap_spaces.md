---
title: "two swap spaces"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by konsolelover on 2011-07-04
hey, i have just partitioned my new 250 GB hard disk n planned to install two distros. So i created 2 swap spaces of 3 -3 GB (as my RAM is 3 GB)and other ext4 partitions using Gparted. When i installed Ubuntu 11.04 32 bit in my one primary partition of 30 GB , it didn't ask me to choose swap area ....i haven't installed my other distro yet...So i'm not sure which partition did it use(or may be it haven't selected any of that one) but i checked to hibernate the system and it worked properly....so i am in little problem thinking about assigning swap space to my second distro ( Slackware ) installation(i'll install it after few days)....plz help....
  n also i need one another little help....
as my battery is dead now and doesn't have any power backup so i want to set my system to go for hibernate when power gets off......TIA

---

### Post by mutley89 on 2011-07-04
You only need 1 swap space.  Afaik linux just uses whatever it finds, you don't need to allocate it

---

### Post by konsolelover on 2011-07-04
if two distro can work with one swap space then if i hibernate my one distro then log into my second distro and again hibernate it then i dont think it'll save first distro state...correct me if i m wrong...help

---

### Post by CatKiller on 2011-07-04
You only need one swap partition. Any distro can use it. You can nuke one and assign the space to another partition. Mounting a swap partition is the same as mounting any other partition: you use **/etc/fstab**.

```
UUID=152ee2b7-41a7-4a0d-86ab-575beecf3157 none            swap    sw              0       0
```Replace the UUID with whatever the UUID of your swap partition is, which you can find out with **blkid**.

EDIT:
If you want to use a different swap partition for each, you can. Just have an fstab entry in one for one partition, and an entry in the other for the other partition.

EDIT 2:
If you're running multiple distros for whatever reason, have you considered virtualisation?

---

### Post by mcduck on 2011-07-04
> **konsolelover said:**
> if two distro can work with one swap space then if i hibernate my one distro then log into my second distro and again hibernate it then i dont think it'll save first distro state...correct me if i m wrong...help

True, if you want to hibernate one of the two distributions, you'll need separate swap partitions for each.

If you don't use hibernations, then sharing the same swap with all Linux installs works fine.

Anyway, to check which partition(s) Ubuntu is using for swap you can just read the */etc/fstab* file, which is where the swap, like all the other partitions, is configured.

---

### Post by konsolelover on 2011-07-04
i checked /etc/fstab and found ..
UUID=34a4d5e7-9f03-41c4-ac39-c03c2a3285ad /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=5587c177-bf62-438a-acaf-d2f7b3789b34 none            swap    sw              0       0
# swap was on /dev/sda5 during installation
UUID=6394b4b3-ef54-4fca-85dd-78ade20090f8 none            swap    sw              0       0


as i'm newbie to linux , i don't know how to manage two swap spaces with two distros , plz illustrate with enough details...

and yes i considered VBox and Vmware to install other distro but my main focus is to learn Slackware and see its performance(speed) which will be degraded on virtual machine.....

---

### Post by mcduck on 2011-07-04
> **konsolelover said:**
> i checked /etc/fstab and found ..
UUID=34a4d5e7-9f03-41c4-ac39-c03c2a3285ad /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=5587c177-bf62-438a-acaf-d2f7b3789b34 none            swap    sw              0       0
# swap was on /dev/sda5 during installation
UUID=6394b4b3-ef54-4fca-85dd-78ade20090f8 none            swap    sw              0       0


as i'm newbie to linux , i don't know how to manage two swap spaces with two distros , plz illustrate with enough details...

and yes i considered VBox and Vmware to install other distro but my main focus is to learn Slackware and see its performance(speed) which will be degraded on virtual machine.....
Open a terminal and run "gksudo gedit /etc/fstab", and remove (or comment out by adding a # to the beginning) one of the swap partitions and save the file. Do the same on your other Linux install, but for the different swap partition of course.

---

### Post by konsolelover on 2011-07-04
@mcduck 
thnx dude , i'll do that with other distro when i'll install it.....
when i tried to wake up my machine from hibernation it took more time than usual booting and also i got some error message like (before hibernation completed)
ata3:........device not ready
ata4:.........device not ready
i have given 3 Gb space to each swap.....

---

### Post by mcduck on 2011-07-04
> **konsolelover said:**
> @mcduck 
thnx dude , i'll do that with other distro when i'll install it.....
when i tried to wake up my machine from hibernation it took more time than usual booting and also i got some error message like 
ata3:........device not ready
ata4:.........device not ready
i have given 3 Gb space to each swap.....

You'll want to restart the computer properly once after you have edited the swap configuration.

Also you might need to configure things again after installing Slawackware, if it formats the swap partition(s) their UUID's will change and you need t edit fstab in Ubuntu to use the new UUID. But I suppose it's best to worry about that if it happens, as there isn't anyhting you could do beforehands anyway. :)

---

### Post by konsolelover on 2011-07-04
thank y'll :D

---


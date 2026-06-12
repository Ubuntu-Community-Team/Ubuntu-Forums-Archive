---
title: "ubuntu on desktop"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by Kirkland14 on 2010-07-10
I seem to be having a problem loading ubuntu to a desktop I just got.  it's a compaq with a 3000+ amd sempron with 512mb mem, 80gb pc.  it has XP and I tried to install ubuntu as a dual boot as well.  now it won't load either OS.  as soon as it starts to load it says it cant find the ROOT.  Any Ideas?  thanks.

Kevin

ps  I thought about reinstalling ubuntu but it already shows it on my HDD

pss  i tried to run it off of the live cd and when it finally did load it loaded somewhere around 1000 file managers and then went to a screen with a computer and it said ubuntu underneath w/ a login button.  when I clicked it a cancel button was added to the screen but it did not do anything

Thanks again

---

### Post by techunit on 2010-07-10
> **Kirkland14 said:**
> I seem to be having a problem loading ubuntu to a desktop I just got.  it's a compaq with a 3000+ amd sempron with 512mb mem, 80gb pc.  it has XP and I tried to install ubuntu as a dual boot as well.  now it won't load either OS.  as soon as it starts to load it says it cant find the ROOT.  Any Ideas?  thanks.

Kevin

ps  I thought about reinstalling ubuntu but it already shows it on my HDD
What procedure did you use to install Ubuntu as a Dual boot? You may have corrupted the windows partition. 

How did you shrink the windows partition

Are You Using GRUB or are you using Windows Boot Loader?

This information is important to fixing you problem. I understand that this may be complicated to understand so ask the questions you must so we can help you.

---

### Post by theozzlives on 2010-07-10
Try booting off the XP CD and choose recovery console. After you get to the command prompt, do:
```
fdisk /mbr
fixboot
```
You should be able to boot Windows. Then boot off the Ubuntu CD and choose "manual partitioning" reselect the root (/) and re-install. That should hook you up!

---

### Post by Kirkland14 on 2010-07-10
> **techunit said:**
> What procedure did you use to install Ubuntu as a Dual boot? You may have corrupted the windows partition. 

How did you shrink the windows partition

Are You Using GRUB or are you using Windows Boot Loader?

This information is important to fixing you problem. I understand that this may be complicated to understand so ask the questions you must so we can help you.


so in order

1.  I used a prexisting copy of ubuntu(the same one that i used for my laptop.  I went to boot at startup and went to cd rom and the disk started like it should  I chose install,   I used the partitioning option like I did before that does it for me.  it finished and restarted but then said ubuntu wasn't loadable.  I loaded it by just running off the disk and it started but then a bunch of file managers started running and then it crashed

2. was included in last paragraph

3. I don't know how to use GRUB or really know what it is.  All I know is I did it the same way as before but now I have a problem.  Can the processor not handle 10.4?

ps  I got winXP going from the dual boot and it shows the recovery parts of ubuntu at the dual boot choice(ubuntu x3) but ubuntu still won't load

---

### Post by theozzlives on 2010-07-10
Noooooooooooo! your CPU is fine, try my instructions above!

---

### Post by Kirkland14 on 2010-07-10
> **theozzlives said:**
> Noooooooooooo! your CPU is fine, try my instructions above!

i don't have the XP recovery cd. now winXP works but it won't find the ethernet

---

### Post by sandyd on 2010-07-10
> **Kirkland14 said:**
> i don't have the XP recovery cd. now winXP works but it **won't find the ethernet**
sounds like hardware failure.

is it displaying in the device manager (RIght CLIck "MY COmputer", click properties, and go to device manager).

If it is, thats good, just reinstall the drivers for it.

If it isn't... well... take the card out, and put it back in.

---

### Post by Kirkland14 on 2010-07-10
so when I try and boot Ubuntu this is what it says

```

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev
ALERT! /dev/disk/by-uuid/67893doc-d728-4257-8585-b03032b9a5206 does not exist. Dr
opping to a shell!


Busybox v1/13/1 (Ubuntu 1:1.13.3-1unutu11) built-in shell (ash)

```

---

### Post by Kirkland14 on 2010-07-10
> **carlee said:**
> sounds like hardware failure.

is it displaying in the device manager (RIght CLIck "MY COmputer", click properties, and go to device manager).

If it is, thats good, just reinstall the drivers for it.

If it isn't... well... take the card out, and put it back in.
   i will try that .

Thanks

---

### Post by sandyd on 2010-07-10
> **Kirkland14 said:**
> so when I try and boot Ubuntu this is what it says

```

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev
ALERT! /dev/disk/by-uuid/67893doc-d728-4257-8585-b03032b9a5206 does not exist. Dr
opping to a shell!


Busybox v1/13/1 (Ubuntu 1:1.13.3-1unutu11) built-in shell (ash)

```
Try setting the correct UUIDS from a livecd

run
```

blkid
```to get the UUIDS for each parttion.

Then edit the /boot/grub/grub.cfg file to reflect the correct UUIDs.

You can also try (change /dev/sda1 to the correct partition listed in fdisk)
```

sudo mount */dev/sda1 */mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
update-grub2
exit

```

and ANY livecd will do, as long as it is the same architecture as the version you installed on the system. i.e. x64bit installation, x64 bit livecd

---

### Post by Kirkland14 on 2010-07-10
> **carlee said:**
> sounds like hardware failure.

is it displaying in the device manager (RIght CLIck "MY COmputer", click properties, and go to device manager).

If it is, thats good, just reinstall the drivers for it.

If it isn't... well... take the card out, and put it back in.

1st things first.  the eternet is detected but when I try and log on to the internet it won't log on.  So you say pull the card?  How do I know which card to pull[NOOB].  Thanks

Kevin

---

### Post by sandyd on 2010-07-10
> **Kirkland14 said:**
> 1st things first.  the eternet is detected but when I try and log on to the internet it won't log on.  So you say pull the card?  How do I know which card to pull[NOOB].  Thanks

Kevin
eh. if its detected, you don't need to pull it.
Restart your router. Some routers such as mine hate it when we switch the names of our computers, and as a result, they don't identify us properly and dont give us a correct conenction

---

### Post by Kirkland14 on 2010-07-10
> **carlee said:**
> eh. if its detected, you don't need to pull it.
Restart your router. Some routers such as mine hate it when we switch the names of our computers, and as a result, they don't identify us properly and dont give us a correct conenction
a

so now with ubuntu i ran it from the liveCD.  I installed all the upgrades it said to and then I got a prob w/ apport.  it says to upgrade: libc-bin, libc6, python-apt, and tzdata.  How do I do this. Thanks 

your awesome

Kevin

  PS I'm hardwired to the router if that matters

pss  i can get on line on the ubuntu live

---

### Post by sandyd on 2010-07-10
> **Kirkland14 said:**
> a

so now with ubuntu i ran it from the liveCD.  I installed all the upgrades it said to and then I got a prob w/ apport.  it says to upgrade: libc-bin, libc6, python-apt, and tzdata.  How do I do this. Thanks 

your awesome

Kevin

ps  i'm hardwired to the routher if that matters
u don't need to update if ur running it from the livecd.
just either try installing it again, or try the commands listed abve

---

### Post by Kirkland14 on 2010-07-10
> **carlee said:**
> u don't need to update if ur running it from the livecd.
just either try installing it again, or try the commands listed abve

but won't it add to my HD when I reinstall?

---

### Post by sandyd on 2010-07-11
> **Kirkland14 said:**
> but won't it add to my HD when I reinstall?

go to system -> administration -> gparted, delete the partition, and when partitioning ubuntu, select "use largest block of free space".

---

### Post by Kirkland14 on 2010-07-11
so i tried I actually just used my gparted cd to erase the partition for Ubuntu and reinstalled it.  I installed and ejected the cd like it should but when I tried to boot up again from the HDD again I got this for the second time
```

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev
ALERT! /dev/disk/by-uuid/67893doc-d728-4257-8585-b03032b9a5206 does not exist. Dr
opping to a shell!


Busybox v1/13/1 (Ubuntu 1:1.13.3-1unutu11) built-in shell (ash)
```I don't get it

ps  it works off the live cd


could this free pc just not be able to handle this version of Linux?  Should I try a previous version?

---


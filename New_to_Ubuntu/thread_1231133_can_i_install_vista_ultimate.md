---
title: "can i install vista ultimate ???"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-08-04
i just got a copy of vista ultimate and need to know if i can install it with my current partition set up...  

i dont remember the command to check how my partitions are set up...

help with command ???

thanks...

---

### Post by HostBot on 2009-08-04
When you install Windows you will most likely be asked to partition your HD with a windows 

partition, then it can install. Then you can reinstall Ubuntu.

---

### Post by HavocXphere on 2009-08-04
Vista needs to be activated, so a "copy" won't fly.

As for the question, google repairing grub. Basically vista blows grub away and then you need to fix it again...then both *nix and vista are listed in grub.

---

### Post by -=hazard=- on 2009-08-04
> **NOTAGEEK said:**
> i just got a copy of vista ultimate and need to know if i can install it with my current partition set up...  

i dont remember the command to check how my partitions are set up...

help with command ???

thanks...


$df              (in kilobytes)

$df -h            (in gigabytes)

Installing windows after Linux will create problems because windows doesn't recognize other distros.

---

### Post by superprash2003 on 2009-08-04
you could install vista after which you would need to follow this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) .. presuming you are planning on a dual boot

---

### Post by NOTAGEEK on 2009-08-04
> **HavocXphere said:**
> Vista needs to be activated, so a "copy" won't fly.

As for the question, google repairing grub. Basically vista blows grub away and then you need to fix it again...then both *nix and vista are listed in grub.


poor choice of verbiage from a non-geek !!!  this is a new retail unopened vista ultimate os and i would like to install the 64 bit version !!! 

i would like to check the way my partitions are currently set up 2 c if i am ok the way they r set...

thanks...

---

### Post by NOTAGEEK on 2009-08-04
> **superprash2003 said:**
> you could install vista after which you would need to follow this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) .. presuming you are planning on a dual boot

ok i think i had better rephrase my question...

**what is the command to look at my current partitions ???**

---

### Post by lisati on 2009-08-04
> **NOTAGEEK said:**
> ok i think i had better rephrase my question...

**what is the command to look at my current partitions ???**

```
fdisk -l
```
(that's little "ell" not number one)

---

### Post by NOTAGEEK on 2009-08-04
> **lisati said:**
> ```
fdisk -l
```(that's little "ell" not number one)


thanks---i needed sudo...

sudo fdisk -l
[sudo] password for topsecret: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc0fdc0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       26747   195310237+  83  Linux
/dev/sda3           26748       27355     4883760   82  Linux swap / Solaris

---

### Post by kayvortex on 2009-08-04
It looks like you have 11557 cylinders free, which is about 88Gb. That should be plenty for Vista, but remember to put it on a primary partition. Also, since your other three partitions are primary too, that's all the partitions you can have on that disk, so you might as well use all the space up.

As already mentioned, you'll have to reinstall grub after you install Vista since it will write over the MBR and all that will happen when you boot up is that Vista will start up. Take a look [here]("http://ubuntuforums.org/showthread.php?t=224351") for instructions on how to reinstall grub.

---

### Post by NOTAGEEK on 2009-08-05
> **kayvortex said:**
> It looks like you have 11557 cylinders free, which is about 88Gb. That should be plenty for Vista, but remember to put it on a primary partition. Also, since your other three partitions are primary too, that's all the partitions you can have on that disk, so you might as well use all the space up.
 
As already mentioned, you'll have to reinstall grub after you install Vista since it will write over the MBR and all that will happen when you boot up is that Vista will start up. Take a look [here]("http://ubuntuforums.org/showthread.php?t=224351") for instructions on how to reinstall grub.
 
 
thanks kayvortex---i ended up just installing 64 bit vista ult for now my ubuntu was a 32 bit disc that i bought on ebay... later i will install 64 bit ubuntu as soon as my pc experience and know how increases...

---

### Post by Tux118 on 2009-08-05
I seriously would not suggest Windows Vista. It is bigger, slower, has more pop-up messages, and things are not compatible. If you want a Windows, I would get Windows XP, 2003, or 7 when it releases.

---

### Post by tarps87 on 2009-08-05
> **NOTAGEEK said:**
> thanks kayvortex---i ended up just installing 64 bit vista ult for now my ubuntu was a 32 bit disc that i bought on ebay... later i will install 64 bit ubuntu as soon as my pc experience and know how increases...

I would suggest downloading Ubuntu from here:
[http://www.ubuntu.com/](http://www.ubuntu.com/)
Or you can order a free copy from here:
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Although there is noting to stop people from selling Ubuntu on at a profit, but I would advise against buying a copy from ebay as you don't know if the seller has tampered with the source code. Just a warning.

---

### Post by Sef on 2009-08-05
> ...but remember to put it on a primary partition.Windows needs to be on your first primary partition.

---

### Post by Mark Phelps on 2009-08-05
> **Tux118 said:**
> I seriously would not suggest Windows Vista. It is bigger, slower, has more pop-up messages, and things are not compatible. If you want a Windows, I would get Windows XP, 2003, or 7 when it releases.

Exactly what does this remark have to do with the op's request?? He already indicated that he has a retail DVD and simply wants to know how to install it.

---

### Post by kayvortex on 2009-08-05
> Windows needs to be on your first primary partition.

Yes, but it wouldn't be that much of problem, would it? Windows wont recognize the ext3 partitions (I'm not sure about the swap partition come to think of it), so there shouldn't be any problems with disk labels.

> Although there is noting to stop people from selling Ubuntu on at a profit, but I would advise against buying a copy from ebay as you don't know if the seller has tampered with the source code. Just a warning.

I'd second that. Why buy it from ebay when you can download it for free?

I'd also be careful with the 64bit version. I don't know about the situation now, but my early experience was that some programs/libraries had yet to be built for that architecture. In my case, the lack of a fan-controlling daemon for my Inspiron 9400 was too dangerous a situation to run the 64bit version on my laptop. But, if everything seems to run fine on your system, then stick with it.

---

### Post by tarps87 on 2009-08-06
> **kayvortex said:**
> Yes, but it wouldn't be that much of problem, would it? Windows wont recognize the ext3 partitions (I'm not sure about the swap partition come to think of it), so there shouldn't be any problems with disk labels.


It's a windows thing, it wants to be on the first partition regardless of if it understands any of the other partitions, or at least this is the case up to xp, when I tried vista that was on the first primary partition too. It will run happily on the first partition of another (slave) hard drive.
I don't know why there is this problem but I can guess it is related to the bootloader windows uses

> **kayvortex said:**
> 
I'd second that. Why buy it from ebay when you can download it for free?

I'd also be careful with the 64bit version. I don't know about the situation now, but my early experience was that some programs/libraries had yet to be built for that architecture. In my case, the lack of a fan-controlling daemon for my Inspiron 9400 was too dangerous a situation to run the 64bit version on my laptop. But, if everything seems to run fine on your system, then stick with it.

I'm using the 64bit version on my desktop and haven't had any incompatibility problems so far, can't say about the fan daemon as I don't have a Inspiron 9400

---

### Post by NOTAGEEK on 2009-08-06
thanks to all...
 
thread closed...

---


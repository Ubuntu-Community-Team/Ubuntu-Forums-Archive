---
title: "New side by side Ubuntu Install needs more space after update"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by dixcuxx on 2011-07-26
I was using Windows XP with my thinkpad T60, then I decided to install Ubuntu 11.04 side by side. I have around 8GB free in my D:, and in ubuntu installation, I just choose the default kind and it has detected my D: has most space left and use that. D: is with NTFS format. Ubuntu installation was successfull and I checked the new ext4 is about 3.6Gz size. I did software update in ubuntu, then there is pop up saying it only has around 10MB left. 

I run the Windows XP, and see the D: has around 2GB left. 

So how can I free more space from D: to Ubuntu ext4? And where is the rest of the space? Even after update the Ubuntu should be around 4GB, with 2GB free in D: as I see in Windows XP, there should be 2GB left. I think I saw there is something 2GB doing something, I am not next to the computer and not at home now so cannot check.

Thanks everyone, by the way the new installation of Ubuntu looks very cool and effective.

My T60 has long term trouble with XP that it would hang when I keep using the red dot or the detective pad, sometimes even I just touch any of these two then the windows hang, the only choice would be using usb mouse. I check many things online and seem like it is a bug by lenovo that they don't want to fix.

Ubuntu doesn't have that problem and everything is just smooth, my T60 cpu doesn't support 64bits, if not I would install 64bits and feel the fastest possible way:popcorn:

---

### Post by jerrrys on 2011-07-26
open a terminal and enter:

df -Th

and please post the result

---

### Post by wildmanne39 on 2011-07-27
Hi, also here is a guide on resizing partitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by dixcuxx on 2011-07-27
> **wildmanne39 said:**
> Hi, also here is a guide on resizing partitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

Can I use partitions magic to do that? I have a bootable XP disc which has partitions magic, but the disc is kind of old, like 2 to 3 years ago, I am not sure if it can work with ext4.

Base on my understanding, I need to resize my D: partitions to get free space, then add the free space to the ext4, correct?

---

### Post by wildmanne39 on 2011-07-27
Hi, boot the ubuntu livecd and use gparted, you need to be very careful with partitions.

Also read that page I gave you very carefully.

---

### Post by amjjawad on 2011-07-27
If you are trying to resize a Windows Partition, then you need to use Windows Tool/Program to do that.

If you are trying to resize Linux Partition, then as explained by wildmanne39, run the LiveCD, go to:

System > Administration > GParted

and resize the desired partition.


If you have lots of problems with XP, I suggest to backup your important files (better to use external HDD) and then format your HDD (wipe everything) and start a fresh new Ubuntu installation ;)

Make sure to backup your data in both XP and Ubuntu.

Good luck :)

---

### Post by Mark Phelps on 2011-07-27
You should be able to resize XP partitions with GParted without problems; it's Vista and Win7 that give it problems.

But, you could also download, install, and use the free version of EASEUS Partition Master (in MS Windows) if you don't want to risk using Partition Magic.

---

### Post by dixcuxx on 2011-07-27
> **Mark Phelps said:**
> You should be able to resize XP partitions with GParted without problems; it's Vista and Win7 that give it problems.

But, you could also download, install, and use the free version of EASEUS Partition Master (in MS Windows) if you don't want to risk using Partition Magic.

I use Gparted to resize NTFS, and then it somehow has error. Now I can see there is D driver, but it cannot be access. If I use windows XP, then it even asks me to format the D: when I try to access it. I use recovery problem and then can see almost everything is still inside the partition, but I don't know if there is anyway to just reactive this partition and use it. Any idea?

Base on this experience, I don't suggest to reize NTFS with gparted.

---

### Post by amjjawad on 2011-07-28
Hi,

From Terminal, please issue the following commands, each one separately and pleas post the output and wrap up the text with CODE TAGS [ ] and [/] OR highlight the text and click "#".

```
sudo fdisk -l

```

then

```
df -h
```

Thank you!

---

### Post by dixcuxx on 2011-07-28
> **amjjawad said:**
> Hi,

From Terminal, please issue the following commands, each one separately and pleas post the output and wrap up the text with CODE TAGS [ ] and [/] OR highlight the text and click "#".

```
sudo fdisk -l

```

then

```
df -h
```

Thank you!

My current biggest problem is at #8, which my D: cannot even use now after try to resize NTFS with Gparted.

---

### Post by amjjawad on 2011-07-28
> **dixcuxx said:**
> My current biggest problem is at #8, which my D: cannot even use now after try to resize NTFS with Gparted.

Well my friend, I don't know how can we help if you are refusing to post the result of each command that we all are suggesting here.

You tell me which way you want us to help and we'll try our best :)

---

### Post by dixcuxx on 2011-07-28
> **amjjawad said:**
> Well my friend, I don't know how can we help if you are refusing to post the result of each command that we all are suggesting here.

You tell me which way you want us to help and we'll try our best :)

I try to reinstall Ubuntu, and I run the ubuntu live CD and click the "install now" icon. It just even erase my d: and just left my c: with windows in it. 

So now I just try to forget c: and d:, then  resore c: with the ghost I had made with windows in it, then using windows software to get out some space from d:, and install ubuntu.

---

### Post by amjjawad on 2011-07-28
> **dixcuxx said:**
> I try to reinstall Ubuntu, and I run the ubuntu live CD and click the "install now" icon. It just even erase my d: and just left my c: with windows in it. 

So now I just try to forget c: and d:, then  resore c: with the ghost I had made with windows in it, then using windows software to get out some space from d:, and install ubuntu.

I did not understand anything. What are you trying to achieve here?

---

### Post by dixcuxx on 2011-07-29
Finally I buy a new harddisk and use the old one for backup photos.

---

### Post by jerrrys on 2011-07-29
you have a unique way of solving a problem.  in tool tips mark as solved please

---


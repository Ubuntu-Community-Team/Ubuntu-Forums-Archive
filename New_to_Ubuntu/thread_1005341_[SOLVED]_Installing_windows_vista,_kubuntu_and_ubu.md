---
title: "[SOLVED] Installing windows vista, kubuntu and ubuntu in your system"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by halovivek on 2008-12-08
Installing windows vista, kubuntu and ubuntu in your system

hi
i have installed windows vista, kubuntu and ubuntu in my system.
i hope this will help for you also.

below i have given my system configuration. and i will give you steps how i did it. any comments and suggestions welcome
Processor :- AMD Turion RM70 64 bit
Memory:- 4 GB (2x2) RAM DDR2 667 MHz
Hard Drive:- 320GB
Graphics Card :- ATI HD3200
video card:-  HDMI, VGA
Screen :- 15.4  WXGA
Sound card :- HD Audio
Optical drive:-  DVD +-RW DL
PC-card-express-Mini No / Yes / Yes
Wlan-Network-Bluetoo 11g/10-1000/No
USB-Firewire-Modem 4/No/No
web cam:- Built in- crystal clear
Operating system:-  Vista ultimate 64 bit, ubuntu 8.10 and kubuntu 8.10
Weight:-  2,9 kg ( too Heavy)

about Hard disk:-
C: drive for windows vista - 80 GB
d:- 40 GB
e:- 40 GB
f:- 40 GB
g:- DVD drive
f:- 40 GB
then remaining 80 GB is there -- 10 GB for swap and 70 GB for ubuntu.

1.first i have installed windows vista in c: drive by general and leaving the others space .
2. Then i have downloaded the kubuntu 8.10 and i stored in the hard disk.
3. i mounted the image using Magic ISO . with the help option of auto run. i have installed the kubuntu in F: drive.
4. I reboot the system and i configured the Kubuntu for internet and other purpose.
5. I thought of installing Ubuntu in my system. i tried to install from windows but it did not work.
6. So i burn the image in the Disk and i have reboot the system and i started the ubuntu CD.
7. I selected the manual install and i went to the un used partition and i done partition for 10GB for SWAP.
8. Then i selected the another un-used partition and i selected as ext3 as well as root. (" /")
9. I have followed the steps and I installed the ubuntu.
10. I reboot the system and first i went to Ubuntu from main screen and i configured for the internet and other things.
11. Then from ubuntu i reboot by using the grub selection i selected the another operating system as windows.
12. Once again i got the grub loader and i selected the windows to work.
13. Once again i reboot the system i went to windows os as in Gurb selection. I got one more Gurb window i selected the Kubuntu and i am working on it.
14. Please try and tell me. I am done this for my system and working fine.
15. please give any feedback on this.):P
16 Did i did a good one or bad?:confused:

:lolflag::guitar:

---

### Post by carml on 2008-12-08
Hi me too I installed both Vista and Ubuntu on the same PC.
I wonder why you did installed both Ubuntu (with GNOME?) and Kubuntu?
If you want to try others OS,you can install a software like Virtualbox,so you can install others OS without reformatting your hard disk,because this way you install the OS on a virtual machine,and all changes don't afflict the whole PC.:p

---

### Post by halovivek on 2008-12-08
> **carml said:**
> Hi me too I installed both Vista and Ubuntu on the same PC.
I wonder why you did installed both Ubuntu (with GNOME?) and Kubuntu?
If you want to try others OS,you can install a software like Virtualbox,so you can install others OS without reformatting your hard disk,because this way you install the OS on a virtual machine,and all changes don't afflict the whole PC.:p

All the operating system is working fine for me. no problem with mine. ):P

---

### Post by carml on 2008-12-08
No problem for me too,mine was only a suggestion,because Ubuntu and Kubuntu act in the same way,apart from the GUI( GNOME or KDE),it was to answer your last question,basing on my (little) )experience.   ):P

---

### Post by tarps87 on 2008-12-08
halovivek, if you wanted to from Ubuntu you could type
```
sudo apt-get install kubuntu-desktop
```
or from Kubuntu
```
sudo apt-get install ubuntu-desktop
```
To install the other desktop environment.
This would mean you don't need to install the same program on your Kubuntu and Ubuntu partitions.
Although there is nothing wrong with the way you have do it, it's just down to personal preference.
The general rule for a swap partition is at least 1 1/2 time the size of your RAM, ideally twice the size. You can probably shrink the size of your swap partition if you need more space later. Also the drive letters c:,d:,etc are part of the windows naming convention, this is different in Ubuntu:
sda1,sda2,etc for partitions on a drive and sda,sdb,etc for different drives. This maybe of use to you in the future.
If you are going to use multiple Linux distros you may what to look look at having a separate /home partition which is linked to all you Linux distros.
These are just things you can do that may improve you system, but there nothing I can see that is wrong/bad with your system.

---

### Post by halovivek on 2008-12-08
> **tarps87 said:**
> halovivek, if you wanted to from Ubuntu you could type
```
sudo apt-get install kubuntu-desktop
```
or from Kubuntu
```
sudo apt-get install ubuntu-desktop
```
To install the other desktop environment.
This would mean you don't need to install the same program on your Kubuntu and Ubuntu partitions.
Although there is nothing wrong with the way you have do it, it's just down to personal preference.
The general rule for a swap partition is at least 1 1/2 time the size of your RAM, ideally twice the size. You can probably shrink the size of your swap partition if you need more space later. Also the drive letters c:,d:,etc are part of the windows naming convention, this is different in Ubuntu:
sda1,sda2,etc for partitions on a drive and sda,sdb,etc for different drives. This maybe of use to you in the future.
If you are going to use multiple Linux distros you may what to look look at having a separate /home partition which is linked to all you Linux distros.
These are just things you can do that may improve you system, but there nothing I can see that is wrong/bad with your system.

i dont want to have two desktop in same base. thats why i am trying in different. ):P

---

### Post by carml on 2008-12-08
@ tarps87
 Thanks for the info.For the swap partition you mean I have to multiply my RAM for 1,5?That's right? I have the doubt that this way I reserve too much space for the swap...

---

### Post by halovivek on 2008-12-08
> **carml said:**
> @ tarps87
 Thanks for the info.For the swap partition you mean I have to multiply my RAM for 1,5?That's right?

yes i have 4GB so i multiplied by 1.5 and got 10GB so i have done and working fine.

---

### Post by carml on 2008-12-08
@ halovivek
When I installed Ubuntu,I left the installer choose the dimension of the partion.Consider that my notebook carries a RAM of 2 GB,and under Ubuntu the swap area is of 266,67 MB,and it works fine...:p

---

### Post by linux_tech on 2008-12-08
If you have low mwmory, then you should set up a swap file.  I like to use 2 x the memory in this case .  So if you have 256 mb RAM, then you should have a swap file of 512MB.  If you have more memory, then swap becomes less 
of an issue.

---

### Post by carml on 2008-12-08
@ linux_tech
It is preferable to leave the amount of swap,than to reduce it,I suppose.Correct me if I'm wrong.

---

### Post by halovivek on 2008-12-08
> **linux_tech said:**
> If you have low mwmory, then you should set up a swap file.  I like to use 2 x the memory in this case .  So if you have 256 mb RAM, then you should have a swap file of 512MB.  If you have more memory, then swap becomes less 
of an issue.

so it is waste for me to use swap of 10GB? still i use it. Is there any program that tells usage of the swap?

---

### Post by carml on 2008-12-08
In my humble opinion,and my experience from Windows it isn't necessary too much of swap memory in a fast and well equiped system.
If you want,try to change the amount of swap memory,if you don't encounter system errors,live the changes active,otherwise reset the swap to its original dimension.
N.B. the changes over the partitions cannot be made while the system is in use.

---

### Post by carml on 2008-12-08
@ halovivek 
You can see the usage of the swap under System->Administration->Sys Info->
Resources:p.

---

### Post by tarps87 on 2008-12-08
> **halovivek said:**
> i dont want to have two desktop in same base. thats why i am trying in different. ):P

Just wanted to make sure you now of the alternatives

> **carml said:**
> @ tarps87
 Thanks for the info.For the swap partition you mean I have to multiply my RAM for 1,5?That's right? I have the doubt that this way I reserve too much space for the swap...

The basis behind this is that is you hibernate any data/bits in RAM need to be saved somewhere, in Linux is the swap partition, in windows it's a file hidden it the windows directory. You can use less if you don't want to hibernate, you can also run without one, but running without a swap has its risks. If you want to learn more have a look a paging

> **halovivek said:**
> yes i have 4GB so i multiplied by 1.5 and got 10GB so i have done and working fine.

You have too much RAM :)

---

### Post by carml on 2008-12-08
@ tarps87 
So for example if one doesn't hibernate can simply reduce the amount of swap,forcing the system to use more RAM instead of the swap(like people suggest on Windows)?:grin:

---

### Post by tarps87 on 2008-12-08
> **carml said:**
> @ tarps87 
So for example if one doesn't hibernate can simply reduce the amount of swap,forcing the system to use more RAM instead of the swap(like people suggest on Windows)?:grin:

Yes, the swap partition/file/thing should only be used if the RAM has been filled at some point. It is usually a good idea to tell new users to use a swap partition larger that the size of the RAM so that their next post is not "help my pc won't hibernate".
If you are prepared to mess around the best way to work it out is trial and error :)

---

### Post by halovivek on 2008-12-19
Thanks for reply to all.

---


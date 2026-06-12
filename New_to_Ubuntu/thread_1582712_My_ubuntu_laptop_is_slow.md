---
title: "My ubuntu laptop is slow"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by rak111esh on 2010-09-26
Hey,
I have a ubuntu 10.04 LTS Lucid Lynx installed recently on my HP-dv5 1106ax Laptop.
In contrast to my expectations this Ubuntu is quiet slow. The boot time is nice but the system as such is slow and i cant even play a mp3 file without that struckings and its impossible to play .mkv files.

My system configurations are posted below:-
AMD Turion X2 RM70 2 GHZ
3 GB DDR2 Ram
ATI Radeon HD 3450 Graphics 512 MB

---

### Post by dirghrabadia on 2010-09-26
It seems like you have a pretty decent configuration to run 10.04. Try running memtest 86+ on boot to see if there are any issues with RAM.

---

### Post by rak111esh on 2010-09-26
Adding up some stuff

My memory is clean
But i have no swap Partition. First i used a dual boot but then i went Ubuntu only for some academic reasons.
My ubuntu is in 10GB but i store all my files in two other partitions(250gb hdd)

---

### Post by lbrty on 2010-09-26
It sounds like you installed Ubuntu inside of Windows using Wubi (Windows-based UBuntu Installer). This would contribute to why your system is slow. Try dual booting Ubuntu instead of running Ubuntu inside of Windows. 

[https://help.ubuntu.com/community/DualBoot](https://help.ubuntu.com/community/DualBoot)

---

### Post by rak111esh on 2010-09-26
I dont have windows any more and my ubuntu installation is wubi right but thats only because i installed it from pendrive(well i did it the right way tbh)

also as a sidenote i would also like to mention that my system as such isnt slow this can be shown by 100+fps in a game called UrbanTerror i play.
But somehow i feel like ubuntu (especially while watching movies,surfing etc) isnt taking full power from my system

---

### Post by dirghrabadia on 2010-09-26
Go to System->Administration->System Monitor. Check the Processes tab to see if any of the applications is having an abnormal memory requirement.

---

### Post by lbrty on 2010-09-26
Do you boot off the USB flash device every time you boot into Ubuntu or did you actually install Ubuntu on the hard drive?

> **rak111esh said:**
> But somehow i feel like ubuntu (especially while watching movies,surfing etc) isnt taking full power from my system

What makes you come to that conclusion?

---

### Post by rak111esh on 2010-09-26
> **lbrty said:**
> Do you boot off the USB flash device every time you boot into Ubuntu or did you actually install Ubuntu on the hard drive?



What makes you come to that conclusion?

1)I installed Ubuntu on my hdd.
2)The fact that a 3d game plays without any fps drop or lag. Where as a movie(.mkv) has considerable fps drop. I use vlc btw

@dirghrabadia
No none exceptionally high but noticed vlc takes 60-70 % cpu.

---

### Post by lbrty on 2010-09-27
It may have something to do with your CPU or possibly the .mkv file format or the file itself. Have you tried a different video file or a different type of video format (e.g. .avi, etc)?

Scroll to the bottom of the page. 
[http://cpubenchmark.net/cpu_lookup.php?cpu=AMD+Turion+X2+Dual+Core+Mobile+RM-70](http://cpubenchmark.net/cpu_lookup.php?cpu=AMD+Turion+X2+Dual+Core+Mobile+RM-70)

I have 4GB of DDR3 SO-DIMM RAM, Intel Core 2 Duo T6600 (+531 point difference), with integrated Intel Graphics and do not have the FPS issue. When I do play a video file (with VLC) the file format is .avi

[http://www.cpubenchmark.net/cpu_lookup.php?cpu=Intel+Core2+Duo+T6600+%40+2.20GHz]("http://www.cpubenchmark.net/cpu_lookup.php?cpu=Intel+Core2+Duo+T6600+%40+2.20GHz")

---

### Post by mastablasta on 2010-09-27
> **rak111esh said:**
> I dont have windows any more and **my ubuntu installation is wubi right** but thats only because i installed it from pendrive(well i did it the right way tbh)
 

 
wait are you saying you are/were using Wubi to install?
 
if so then no wonder it runs slow. Wubi is running ubuntu inside windows in a sort of virtualisation (well it's all stuck in one file).
 
 
you also said: 
> But i have no swap Partition. 
 
This (if true) could be problematic or the thing causing your problems.
 
another thing to look at are graphics drivers. if they are poor or inapropriate they can cause issues - movies are connected with graphics card.

---

### Post by rak111esh on 2010-09-27
> **mastablasta said:**
> wait are you saying you are/were using Wubi to install?
 
if so then no wonder it runs slow. Wubi is running ubuntu inside windows in a sort of virtualisation (well it's all stuck in one file).
 webi.exe is one file i saw on pendrive before installing ubuntu. But i know i installed it properly so thats not an issue.

Yes i dont have any swap file or partition. Does this affect the system so much? I am attatching a screen shot plz take a look at it.
I already have 4 partitions so i cant create another one it(Disk Utility) says

---

### Post by rak111esh on 2010-09-27
When i changed the visual effects to none everything seems to work fine.

So i guess thats too much for my system to handle?

---


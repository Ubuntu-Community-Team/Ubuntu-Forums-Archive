---
title: "Install Problems"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by hdtvchris on 2010-03-23
hi
i install ubuntu but the system does not start
not even from the windows HD

i had windows xp installed (IDE hard disk) and i install Ubuntu 9.10 on my other HD (SATA)
but the system does not start

when i try to boot from the win xp HD i see black screen with a GRUB _ text in the top and there stops
if i try to boot from ubuntu harddisk i see GRUB menu, i try the grub recovery and packages recovery
and then boot from normal install (i get a black screen and nothing happens) 
if i try to boot at  recovery mode, boots at command line mode and from there i have no idea what to do.
eg how to start the graphics shell from command line or how to fix grub or anything else may be broken

only the live cd works

some help please


thanks

---

### Post by Mykk on 2010-03-23
Ok, just a few questions.

1) Which version of Ubuntu are you using?

2) Just to clarify you have Ubuntu and Windows on two different hard drives?

3) What system are you using? I'm assuming a desktop so whats the make and model + spec?


I once came across a similar problem with a black screen when installing Ubuntu 9.10 on a Dell Inspiron laptop. Funnily enough if I just left the laptop for 15 mins or so on the black screen it would eventually reach the log on screen. I know this isn't exactly ideal as a long term solution but if you can get in the GUI this way we can take steps from there to solve it.

Let me know...

...and if all else fails maybe try an install from the alternate cd.

M

---

### Post by hdtvchris on 2010-03-23
1) ubuntu 9.10
2) yes 2 different hard drives (win xp at IDE, ubuntu at SATA)
3) desktop, P4 3.00Ghz, 2Gb Ram, Asus p4p 800se

i read the forum and i try, from grub menu to delete the "splash quiet" and then boot
and finaly i can boot ubuntu and win xp but with problems

now some times the ubuntu boot fine and sometimes i see the black screen (when this happen i have to delete the "splash quiet" again

other times the bios change the bootable hard disk (from the one with ubuntu to the one with win xp and the system cant boot)

other times when i start the system i get an error about the cpu fan

is there any way for remove the grub from the win xp hard disk ? (if i want to boot with windows i preffer to change the bootable hard disk from the bios)

---

### Post by Mykk on 2010-03-23
Funny you should mention an Asus Board, as a friend of mine had a similar setup and encountered dual boot problems. In the end we managed to solve the problem by switching round the sata connections for the two hard drives. I know you are using one sata and one ide, but maybe changing the sata port and/or setting the IDE hard drive to slave (dont forget to do the jumper pin too) might have some effect on the situation. Unlikely but still worth a shot.

As for the fan error, is the fan actually working correctly? Maybe open up your computer and take a look (if you havent already). Check if the wire from the fan to the mobo is connected properly. If this STILL doesn't solve that issue you can always disable warning halts on boot from the bios. I did this with my watercooling setup as there was no wire from the waterblock to the mobo.

---

### Post by andrewthomas on 2010-03-23
> **hdtvchris said:**
> 1)

**is there any way for remove the grub from the win xp hard disk** ? (if i want to boot with windows i preffer to change the bootable hard disk from the bios)

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Follow the instructions in this post and that should restore your XP mbr

---

### Post by hdtvchris on 2010-03-23
> **Mykk said:**
> Funny you should mention an Asus Board, as a friend of mine had a similar setup and encountered dual boot problems. In the end we managed to solve the problem by switching round the sata connections for the two hard drives. I know you are using one sata and one ide, but maybe changing the sata port and/or setting the IDE hard drive to slave (dont forget to do the jumper pin too) might have some effect on the situation. Unlikely but still worth a shot.

As for the fan error, is the fan actually working correctly? Maybe open up your computer and take a look (if you havent already). Check if the wire from the fan to the mobo is connected properly. If this STILL doesn't solve that issue you can always disable warning halts on boot from the bios. I did this with my watercooling setup as there was no wire from the waterblock to the mobo.

i try it with the SATA HDD but nothing change, i will try the IDE too

the fan working, before ubuntu i never got error like that

also i find one more problem, after installing ubuntu when i boot to windows it change the computer time settings (it goes 2 hours back)
this happen first time when i try the ubuntu from the live cd and still happen now who i install on the HDD


@andrewthomas thank you for the info

---

### Post by hdtvchris on 2010-03-24
hi again

is there any way for perm delete the "splash quiet" ?
now i do it manualy from the grub menu or the system does not boot

also after the system run for some mins 20-30 mins the graphics go slow
do i have to install a graphics driver ? and how can i see what drivers the ubuntu have install ?

i have this graphics card RV350 AR [Radeon 9600]

```
[    3.080660] [drm] Initialized drm 1.1.0 20060810
[    3.110645] [drm] radeon default to kernel modesetting DISABLED.
[    3.111535] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[   18.117467] [drm] Setting GART location based on new memory map
[   18.117475] [drm] Loading R300 Microcode
[   18.117511] [drm] Num pipes: 1
[   18.117518] [drm] writeback test succeeded in 1 usecs
[  627.748148] [drm] Num pipes: 1
[  630.416983] [drm] Loading R300 Microcode
[  630.417019] [drm] Num pipes: 1

```

---

### Post by Mykk on 2010-03-24
You seem to have no end of problems with this machine haha :)

One thing you could try is unplugging one of the hard drives, for example, just have the drive with ubuntu plugged in. See if that makes any difference.


*is there any way for perm delete the "splash quiet" ?*

Im not too sure about this one - i'll do a bit of research but in the mean time maybe some one here will contribute to this.


As for the graphics, have you set up your propriety drivers?

---

### Post by andrewthomas on 2010-03-24
> **hdtvchris said:**
> 

is there any way for perm delete the "splash quiet" ?

```
gksudo gedit /etc/default/grub
```and remove quiet splash from both the following lines
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---


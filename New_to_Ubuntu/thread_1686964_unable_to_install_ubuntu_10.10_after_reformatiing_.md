---
title: "unable to install ubuntu 10.10 after reformatiing pc"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by cloube on 2011-02-13
i have problem now.. last few days ive done some stupid things by changing 

gedit etc/passwd  and change the top root name thinking that it will rename my root. but after that i can't login to the system

[http://ubuntuforums.org/showthread.php?t=1686298](http://ubuntuforums.org/showthread.php?t=1686298)

since my last thread dont get any reply from the expert, i just reformat everything in my laptop. i install back windows xp but after that i still can't reinstall  ubuntu .

when i use the ubuntu CD, the terminal will open and below error appear.

General error mounting filesystems
a mantenance shell will now be started
Control -D will terminate this shell and reboot the system
root@ubuntu:~#


i dont know what to do now. currently my hard disk all are occupied by windows XP.. please help me. im a newbie here i've spent the weekends trying to use ubuntu back over my stupid mistake....  :(:(

---

### Post by linuxsyst on 2011-02-13
I said you you changed the root password and now reinstall the system to older linux and then back to 10.10

---

### Post by linuxsyst on 2011-02-13
OMG where did you get the etc/passwd I don't have it
But try to install the earlear version of linux and the new one

---

### Post by cloube on 2011-02-13
> **linuxsyst said:**
> I said you you changed the root password and now reinstall the system to older linux and then back to 10.10


i've tried changing the passwd on root but still unable to login..
after i formatted the PC, i delete the ubuntu partition and format everything including my windows XP..now i only run on 1 partition on windows XP. 

for other version of ubuntu, i dont have a disc burner, usb boot in the bios selection and i just get the live ubuntu 10.10 CD by post...

i think it have to do something with the kernel but i dont know how to check it...and need guidance...

---

### Post by cloube on 2011-02-13
by using the live CD i search the disc for file defects. upon finishing, on the screen shows 1 file are effected...but im not sure which file are effected.i need help in this too..

then i try reboot the system and select "try ubuntu without installing" . the same error pop out....


please help........

---

### Post by linuxsyst on 2011-02-13
[root@pc1  disk]#  gedit /etc/passwd

All groups stored in this file
[root@pc1  disk]#  edit /etc/shadow
 
User password stored in this file
[root@pc1  disk]#  gedit  /etc/group

---

### Post by linuxsyst on 2011-02-13
```
To Change Computer Name:

    sudo gedit /etc/hostname
    sudo gedit /etc/hosts

    Change the name of your system in both and reboot.


To Change User Login Name:

    sudo gedit /etc/passwd
    sudo gedit /etc/shadow
    sudo gedit /etc/group
    sudo gedit /etc/gshadow
```

---

### Post by Linyx on 2011-02-13
I Have found Similar thread > [http://www.uluga.ubuntuforums.org/showthread.php?t=1333302&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1333302&page=2) 

& it was Solved by the Given Instruction

Try these Commands is shell:-

```
mount -n -o remount,rw /
aptitude --configure -a
xinit
```

---

### Post by linuxsyst on 2011-02-13
ok i get what > sudo gedit /etc/passwd
what last you changed it to?
I get what the problem is.

---

### Post by linuxsyst on 2011-02-13
into user login enter the name you changed it to > sudo gedit /etc/passwd
and the password normal if you didn't write > sudo passwd

---

### Post by cloube on 2011-02-14
> **Linyx said:**
> I Have found Similar thread > [http://www.uluga.ubuntuforums.org/showthread.php?t=1333302&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1333302&page=2) 

& it was Solved by the Given Instruction

Try these Commands is shell:-

```
mount -n -o remount,rw /
aptitude --configure -a
xinit
```

sorry for the late reply i can't login the forum today.

for the command given. i've tried to run it but unable to execute the "aptitude --configure -a" since currently i run on a live cd and my laptop can't connect to the internet thus i can't get the  program  
"apt-get install aptitude" .

ok but when i  put "mount" command in the system i get below information

root@ubuntu # mount
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=628260k,nr_imodes=157065,mode=755)
none on /dev/pts type devpts 
(rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
fusect1 on /sys/fs/fuse/connections type fusect1 (rw,relatime)
/dev/sr0 on /cdrom type iso 9660 (ro,noatime)
/dev/loop0 on/rofs/type squashfs (ro,noatime)
tmpfs on /cow/type tmpfs (rw,noatime,mode=755)
aufs on /type aufs (rw,relatime,si=d8c8a88b)


and when i check fstab information i get below information
aufs /aufs/rw 0 0
tmpfs /tmp tmpfs nosuid, nodev 00

other than that, ive tried editing the fstab
by adding 

aufs /aufs/rw 0 0
tmpfs /tmp tmpfs nosuid, nodev 00
/dev/sda5 /mnt vfat


and try mount it
mount -t vfat /dev/sda5 /mnt --rw

but after reboot the configuration seem lost i guess because it run from the CD. ive try input "init s" again after reconfigure everything into the system but there  pop out some error like

tty1 respawning or something like that...

please help..

---

### Post by cloube on 2011-02-14
> **linuxsyst said:**
> into user login enter the name you changed it to 
and the password normal if you didn't write



in the first place i change the top
root:x:0:0:root:/root:root/bin/bash
to
abcdefghig:x:0:0:root:/root:root/bin/bash

after ive tried many things ive format all my drive including windows xp ...that bring to where im now..

---

### Post by cloube on 2011-02-14
anyone can help?
it seems that whenever i boot from the live cd and the error "general error filesystem " occur and try to mount everything then reboot, all the configuration is lost. i read about grub but my laptop request me to  run "apt-get install grub" command. which now i can't do as i can't connect to the internet..using it. so for now whatever i do the system doesn't take effect after rebooting. i try to reboot without the ubuntu CD but then it will straight away go to windows xp .

so what else i can do to solve this im running out of idea.....

---

### Post by presence1960 on 2011-02-14
> **cloube said:**
> anyone can help?
it seems that whenever i boot from the live cd and the error "general error filesystem " occur and try to mount everything then reboot, all the configuration is lost. i read about grub but my laptop request me to  run "apt-get install grub" command. which now i can't do as i can't connect to the internet..using it. so for now whatever i do the system doesn't take effect after rebooting. i try to reboot without the ubuntu CD but then it will straight away go to windows xp .

so what else i can do to solve this im running out of idea.....

You said earlier when you checked the live CD/USB for errors you had one file that was affected. That means your Live CD/USB is no good. You must create another one.

---

### Post by cloube on 2011-02-14
> **presence1960 said:**
> You said earlier when you checked the live CD/USB for errors you had one file that was affected. That means your Live CD/USB is no good. You must create another one.


the cd i got from ubuntu team before..i will try make new CD and will update with you guys.....

---

### Post by cloube on 2011-02-16
> **presence1960 said:**
> You said earlier when you checked the live CD/USB for errors you had one file that was affected. That means your Live CD/USB is no good. You must create another one.


After twice reformating my pc, 8 times burn cd at 4x speed,new DVD head cleaner,i manage to install back ubuntu and currently im running on it....

The lesson i learn from this problem is "Don't believe the cd even when its ok in the first installation"  need to check the defects on the cd and re burn the cd 

thanks Presencea1960  and others for the guide..:D:D

---


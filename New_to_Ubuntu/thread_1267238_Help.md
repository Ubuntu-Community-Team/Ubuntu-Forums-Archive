---
title: "Help"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by stuffnsuch on 2009-09-15
Hi Yaall;
I just downloaded and installed ubuntu linux and all seemed to go well, but now nothing seems to work.
Ex; Firefox won't import or keep bookmarks and I cant even open the email program.
What have I done????
Dan:(

---

### Post by LowSky on 2009-09-15
welcome to the forums Dan.

Can ou tell me how you installed Ubuntu, and are you actually using version 7.04 or are you using a newer version.

---

### Post by stuffnsuch on 2009-09-15
I downloaded from the ubuntu site to a CD and installed by the directions (I hope).
It is version 9.04 as far as I can tell.
Thanks for the response.
Dan

---

### Post by stuffnsuch on 2009-09-16
[FONT=Arial, sans-serif]:confused: I think I will start this thread over.[/FONT]
 [FONT=Arial, sans-serif]I have been playing with computers for about 30 years, my first one was a T I 99 with 64 K of ram, (WOW). I suppose I was  geek back then, when we wrote our own programs in dos. But now I'm just a confused old fart.[/FONT]
 [FONT=Arial, sans-serif]I have upgraded a bit since then. I recently moved to an Acer E620 with 3 GB of ram running windows (yuk) vista with sp 2. 136 Gb hard drive with 72 free.[/FONT]
 [FONT=Arial, sans-serif]I have been threatening to switch to Lenix for years and after reading how easy it is to switch in 'PC World' I downloaded Ubuntu 9.04 and installed it in the dual boot method.[/FONT]
 [FONT=Arial, sans-serif]After following all the instructions (I hope) the system started and looks beautiful. BUT, when I tried to import my bookmarks from my windows Firefox they get lost every time I restart it, and it wont even bookmark any page.[/FONT]
 [FONT=Arial, sans-serif]Also a pop up instructed me to download many upgrades and when I tried, it said “not enough memory” I have defragged my drive and looked at re-partitioning and just get more and more confused. Am I just too old and outdated to install this operating system?[/FONT]
 [FONT=Arial, sans-serif]Please be gentle with me,,,,LOL.[/FONT]
 [FONT=Arial, sans-serif]Thanks; Dan.[/FONT]

---

### Post by bodyharvester on 2009-09-16
> **stuffnsuch said:**
> [FONT=Arial, sans-serif]“not enough memory”[/FONT]

hi

is this the memory in the ubuntu partition? how much space did you give ubuntu to install itself in? if you didnt give ubuntu enough space to breathe youll need to re-install it and give it more space.

can you successfully update the system?

---

### Post by stuffnsuch on 2009-09-16
I have so far not been able to define which is the ubuntu partition.
I'm not sure how much memory was allocated as I used the default settings,,duh.
I haven't tried to update or re install,, not sure how,,(or maybe afraid??)
Thanks for the reply;
still confused Dan.

---

### Post by bodyharvester on 2009-09-16
to update:

sudo apt-get update
sudo apt-get upgrade

my screens show me in the terminal, you can see one of the commands in there and the results. the third screen "df -h.png" shows another command i want you to run

also type in:

df -h

and post the output, i dont know if it shows both partitions, my netbook only has jaunty

EDIT: sorry an email was on the desktop, gonna edit it out of images and repost them

EDIT 2: email address removed, images reposted

---

### Post by LewRockwell on 2009-09-16
> **stuffnsuch said:**
> [FONT=Arial, sans-serif]:confused: I think I will start this thread over.[/FONT]
 [FONT=Arial, sans-serif]I have been playing with computers for about 30 years, my first one was a T I 99 with 64 K of ram, (WOW). I suppose I was  geek back then, when we wrote our own programs in dos. But now I'm just a confused old fart.[/FONT]
 [FONT=Arial, sans-serif]I have upgraded a bit since then. I recently moved to an Acer E620 with 3 GB of ram running windows (yuk) vista with sp 2. 136 Gb hard drive with 72 free.[/FONT]
 [FONT=Arial, sans-serif]I have been threatening to switch to Lenix for years and after reading how easy it is to switch in 'PC World' I downloaded Ubuntu 9.04 and installed it in the dual boot method.[/FONT]
 [FONT=Arial, sans-serif]After following all the instructions (I hope) the system started and looks beautiful. BUT, when I tried to import my bookmarks from my windows Firefox they get lost every time I restart it, and it wont even bookmark any page.[/FONT]
 [FONT=Arial, sans-serif]Also a pop up instructed me to download many upgrades and when I tried, it said “not enough memory” I have defragged my drive and looked at re-partitioning and just get more and more confused. Am I just too old and outdated to install this operating system?[/FONT]
 [FONT=Arial, sans-serif]Please be gentle with me,,,,LOL.[/FONT]
 [FONT=Arial, sans-serif]Thanks; Dan.[/FONT]

did you use vista to create your new partitions?

here, we ask this question because it is quite possible that you just let the installer hack at your hard drive(which is not recommended)

.

---

### Post by bodyharvester on 2009-09-16
> **LewRockwell said:**
> did you use vista to create your new partitions?

here, we ask this question because it is quite possible that you just let the installer hack at your hard drive(which is not recommended)

.

no, i think he used the method on the cd that is offered.

---

### Post by stuffnsuch on 2009-09-16
Sorry for the delay, but I was working in YUK windows and had to switch.
Dumb question, but how do you type in a command????

---

### Post by ubongo2008 on 2009-09-16
well it is normal that there are many updates which can be installed after an cd-only install. 
if you want to know which partition is linux and which is windows just type 

sudo fdisk -l

maybe you haven't any space left on your ubuntu partition so that the updates can't be saved to your pc.  
well as [bodyharvester]("http://ubuntuforums.org/member.php?u=869539") mentioned you may just type 

df -h 

to see how many space is left on that partition ( "/" is what is interesting for you)


if you want to clear you firefox settings and have them recreated then type 

rm -r $HOME/.mozilla

concerning your command question:

press ALT+F2 then type gnome-terminal

---

### Post by bodyharvester on 2009-09-16
i cant believe i forgot about the "fdisk -l" command#-o

---

### Post by stuffnsuch on 2009-09-16
OK,,, now I have the command page up but any I type in returns 
bash: df-h.png: command not found
I just found the dick usage manager and it says I have 76 gb available

---

### Post by muteXe on 2009-09-16
why .png at the end of the command??

---

### Post by bodyharvester on 2009-09-16
> **stuffnsuch said:**
> OK,,, now I have the command page up but any I type in returns 
bash: df-h.png: command not found
I just found the dick usage manager and it says I have 76 gb available

when i said "df -h.png" i was refering to the image which is a .png type file, sorry for the confusion

the command is

df -h

there is a single space between "f" and "-h", just copy and paste the command on the above line ;)

---

### Post by stuffnsuch on 2009-09-16
OK I finally got the fdisk to work and this is what I got,,,,,,,,,,
I also can t get the quickreply to work on here???

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ee807df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10490413+  27  Unknown
/dev/sda2   *        1307       19132   143180632    7  HPFS/NTFS
/dev/sda3           19133       19457     2610562+   5  Extended
/dev/sda5           19133       19435     2433816   83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris
dan@dan-laptop:~$

---

### Post by ubongo2008 on 2009-09-16
> **stuffnsuch said:**
> OK,,, now I have the command page up but any I type in returns 
bash: df-h.png: command not found
I just found the dick usage manager and it says I have 76 gb available


just use ```
df -h 
``` hehe what is a  > dick usage manager maybe something for an adult-only thread? 

well 76 gb is plenty of space 

try again 

> sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get clean^^ that should update all installed packages

 edit: if that fails please post the output here
you  can also run those commands step by step  like 

> 
sudo apt-get update
 sudo apt-get dist-upgrade
sudo apt-get clean


well as you can see "/dev/sda5" is your linux partition
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ee807df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10490413+  27  Unknown
/dev/sda2   *        1307       19132   143180632    7  HPFS/NTFS
/dev/sda3           19133       19457     2610562+   5  Extended
/dev/sda5           19133       19435     2433816   83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris


if you want to know where those patitions are mounted you can type 
```
mount 
```well my mount output looks a bit complicated but i'll post it anyway


> 
/dev/sda1 on / type ext3 (rw,noatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /media/data type ext3 (rw,noatime)
/bin on /.physical_disk/bin type none (rw,bind)
/.ramdom_access_memory/bin on /bin type none (rw,bind,noatime)
/sbin on /.physical_disk/sbin type none (rw,bind)
/.ramdom_access_memory/sbin on /sbin type none (rw,bind,noatime)
/etc on /.physical_disk/etc type none (rw,bind)
/.ramdom_access_memory/etc on /etc type none (rw,bind,noatime)
/lib on /.physical_disk/lib type none (rw,bind)
/.ramdom_access_memory/lib on /lib type none (rw,bind,noatime)
/lib32 on /.physical_disk/lib32 type none (rw,bind)
/.ramdom_access_memory/lib32 on /lib32 type none (rw,bind,noatime)
/var on /.physical_disk/var type none (rw,bind)
/.ramdom_access_memory/var on /var type none (rw,bind,noatime)
/usr on /.physical_disk/usr/originalfs type none (rw,bind,noatime)
none on /.ramdom_access_memory/usr type tmpfs (rw,size=1500m)
/dev/loop0 on /.ramdom_access_memory/usr/aufs/ro type squashfs (ro,noatime)
aufs on /usr type aufs (rw,noatime,br=/.ramdom_access_memory/usr/aufs/rw:/.ramdom_access_memory/usr/aufs/ro=ro)
/home/trg on /.physical_disk/home/trg/originalfs type none (rw,bind,noatime)
none on /.ramdom_access_memory/home/trg type tmpfs (rw,size=1500m)
/dev/loop1 on /.ramdom_access_memory/home/trg/aufs/ro type squashfs (ro,noatime)
aufs on /home/trg type aufs (rw,noatime,br=/.ramdom_access_memory/home/trg/aufs/rw:/.ramdom_access_memory/home/trg/aufs/ro=ro)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000)
for example the line  "/dev/sda1 on / type ext3 (rw,noatime,errors=remount-ro)"
tells you that my first patition is an ext3 and that it is mounted to "/"

---

### Post by stuffnsuch on 2009-09-16
Cheese,, I gotta read the instructions more carefully,,, duhhhh

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ee807df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10490413+  27  Unknown
/dev/sda2   *        1307       19132   143180632    7  HPFS/NTFS
/dev/sda3           19133       19457     2610562+   5  Extended
/dev/sda5           19133       19435     2433816   83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris
dan@dan-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  104K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  168K  1.4G   1% /dev
tmpfs                 1.4G   84K  1.4G   1% /dev/shm
lrm                   1.4G  2.4M  1.4G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/sda2             137G   65G   72G  48% /media/OS
dan@dan-laptop:~$

---

### Post by stuffnsuch on 2009-09-16
OOps old fingers just dont always work right,,, glad you have a sense of humour,,,LOL
still wont update, though.

---

### Post by bodyharvester on 2009-09-16
> **stuffnsuch said:**
> OOps old fingers just dont always work right,,, glad you have a sense of humour,,,LOL
still wont update, though.

so it says you dont have enough space to update or something else?

---

### Post by stuffnsuch on 2009-09-16
not enough space

Not enough free disk space

The upgrade needs a total of 412M free space on disk '/'. Please free at least an additional 412M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

---

### Post by ubongo2008 on 2009-09-16
> **stuffnsuch said:**
> Cheese,, I gotta read the instructions more carefully,,, duhhhh

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ee807df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10490413+  27  Unknown
/dev/sda2   *        1307       19132   143180632    7  HPFS/NTFS
/dev/sda3           19133       19457     2610562+   5  Extended
/dev/sda5           19133       19435     2433816   83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris
dan@dan-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  104K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  168K  1.4G   1% /dev
tmpfs                 1.4G   84K  1.4G   1% /dev/shm
lrm                   1.4G  2.4M  1.4G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/sda2             137G   65G   72G  48% /media/OS
dan@dan-laptop:~$


so " /dev/sda5             2.3G  2.3G     0 100% /" tells you that you indeed have no space left on your root partiton

you may boot up an live-cd and use "gparted" to resize it you should give it at least 15 GB because i think you also want to have some extra space for /home or other stuff which you may want to install at a later time

here is a pic of gparted (partition editor)

[IMG]http://t3.gstatic.com/images?q=tbn:weovhDPk66A3KM:http://freewaregenius.com/wp-content/uploads/2006/12/gpartedscreenshot.jpg[/IMG]



EDIT: oh by the way that explains why firefox couldn't save your settings (no space to write to)

---

### Post by mrbiggbrain on 2009-09-16
Note, It can take some time to resize partitions, it took me about 6 hours to resize one of my partitions once. making them smaller is slow, making them bigger is a fast as heck.

also if after resizing if windows dosnt want to boot, or gives unmoutable boot volume blue-screen, run the vista install disk or recovery disk and select to repair your pc, start up a command prompt, and type 

```
chkdsk /r
```

id say theres no way to really do a standard ubuntu 9.04 install without at least 10 gb. Iv done a minimal install with fluxbox in about 800mb, but thats not something that most people would want to attempt.

---

### Post by stuffnsuch on 2009-09-16
That sounds like you have indeed found the problem, thanks, I owe you one, or two, you just have to visit Canada to collect,,,LOL.
One more question,,, not sure about rebooting,, do I use the install disk and where or when do I type the " gparted????

---

### Post by mrbiggbrain on 2009-09-16
> **mrbiggbrain said:**
> Note, It can take some time to resize partitions, it took me about 6 hours to resize one of my partitions once. making them smaller is slow, making them bigger is a fast as heck.

also if after resizing if windows dosnt want to boot, or gives unmoutable boot volume blue-screen, run the vista install disk or recovery disk and select to repair your pc, start up a command prompt, and type 

```
chkdsk /r
```

id say theres no way to really do a standard ubuntu 9.04 install without at least 10 gb. Iv done a minimal install with fluxbox in about 800mb, but thats not something that most people would want to attempt.

EDIT: also, to ensure quick responses and better answers, pick better thread titles. Help might seem like a good title when you know verry little about linux, but it dosnt stand out to people who know things you dont. 

Setting the title to "Cant download updates, or Import firefox info" or "New to linux, Updates wont work" are more likly to bring in those with good info, and less likely to be skipped over by those people, there are dozens of threads a day, and a thread with title "help" is easy to skip over.

---

### Post by bodyharvester on 2009-09-16
> **stuffnsuch said:**
> That sounds like you have indeed found the problem, thanks, I owe you one, or two, you just have to visit Canada to collect,,,LOL.
One more question,,, not sure about rebooting,, do I use the install disk and where or when do I type the " gparted????

gparted is a program, go to SYSTEM > ADMINISTRATION it should be in there, or "partition editor", im not sure how to use them though

---

### Post by ubongo2008 on 2009-09-16
> **stuffnsuch said:**
> That sounds like you have indeed found the problem, thanks, I owe you one, or two, you just have to visit Canada to collect,,,LOL.
One more question,,, not sure about rebooting,, do I use the install disk and where or when do I type the " gparted????

no problem at all ...
well yes you can choose the "try ubuntu without changing ..." menu entry. 
that will boot up an live-environment where you can use gparted ..

---


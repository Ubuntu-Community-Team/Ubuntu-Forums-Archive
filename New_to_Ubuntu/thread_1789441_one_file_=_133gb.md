---
title: "one file = 133gb??"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by matty4203 on 2011-06-23
just ran a disc usage analyser scan thing on ubuntu and one file named [/] came up with 100% usage at 113.4 gb, it is stopping me from downloading anymore files etc because it says i have no hdd space left, i have no idea what to do (yes new to ubuntu linux) help would be greatly appreciated :)

Edit: 
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/loop0               16481     15644         1 100% /
none                      1502         1      1501   1% /dev
none                      1510         1      1509   1% /dev/shm
none                      1510         1      1509   1% /var/run
none                      1510         0      1510   0% /var/lock
/dev/sdb1               229622     51192    178431  23% /host
/dev/sda1               152618     52128    100491  35% /media/12B43B3FB43B249F
/dev/sdc                  7648        63      7586   1% /media/1C50B8E350B8C534

---

### Post by josephmills on 2011-06-23
> **matty4203 said:**
> just ran a disc usage analyser scan thing on ubuntu and one file named [/] came up with 100% usage at 133.4 gb, it is stopping me from downloading anymore files etc because it says i have no hdd space left, i have no idea what to do (yes new to ubuntu linux) help would be greatly appreciated :)

/ is your root kinda like c drive in windoz

---

### Post by matty4203 on 2011-06-23
alright i see, but is it supposed to take up 113.4gb of hd space? :S

---

### Post by linuxman94 on 2011-06-23
Towards the top of the window what does it say for the amount of space available?

---

### Post by matty4203 on 2011-06-23
> **linuxman94 said:**
> Towards the top of the window what does it say for the amount of space available?

it says 280.9GB available with 116gb used

---

### Post by josephmills on 2011-06-23
open your terminal (ctrl+alt+t)and type in```
df -a
``` and paste here thanks

---

### Post by linuxman94 on 2011-06-23
Disk usage analyzer can be a bit tricky.  It shows 100% but it does not actually take up 100% of the drive.  as long as it says you have free space you're fine

---

### Post by matty4203 on 2011-06-23
> **josephmills said:**
> open your terminal (ctrl+alt+t)and type in```
df -a
``` and paste here thanks

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0            16876388  16019188         0 100% /
proc                         0         0         0   -  /proc
none                         0         0         0   -  /sys
fusectl                      0         0         0   -  /sys/fs/fuse/connections
none                         0         0         0   -  /sys/kernel/debug
none                         0         0         0   -  /sys/kernel/security
none                   1537572       728   1536844   1% /dev
none                         0         0         0   -  /dev/pts
none                   1545280       456   1544824   1% /dev/shm
none                   1545280       224   1545056   1% /var/run
none                   1545280         0   1545280   0% /var/lock
/dev/sdb1            235132664  52420096 182712568  23% /host
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon             0         0         0   -  /home/mat/.gvfs
/dev/sda1            156280288  53378444 102901844  35% /media/12B43B3FB43B249F
/dev/sdc               7831548     64408   7767140   1% /media/1C50B8E350B8C534

---

### Post by matty4203 on 2011-06-23
> **linuxman94 said:**
> Disk usage analyzer can be a bit tricky.  It shows 100% but it does not actually take up 100% of the drive.  as long as it says you have free space you're fine

but the thing is, im trying to patch a game thats 7gb and it's telling my i have no space left in my HDD

---

### Post by dFlyer on 2011-06-23
If I understand you correctly your hard drive is full. If that is the case you will need to remove some files. You might want to try this at a command line:

sudo apt-get autoclean

this will remove old deb files that are downloaded when you update your system from the hard drive. Another way to free up some space is to remove old compressed logs with the below command.

sudo rm /var/log/*.gz

Of course the other solution would be to add another drive.

---

### Post by josephmills on 2011-06-23
looks like you are maxed out time to upgrade or get an ex.harddrive

---

### Post by matty4203 on 2011-06-23
> **dFlyer said:**
> If I understand you correctly your hard drive is full. If that is the case you will need to remove some files. You might want to try this at a command line:

sudo apt-get autoclean

this will remove old deb files that are downloaded when you update your system from the hard drive. Another way to free up some space is to remove old compressed logs with the below command.

sudo rm /var/log/*.gz

Of course the other solution would be to add another drive.

got 2 HDD's on here mate, whiped them both before installing ubuntu and it still says i have room left, which is why im so damn confused as to why this has happened!

---

### Post by linuxman94 on 2011-06-23
Please post the result of this command:

```
sudo du -xk --max-depth 1 / | sort -n
```

---

### Post by matty4203 on 2011-06-23
> **linuxman94 said:**
> Please post the result of this command:

```
sudo du -xk --max-depth 1 / | sort -n
```

du: cannot access `/home/mat/.gvfs': Permission denied
0	/dev
0	/proc
0	/sys
4	/cdrom
4	/mnt
4	/selinux
4	/srv
16	/lost+found
28	/host
68	/tmp
72	/media
148	/root
8112	/bin
9104	/sbin
11876	/lib32
13320	/etc
26572	/boot
84200	/opt
196108	/lib
651468	/var
2304008	/usr
12556928	/home
15862048	/

---

### Post by linuxman94 on 2011-06-23
Your home folder is huge.  Try this:

```
sudo du -xk --max-depth 1 /home/* | sort -n
```

---

### Post by matty4203 on 2011-06-23
4	/home/mat/.nautilus
4	/home/mat/Pictures
4	/home/mat/Public
4	/home/mat/Templates
4	/home/mat/.themes
4	/home/mat/Ubuntu One
4	/home/mat/Videos
12	/home/mat/.dbus
12	/home/mat/.mission-control
16	/home/mat/.adobe
20	/home/test
36	/home/mat/.pki
80	/home/mat/.gconfd
100	/home/mat/.gnome2
140	/home/mat/.macromedia
148	/home/mat/.pulse
360	/home/mat/.gstreamer-0.10
516	/home/mat/.fontconfig
1108	/home/mat/.libreoffice
1460	/home/mat/.gconf
1940	/home/mat/.local
3312	/home/mat/Desktop
6552	/home/mat/.thumbnails
18364	/home/mat/.config
35032	/home/mat/Downloads
49792	/home/mat/.mozilla
111428	/home/mat/.cache
11910928	/home/mat/.wine
12549776	/home/mat

---

### Post by linuxman94 on 2011-06-23
Ok do this:

```
sudo du -xk --max-depth 1 /home/mat/.wine/* | sort -n
```

---

### Post by matty4203 on 2011-06-23
4	/home/mat/.wine/dosdevices
4	/home/mat/.wine/userdef.reg
4	/home/mat/.wine/winetricks.log
48	/home/mat/.wine/user.reg
672	/home/mat/.wine/system.reg
195000	/home/mat/.wine/drive_c/users
273468	/home/mat/.wine/drive_c/windows
11439116	/home/mat/.wine/drive_c/Program Files
11910188	/home/mat/.wine/drive_c

---

### Post by matty4203 on 2011-06-23
my home file contents: 143 items, totalling 3.0 MB

---

### Post by linuxman94 on 2011-06-23
How many programs do you have installed in wine and what are they?

---

### Post by matty4203 on 2011-06-23
> **linuxman94 said:**
> How many programs do you have installed in wine and what are they?

just steam, and the contents: 2,370 items, totalling 7.4 GB

---

### Post by matty4203 on 2011-06-23
oh and my C usage: 42.8gb used, 106.3gb free

---

### Post by matty4203 on 2011-06-23
just rebooted to be welcomed by a message, your HDD has 133mb of memory left

which is a damn lie!

---

### Post by matty4203 on 2011-06-23
I'm tempted to just give up at this point, I have no understanding on why it is doing this.

---

### Post by linuxman94 on 2011-06-23
Something is seriously taking up loads of space in the c drive in wine. do this:

```
sudo du -xk --max-depth 1 /home/mat/.wine/drive_c/* | sort -rn
```

---

### Post by matty4203 on 2011-06-23
96	/home/mat/.wine/drive_c/install.res.1036.dll
96	/home/mat/.wine/drive_c/install.res.1031.dll
92	/home/mat/.wine/drive_c/install.res.1033.dll
84	/home/mat/.wine/drive_c/windows/command
80	/home/mat/.wine/drive_c/install.res.1042.dll
80	/home/mat/.wine/drive_c/install.res.1041.dll
76	/home/mat/.wine/drive_c/install.res.2052.dll
76	/home/mat/.wine/drive_c/install.res.1028.dll
60	/home/mat/.wine/drive_c/windows/Logs
28	/home/mat/.wine/drive_c/users
24	/home/mat/.wine/drive_c/windows/Microsoft.NET
24	/home/mat/.wine/drive_c/users/mat
20	/home/mat/.wine/drive_c/eula.3082.txt
20	/home/mat/.wine/drive_c/eula.2052.txt
20	/home/mat/.wine/drive_c/eula.1042.txt
20	/home/mat/.wine/drive_c/eula.1040.txt
20	/home/mat/.wine/drive_c/eula.1036.txt
20	/home/mat/.wine/drive_c/eula.1031.txt
20	/home/mat/.wine/drive_c/eula.1028.txt
12	/home/mat/.wine/drive_c/windows/temp
12	/home/mat/.wine/drive_c/eula.1033.txt
8	/home/mat/.wine/drive_c/windows/system
8	/home/mat/.wine/drive_c/vcredist.bmp
4	/home/mat/.wine/drive_c/windows/inf
4	/home/mat/.wine/drive_c/windows/help
4	/home/mat/.wine/drive_c/windows/Fonts
4	/home/mat/.wine/drive_c/install.ini
4	/home/mat/.wine/drive_c/globdata.ini
4	/home/mat/.wine/drive_c/eula.1041.txt

---

### Post by matty4203 on 2011-06-23
it's definatly nothing in there, but look at the folder [/] contents!!!! 384,224 items, totalling 128.0 TB
(some contents unreadable) jesus christ on a bike what the hell??

---

### Post by linuxman94 on 2011-06-23
sorry i meant this:

```
sudo du -xk --max-depth 1 /home/mat/.wine/drive_c/ | sort -rn
```

---

### Post by matty4203 on 2011-06-23
8136768	/home/mat/.wine/drive_c/
7860668	/home/mat/.wine/drive_c/Program Files
273468	/home/mat/.wine/drive_c/windows
28	/home/mat/.wine/drive_c/users
 
hmm, maybe my wine folder is bugged?? :S

---

### Post by linuxman94 on 2011-06-23
Weird it said program files was 11910188 bytes earlier but now it says 8136768 bytes!

---

### Post by linuxman94 on 2011-06-23
Do this again:

```
sudo du -xk --max-depth 1 /home/mat/.wine/ | sort -rn
```

---

### Post by matty4203 on 2011-06-23
8137500	/home/mat/.wine/
8136768	/home/mat/.wine/drive_c
4	/home/mat/.wine/dosdevices

but what i want to know is, why does the file [/] claim to have 128TB of data in there? and btw on the HDD scan that was at the top with 100% of the HDD usage, strange things a happening

---

### Post by oldfred on 2011-06-23
/dev/loop0               16481     15644         1 100% /
/dev/sdb1               229622     51192    178431  23% /host

The above indicate a wubi install. Is this a wubi install? I do not know wubi but I think the max that it can be is 30GB, but it is whatever size you selected when you installed it as it is just a file inside your windows NTFS partition.

---

### Post by linuxman94 on 2011-06-23
Thats a bug: [bug #585472]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/585472") Just ignore it.

---

### Post by matty4203 on 2011-06-23
> **oldfred said:**
> /dev/loop0               16481     15644         1 100% /
/dev/sdb1               229622     51192    178431  23% /host

The above indicate a wubi install. Is this a wubi install? I do not know wubi but I think the max that it can be is 30GB, but it is whatever size you selected when you installed it as it is just a file inside your windows NTFS partition.

yep it is a wubi install actually, is there a way to change the max without reinstalling? thanks in advance

---

### Post by linuxman94 on 2011-06-23
Wubi *shudder*

Wubi is problematic.  And you can't change the size without reinstalling.  I suggest you backup all the data you want to keep and uninstall wubi from windows, then install ubuntu on its own partition without using wubi.  This creates what is called a dual boot, and you will be able to select ubuntu or windows when you boot up.

---

### Post by matty4203 on 2011-06-23
> **linuxman94 said:**
> Wubi *shudder*

Wubi is problematic.  And you can't change the size without reinstalling.  I suggest you backup all the data you want to keep and uninstall wubi from windows, then install ubuntu on its own partition without using wubi.  This creates what is called a dual boot, and you will be able to select ubuntu or windows when you boot up.
ah right i see, i thought it was me being a complete idiot and not knowing what the hell is going on, relieved to know its the evil known as wubi, i was going insane for a while there :D. Well anyway, thanks alot for your support if anything i've learned something from it all. Catch ya on the flip side!

---

### Post by scradock on 2011-06-23
> **matty4203 said:**
> yep it is a wubi install actually, is there a way to change the max without reinstalling? thanks in advance
And why, with Windoze installed, use Wubi to run linux programs, and THEN use wine to run Windoze programs??????

Simplify, simplify, simplify!

Save what you need; reinstall Ubuntu; run Windoze programs in windoze and linux programs in linux......

---

### Post by julianb on 2011-06-23
> And why, with Windoze installed, use Wubi to run linux programs, and THEN use wine to run Windoze programs??????

Pretty funny, for sure! 

I have been using wine on a machine with Windows installed on its hard drive ... but it's because I didn't want to reboot AND none of the software I have been using requires me to boot into windows at all.

---

### Post by slooksterpsv on 2011-06-23
Oh shoot this thread made me laugh. Best Thread Ever!

Yeah Wubi, max size is 30GB, and if you install steam games, they range from 4-5GB on average, so you install 4-5 games and your maxed.

---

### Post by bcbc on 2011-06-23
Resize wubi: [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)
Migrate wubi: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

When you run the disk usage analyzer with Wubi, you need to go to the preferences and uncheck your /host partition. Otherwise it analyzes the windows host as well. If you do that you'll have a better idea of where your 16GB has gone (that's all you have for Wubi)

---


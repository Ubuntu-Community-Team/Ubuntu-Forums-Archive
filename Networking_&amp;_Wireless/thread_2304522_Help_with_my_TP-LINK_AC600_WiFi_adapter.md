---
title: "Help with my TP-LINK AC600 WiFi adapter"
date: 2015-11-27
forum: Networking &amp; Wireless
---

### Post by twisted64d on 2015-11-27
I'm a complete beginner when it comes to Linux, I've had a look around the forums and the internet and I'm trying to install the driver that TP link provide for Linux, I get error #2 when running the make command inside the folder.
[Here's the driver]("http://uk.tp-link.com/res/down/soft/Archer_T2U_V1_150901.zip") (download link) I'm trying to install. It's a recent driver from September 2015 so I don't see any compiling issues from age.
If you need any more info I'll try my best to help.
Thanks!

---

### Post by Hadaka on 2015-11-27
Hi, try the chili555 method
[URL="http://ubuntuforums.org/showthread.php?t=2240631"]http://ubuntuforums.org/showthread.php?t=2240631
[/URL]post #4
COPY and paste one line at a time,,,
good luck.
*Take note of post #6
so save this link or the instructions.

---

### Post by twisted64d on 2015-11-28
Hi Hadaka,
I've done what you've asked but there it doesn't seem to have enabled my wireless adapter.
The commands look like they've completed without any errors too.
I've rerun the commands to make sure and here's the output:
```
john@ubuntu-H81M-D2V:~$ sudo apt-get update
[sudo] password for john: 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security InRelease [64.4 kB]    
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates InRelease [64.4 kB]       
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main Sources [17.0 kB]     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports InRelease             
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted Sources [2,854 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/main Sources                    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe Sources [3,691 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/restricted Sources                  
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse Sources [1,922 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/universe Sources                    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main amd64 Packages [44.1 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/multiverse Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/main amd64 Packages                 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted amd64 Packages [10.9 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/restricted amd64 Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/universe amd64 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/multiverse amd64 Packages           
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe amd64 Packages [24.8 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/main i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/restricted i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/universe i386 Packages              
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse amd64 Packages [5,859 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/multiverse i386 Packages            
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main i386 Packages [43.4 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/main Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/main Translation-en               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/multiverse Translation-en_GB        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted i386 Packages [10.8 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe i386 Packages [24.8 kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse i386 Packages [6,052 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/multiverse Translation-en           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main Translation-en  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/restricted Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily/universe Translation-en
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/main Sources [24.4 kB]
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/restricted Sources [3,741 B]
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/universe Sources [6,112 B]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/multiverse Sources [1,922 B]
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/main amd64 Packages [62.3 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted Translation-en    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe Translation-en      
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/restricted amd64 Packages [13.3 kB]
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/universe amd64 Packages [30.9 kB]
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/multiverse amd64 Packages [5,859 B]
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/main i386 Packages [61.1 kB]
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/restricted i386 Packages [13.4 kB]
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/universe i386 Packages [30.9 kB]
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/multiverse i386 Packages [6,052 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/main Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) wily-backports/universe Translation-en
Fetched 585 kB in 3s (159 kB/s)
Reading package lists... Done
john@ubuntu-H81M-D2V:~$ sudo apt-get install linux-headers-generic build-essential git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
git is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-image-generic thermald
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.
john@ubuntu-H81M-D2V:~$ git clone [https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git](https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git)
fatal: destination path 'rtl8812AU_8821AU_linux' already exists and is not an empty directory.
john@ubuntu-H81M-D2V:~$ cd ~/rtl8812AU_8821AU_linux
john@ubuntu-H81M-D2V:~/rtl8812AU_8821AU_linux$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.2.0-18-generic/build M=/home/john/rtl8812AU_8821AU_linux  modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-18-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-18-generic'
john@ubuntu-H81M-D2V:~/rtl8812AU_8821AU_linux$ sudo make install
install -p -m 644 8812au.ko  /lib/modules/4.2.0-18-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.2.0-18-generic
john@ubuntu-H81M-D2V:~/rtl8812AU_8821AU_linux$ sudo modprobe 8812au
john@ubuntu-H81M-D2V:~/rtl8812AU_8821AU_linux$ ^C
john@ubuntu-H81M-D2V:~/rtl8812AU_8821AU_linux$
```

---

### Post by praseodym on 2015-11-28
Hi, there is a dkms package available for wily:
```

sudo apt-get install rtl8812au-dkms dkms build-essential
```
Reboot.

---

### Post by twisted64d on 2015-11-29
Hi again guys, thought I'd let you know I gave up with that model as the support guys at TP link didn't seem to know either, but I have another model (TL-WN723N) that's natively supported :p

---

### Post by Hadaka on 2015-11-29
Great ! glad you found something that works for you.
please mark this thread solved
thanks.

---


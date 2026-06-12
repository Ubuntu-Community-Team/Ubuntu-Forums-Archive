---
title: "Problems loading driver for Broadcom PCI wireless card"
date: 2014-05-05
forum: Networking &amp; Wireless
---

### Post by Arsemyth on 2014-05-05
Hi, 

I have just installed ubuntu 14.04 onto an old Dell Inspiron laptop, dual boot with WinXP.

All is working well except that I do not have a driver for my Broadcom wireless card and am reliant on an Ethernet connection.  

I have followed the instructions for identifying and installing the correct drivers from this forum, but am running into the following problems:

When I run the code to purge the bcmwl kernel source package I get the following message:
[COLOR=#ff0000]
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
[/COLOR]
So I run sudo dpkg --configure -a and after a load of text get the following~:

[COLOR=#ff0000]DKMS: install completed
Segmentation fault[/COLOR]

My Ethernet connection drops and cannot be recovered and I am left with no recourse but to reboot and start again.

Any suggestions gratefully received

---

### Post by Hadaka on 2014-05-05
hi, please COPY and paste into a terminal..
```
lspci -n | egrep '0200|0280' | awk '{print $3}'
```
post the output please.

---

### Post by Arsemyth on 2014-05-05
roger@roger-ME051:~$ lspci -n | egrep '0200|0280' | awk '{print $3}'
14e4:170c
14e4:4318
roger@roger-ME051:~$

---

### Post by Hadaka on 2014-05-05
hi, please do..
*Ignore any error and do each command
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo -rf b44
sudo -v b44
```
your wired connection should be working if it wasnt already,
connect hardwired to the enternet and
then do.
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rf b43
sudo modprobe -v b43
```
boot
thanks.

---

### Post by Arsemyth on 2014-05-05
Hi Hadaka, 

Thanks for your help.  I ran the commands you listed above, ignoring all errors as you said, with no luck I'm afraid.  Here is the ouput from the terminal:

                        ```
roger@roger-ME051:~$ [COLOR=#ff0000]sudo apt-get remove --purge bcmwl-kernel-source  [/COLOR]

 [sudo] password for roger:  
 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  
 roger@roger-ME051:~$ [COLOR=#ff0000]sudo rm /etc/modprobe.d/blacklist-bcm43.conf  [/COLOR]

 roger@roger-ME051:~$ [COLOR=#ff0000]sudo -rf b44  [/COLOR]

 sudo: b44: command not found  

 roger@roger-ME051:~$ [COLOR=#ff0000]sudo -v b44[/COLOR]  

 usage: sudo -h | -K | -k | -V  
 usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]  
 usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]  
             [command]  
 usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p  
             prompt] [-u user] [VAR=value] [-i|-s] [<command>]  
 usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p  
             prompt] [-u user] file ...  
 roger@roger-ME051:~$ [COLOR=#ff0000]sudo apt-get update[/COLOR]  

 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty InRelease  
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates InRelease  
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports InRelease  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release.gpg  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease  
 Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates Release.gpg [933 B]  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports Release.gpg  
 Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release  
 Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates Release [58.5 kB]     
 Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [58.5 kB]              
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports Release                       
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Sources                            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Sources  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Sources  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Sources  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main i386 Packages  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted i386 Packages  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe i386 Packages  
 Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [10.6 kB]  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse i386 Packages  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en_GB  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en_GB  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en_GB  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en_GB  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en  
 Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Sources [17.6 kB]  
 Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]     
 Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Sources [9,282 B]    
 Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]  
 Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [1,785 B]    
 Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [699 B]    
 Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Sources [2,220 B]  
 Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [34.9 kB]  
 Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main i386 Packages [50.3 kB]  
 Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]  
 Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe i386 Packages [26.0 kB]  
 Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]  
 Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7,277 B]  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Translation-en      
 Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [9,343 B]  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Translation-en 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Translation-en 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Translation-en  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Sources  
 Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,389 B]  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Sources  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Sources       
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Sources  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main i386 Packages  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted i386 Packages  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe i386 Packages  
 Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [15.7 kB]  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse i386 Packages  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Translation-en  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Translation-en  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Translation-en  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Translation-en 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en  
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Translation-en_GB  
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Translation-en_GB  
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Translation-en_GB  
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Translation-en_GB  
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Translation-en_GB  
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Translation-en_GB  
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Translation-en_GB  
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Translation-en_GB    
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_GB           
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_GB     
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_GB     
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_GB       
 Fetched 306 kB in 7s (41.7 kB/s)                                                
 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  
 roger@roger-ME051:~$ [COLOR=#ff0000]sudo apt-get install linux-firmware-nonfree  [/COLOR]

 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  
 roger@roger-ME051:~$ [COLOR=#ff0000]sudo modprobe -rf b43  [/COLOR]

 roger@roger-ME051:~$ [COLOR=#ff0000]sudo modprobe -v b43  [/COLOR]

 insmod /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko  
 insmod /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko  
 insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko 

 roger@roger-ME051:~$
```

---

### Post by QIII on 2014-05-05
Hello!

Please run 

```
sudo dpkg --configure -a
```

again as indicated and re-try the instructions given.

if dpkg returns any errors, please post that back.

Best wishes.

---

### Post by Hadaka on 2014-05-05
hi, also please run..
```
sudo modprobe -v b44
```
thanks...there was a typo on my last entry

---

### Post by Arsemyth on 2014-05-06
Hi QIII, 

every time I run sudo dpkg --configure -a

I get the following, which always ends with the same segmentation fault and causes my Ethernet connection to crash: 
  
roger@roger-ME051:~$ sudo dpkg --configure -a  

 [sudo] password for roger:  
 Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...  
 Removing old bcmwl-6.30.223.141+bdcom DKMS files...  
 

 -------- Uninstall Beginning --------  
 Module:  bcmwl  
 Version: 6.30.223.141+bdcom  
 Kernel:  3.13.0-24-generic (i686)  
 ------------------------------------- 
 

 Status: Before uninstall, this module version was ACTIVE on this kernel.  
 

 wl.ko:  
  - Uninstallation  
    - Deleting from: /lib/modules/3.13.0-24-generic/updates/dkms/  
  - Original module  
    - No original module was found for this module on this kernel.  
    - Use the dkms install command to reinstall any previous module version.  
 

 depmod.........  
 

 DKMS: uninstall completed.  
 

 ------------------------------ 
 Deleting module version: 6.30.223.141+bdcom  
 completely from the DKMS tree.  
 ------------------------------ 
 Done.  
 Loading new bcmwl-6.30.223.141+bdcom DKMS files...  
 First Installation: checking all kernels...  
 Building only for 3.13.0-24-generic  
 Building for architecture i686  
 Building initial module for 3.13.0-24-generic  
 Done.  
 

 wl:  
 Running module version sanity check.  
  - Original module  
    - No original module exists within this kernel  
  - Installation  
    - Installing to /lib/modules/3.13.0-24-generic/updates/dkms/  
 

 depmod....  
 

 DKMS: install completed.  
 Segmentation fault  

I hope this helps

Rog

---

### Post by Hadaka on 2014-05-06
hi, glad you got that cleared, the current driver it loaded
is not the correct driver for your card...please open a terminal  ctrl/alt/t
and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
from a wired connection connected to the internet
please do..
```
sudo apt-get update
sudo apt-get install linux firmware-nonfree
sudo modprobe b43
```
thanks.

---

### Post by Arsemyth on 2014-05-07
Hi QIII and Hadaka, 

Many thanks for all the time and effort you are giving me, it is much appreciated.

However, I am no further forward.  Every time I try to run the commands Hadaka gives me, I get the message:

[COLOR=#ff0000]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.[/COLOR]

And every time I run 'sudo dpkg --configure -a' I get:

[COLOR=#ff0000]DKMS: install completed.  
Segmentation fault  [/COLOR]

and my Ethernet crashes.

As a result I have not been able to install the drivers I need.

Is there anything else I could try?

---

### Post by Hadaka on 2014-05-07
Hi, please do..
```
sudo dpkg -r bcmwl-kernel-source
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
```
from a wired connection do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by Arsemyth on 2014-05-07
Hi Hadaka, 

You will be pleased to know that I now have a working wireless connection!  Many thanks for all your efforts (and yours QIII).

Please have a delicious Anchovy, Herring and Squid pizza on me!

Rog

---

### Post by Hadaka on 2014-05-07
Awesome!!   please mark this thread SOLVED

How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by dan95 on 2014-05-08
I applied this technique on my dv1000 w/4318 and it worked perfectly. Ubuntu 14.04.

Thank you Hadaka

---

### Post by Hadaka on 2014-05-08
@dan95...glad that worked for you !

---

### Post by Brad_Williams on 2014-05-19
Thank you.  This worked a treat for me as well.  

Since XP died and my mothers Dell Inspiron B130 (with Broadcom BCM4318 [14e4:4318] ) will not take Windows 7, I decided to use Ubuntu but could not get her wireless card to work.
I was getting the exact same errors as the OP.  I just followed these instructions and it slid right in there smoother than a boiled egg. :D

---

### Post by Hadaka on 2014-05-20
Glad i was able to "boil the egg"

---


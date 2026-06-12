---
title: "No Wired Connection"
date: 2014-04-02
forum: Networking &amp; Wireless
---

### Post by honwaiwong on 2014-04-02
I am brand new to Ubuntu.

I have just installed XP/Ubuntu dual boot on my Dell Inspirion 9400 Lap Top through CD. The version is 12.04.4 LTS.

I think the wired connection was detected during installation, but once installation is done, there is neither wired connection nor wireless.

Below are the responses to the two commands that I may be asked to perform. I would appreciate very much if someone can guide me through trouble shooting it.

Thanks

uname -r
3.11.0-15-generic
 
ifconfig
lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0
          inet6 addr:::1/128 Scope:Host
          UP LOOPBACKRUNNING  MTU:65536  Metric:1
          RXpackets:504 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:0
          RXbytes:39800 (39.8 KB)  TX bytes:39800(39.8 KB)

---

### Post by Hadaka on 2014-04-02
hi open a terminal..crtrl/alt/t and do..
```
sudo modprobe -rf wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe b44
```
with the wired connection now working..connect to the internet and
then do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

how to mark SOLVED [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by honwaiwong on 2014-04-02
I try the first command sudo modprobe -rf wl
it just hangs there for many minutes and no response.

---

### Post by Hadaka on 2014-04-02
thats ok, do each command one at a time...even if you get an error
or warning. copy and paste the commands to avoid typo's
thanks.

---

### Post by honwaiwong on 2014-04-03
Hi, I tried the first command [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -rf wl, and it waited there for more than 8 hours and no response (after I am asked for password as su).

I finally just quit. Should I be more patient or there is something wrong.[/FONT][/COLOR]

---

### Post by Hadaka on 2014-04-03
you can quit if you want to, but that wont fix the problem.
when it asks for your password...it does not show the letters
when you type them...it shows nothing..but does read what you put in.
this is a security feature. Try agin and be patient. Copy and past the commands
i gave you one at a time.
Good Luck !

---

### Post by honwaiwong on 2014-04-05
Hi,

I have done as instructed: I executed the command "[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -rf wl", enter my password when prompted, and let it run continuously undisturbed for 48 hours. The machine is still running the command. Is it possible that it is hung some how? It is still running, but I feel I need to check with you whether such a long time is unexpected.[/FONT][/COLOR]

---

### Post by Hadaka on 2014-04-05
hi,providing you are entering the command correctly, you
should be seeing some respons back after you enter your password.
which DOES NOT print back anything as you enter it. If you dont get
a response..then press ctrl/c   then enter the next command. please
post the outputs of any of these commands if possible. also..Copy and paste
```
lspci -n | egrep '0280|0200'
```
and post the results.
*If you post pack with no vaild data, i have nothing more to suggest.
thanks

---

### Post by honwaiwong on 2014-04-05
Thanks. I do ctrl-C to interrupt and enter the lspci command. See output below. I am in the middle of executing the next command (i.e., it stops giving output but does not seem to finish yet). I think it would to hurt to everything I have so far, starting from the first command which has taken 48 hours and I finally interrupt. The lscpi command is near the top.

honwaiwong@honwaiwong-MP061:~$ sudo modprobe -rf wl
[sudo] password for honwaiwong:
 
^Chonwaiwong@honwaiwong-MP061:~$ lspci -n | egrep '0280|0200'
03:00.0 0200: 14e4:170c (rev 02)
0c:00.0 0280: 14e4:4311 (rev 01)
honwaiwong@honwaiwong-MP061:~$
 sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for honwaiwong:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 63 not upgraded.
After this operation, 3,668 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 145986 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-15-generic

---

### Post by Hadaka on 2014-04-05
GREAT !
please do..
```
sudo modprobe b44
```
you should now have a wired connection.
from the wired connection..connected to the internet
please do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt -get linux-firmware-nonfree
sudo modprobe -rf b43
sudo modprobe -v b43
```
disconnect the wired connecion...BOOT
you should now have wireless

---

### Post by honwaiwong on 2014-04-06
Thanks. All work now. What confused me was that the commands finished without terminating (I have to do Control-C to interrupt).

---

### Post by Hadaka on 2014-04-06
GREAT !! i am very pleased it is working.
have fun !

---


---
title: "Ubuntu 15.10 - WiFi not detected"
date: 2015-12-10
forum: Networking &amp; Wireless
---

### Post by les9 on 2015-12-10
Hello,

I cannot seem to get my WiFi to connect on Ubuntu 15.10.

Ifconfig shows:

> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:da:74:7c  
          inet addr:10.0.0.16  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:4a:4202:d58c:218:8bff:feda:747c/64 Scope:Global
          inet6 addr: fe80::218:8bff:feda:747c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8088217 (8.0 MB)  TX bytes:1040039 (1.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:511693 (511.6 KB)  TX bytes:511693 (511.6 KB)



ls -lFA /etc/resolv.conf shows:

> ls -lFA /etc/resolv.conf
lrwxrwxrwx 1 root root 29 Dec 10 02:24 /etc/resolv.conf -> ../run/resolvconf/resolv.conf



My drivers are Broadcom.  What should I be doing to fix this?  Thanks!

---

### Post by slickymaster on 2015-12-10
*Moved to the ***Networking & Wireless*** sub-forum*

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums

---

### Post by les9 on 2015-12-10
[ATTACH]266082[/ATTACH]

Hopefully that works

---

### Post by Hadaka on 2015-12-10
Hi,from a working wired connection please do.
```
sudo apt-get update
sudo apt-get dist-upgrade
```
then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install --reinstall firmware-b43-installer
sudo modprobe b43
```
Copy and paste one line at a time..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
boot,remove wired connection and test wireless

---

### Post by les9 on 2015-12-10
When I tried to do the 

```

sudo apt-get install --reinstall firmware-b43-installer
```

I got:

```
enel@enel-MP061:~$ sudo apt-get install --reinstall firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,120 B/27.4 kB of archives.
After this operation, 158 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Media change: please insert the disc labeled
 'Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)'
in the drive '/media/cdrom/' and press enter
```


And it stopped

---

### Post by Hadaka on 2015-12-10
Hi, were you attached to the internet with the wired connection?
did you run the updates??
you should not have gotten..
```
Media change: please insert the disc labeled
 'Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)'
in the drive '/media/cdrom/' and press enter
```
or are you in the "Try Ubuntu" mode?????

Please open a terminal ctrl/alt/t then COPY and paste this command,
```
grep -i cdrom /etc/apt/sources.list
```
please post the output
thank you.

---

### Post by dellboy56 on 2015-12-11
What driver is it and if its a broadcom et your install disk that u created and go to pools restrict d  install dkms then go to pools restricted and if its a broadcom driver click bcwml and install that you should see wifi connections avaible that what worked for me

---

### Post by Hadaka on 2015-12-12
@dellboy6 your suggestion gets the broadcom-kernel-source driver that is incorrect for this card
this card requires the b43 driver,please read the sticky to determine the driver.

---


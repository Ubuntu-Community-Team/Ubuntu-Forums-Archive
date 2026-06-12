---
title: "i need help getting wifi working (please)"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by Beowulf.1000 on 2008-02-23
Ubuntu 7.10 i385 desktop. Acer Aspire 5520-5716 notebook, wifi inside it is "Atheros AR5006EG 802.11 b/g Wireless PCI Express Adapter" on a PCI bus. I have installed madwifi on my other laptop just fine, this one has me stumped. Any help appreciated. This is a notebook pc i take to the coffee shop each day, it pains me to boot into Windows just to use wifi which I just do each day.  eth8 must be my wired LAN cable to my router I figure.

beowulf@acer-laptop:~$ iwconfig
lo        no wireless extensions.
eth8      no wireless extensions.

beowulf@acer-laptop:~$ ifconfig
eth8      Link encap:Ethernet  HWaddr 00:00:6C:A3:08:55  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fea3:855/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2333889 (2.2 MB)  TX bytes:193313 (188.7 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

When I try to run the madwifi script:

$ sudo ./madwifi/scripts/madwifi-unload.bash 
FATAL: Module wlan is in use

$ sudo rmmod wlan
ERROR: Module wlan is in use by ath_pci

$ rmmod ath_pci
ERROR: Removing 'ath_pci': Operation not permitted
beowulf@acer-laptop:~/madwifi-0.9.3.3/scripts$

---

### Post by Paris Heng on 2008-02-23
I think is your driver problems, run the following script if you want to try in different way. For this case here, I am using madwifi-0.9.3.1. Changed the RED color to your intended name.

> #!/bin/sh
#Name: madwifi.sh
#This script is for Madwifi driver installation with Ubuntu 7.04
#Prior to installation, you must have Internet connection to proceed

#Get what is needed to compile the source

sudo apt-get -y install build-essential bin86

#Copy the .tar.gz to the /usr/src/ folder
#Change the Madwifi driver revision if necessary

sudo cp /home/[COLOR="Red"]<USER>[/COLOR]/Desktop/[COLOR="Red"]madwifi-0.9.3.1.tar.gz[/COLOR] /usr/src/

#Change to the /usr/src folder

cd /usr/src

#Decompress the tarball

sudo tar -xzf [COLOR="Red"]madwifi-0.9.3.1.tar.gz[/COLOR]

#Install the sharutils from the package manager

sudo apt-get -y install sharutils

#Change to the folder that the tarball extracted to

cd /usr/src/[COLOR="Red"]madwifi-0.9.3.1[/COLOR]

#Make the drivers (during this time the procedure may ask you to remove the older drivers, let it do so)

sudo make clean
sudo make
sudo make install

#You don't need to but as you are going to reboot you can test your work so far

sudo modprobe ath_pci

#Delete the archive which we copy earlier

rm -r [COLOR="Red"]madwifi-0.9.3.1.tar.gz[/COLOR]

#You can remove the archive from your directory

rm -r /home/[COLOR="Red"]<USER>[/COLOR]/Desktop/madwifi-0.9.3.1.tar.gz

#You will need to modify the modules file to make this change permanent in /etc/modules

echo "Add ath_pci to  the /etc/modules"
CODE=ath_pci
echo $CODE >> /etc/modules


Then, you can use the wlanconfig and iwconfig to change the state of the wifi NIC.

---

### Post by mickinator on 2008-02-23
There are a lot of problems with the Atheros wireless cards, I have the 5007EG chip, but this should work for yours aswell, I think theyre identical, just different names.

Download this madwifi snapshot to your desktop:

snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz

Open terminal and change to your desktop:

$ cd Desktop

Then extract the archive:

$ tar -xvzf madwifi-ng-r2756-20071018.tar.gz

Now download this patch:

madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw

Install patch if you don't have it:

$ sudo apt-get install patch

Drag and drop the patch into the folder that was created when you extracted the archive.

Now patch the file ( in terminal )

$ patch -p0 < madwifi-ng-0933.ar2425.20071130.i386.patch

Now make sure that Java is up to date and make are up to date:

$ sudo apt-get install java && sudo apt-get install make

This'll let you know whether or not they're up to date.

Now make it:

$ make

And install it:

$ sudo make install

Once this is done:

$ modprobe ath_pci

Now restart your box and it should work perfectly!!!

---

### Post by Beowulf.1000 on 2008-02-23
apt-get does not find nor install java, which is odd because I installed Java runtime and also Java for web with synpatic manager.

$ sudo apt-get install java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package java

---

### Post by Beowulf.1000 on 2008-02-23
I get a long list of errors when attempting the make command.

8$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/beowulf/Desktop/madwifi-ng-r2756-20071018 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  HOSTCC  /home/beowulf/Desktop/madwifi-ng-r2756-20071018/ath_hal/uudecode
/home/beowulf/Desktop/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/beowulf/Desktop/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/beowulf/Desktop/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/beowulf/Desktop/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/beowulf/Desktop/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/beowulf/Desktop/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
....

---

### Post by Beowulf.1000 on 2008-02-24
My acer aspire laptop uses something called "MAC Bridge Miniport" that the wifi and even the LAN goes through. I just went into Windows network settings and disabled that MAC miniport, going to see if I can get wifi in Windows without the MAC Bridge. If I can, then I maybe need to find some way to disable that MAC Bridge during the Ubuntu boot -- I am thinking that hardware in the laptop might be funking with the normal atheros chipset and madwifi. I have done madwifi with atheros chipsets before no problem. That is why this is puzzling.

---

### Post by mickinator on 2008-02-24
Sorry my bad:

$ sudo apt-get install sun-java6-jdk

---

### Post by Beowulf.1000 on 2008-02-24
I appreciate all the help here, but I think I am pretty much screwed on this laptop. I just installed linuxant.com's commercial version of madwifi / ndiswrapper, and the windows drivers do not work. I have had linuxant work on several PCs in the past, easy as pie. I think this laptop is just too funky to get wifi working on it. Unfortunately since I make my living using wifi from a coffee shop every morning, I am likely going to have to just use WinXP on this laptop. :( Not by choice, just a reality. Thanks all for the help though.

> **mickinator said:**
> Sorry my bad:

$ sudo apt-get install sun-java6-jdk

---


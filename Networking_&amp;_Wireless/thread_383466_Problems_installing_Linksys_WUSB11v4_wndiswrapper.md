---
title: "Problems installing Linksys WUSB11v4 w/ndiswrapper"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by pollywog on 2007-03-13
Hello, I'm a newbie having problems installing a wireless usb adapter on my Mom's computer. I'm following the directions at : [https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?action=fullsearch&value=linkto%3A%22WifiDocs%2FDevice%2FLinksys+WUSB11v4+%28ndiswrapper%29%22&context=180](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?action=fullsearch&value=linkto%3A%22WifiDocs%2FDevice%2FLinksys+WUSB11v4+%28ndiswrapper%29%22&context=180)

After I've installed ndiswrapper, and the .exe driver, I can get the system to recognize the device as installed, but I get no wireless entry in System>Administration>Networking, and Network Manager does not have any connection option oter than my wired LAN that I'm using to set up the system.

During the set up process my Terminal looks like this[B]

[I]hillary@hillary-desktop:~$ cd WUSB11v4_08272004/Drivers
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ sudo ndiswrapper -i WUSB11v4.inf
wusb11v4 is already installed. Use -e to remove it
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ ndiswrapper -l
Installed ndis drivers:
wusb11v4        driver present, hardware present 
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ ls /etc/ndiswrapper/
wusb11v4
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ ls /etc/ndiswrapper/wusb11v4/
13B1:000B.F.conf  m4301a.sys  mdusb.out  wusb11v4.inf
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ sudo depmod -a
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ sudo modprobe ndiswrapper
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ cd
hillary@hillary-desktop:~$ lsusb

hillary@hillary-desktop:~$ cd WUSB11v4_08272004/Drivers
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ sudo ndiswrapper -i WUSB11v4.inf
wusb11v4 is already installed. Use -e to remove it
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ ndiswrapper -l
Installed ndis drivers:
wusb11v4        driver present, hardware present 
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ ls /etc/ndiswrapper/
wusb11v4
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ ls /etc/ndiswrapper/wusb11v4/
13B1:000B.F.conf  m4301a.sys  mdusb.out  wusb11v4.inf
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ sudo depmod -a
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ sudo modprobe ndiswrapper
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ cd
hillary@hillary-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 001 Device 001: ID 0000:0000  
hillary@hillary-desktop:~$ cd WUSB11v4_08272004/Drivers
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ cd
hillary@hillary-desktop:~$ /WUSB11v4_08272004/Drivers$ iwconfig
bash: /WUSB11v4_08272004/Drivers$: No such file or directory
hillary@hillary-desktop:~$ cd WUSB11v4_08272004/Drivers
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 001 Device 001: ID 0000:0000  
hillary@hillary-desktop:~$ cd WUSB11v4_08272004/Drivers
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ cd
hillary@hillary-desktop:~$ /WUSB11v4_08272004/Drivers$ iwconfig
bash: /WUSB11v4_08272004/Drivers$: No such file or directory
hillary@hillary-desktop:~$ cd WUSB11v4_08272004/Drivers
hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ [/B]



              Appearently there is a problem by this point as there is there is nothing related to wlan0 in this output. I have tried to do this procedure several times, and at other times there is an output for wlan0 that looks like the instructions show- an unconfigured device. If I go further:

[B]hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ gksudo gedit /etc/network/interfaces
(gedit:8013): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/B]

The file looks like this:

[B]auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto eth0[/B]

I edit it so that it looks like this:

[B]auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto eth0

iface wlan0 inet dhcp
wireless-essid My_Essid
auto wlan0[/B]

In which I've omitted the line "wireless-key1 XXXXXXXXXXXXXXXXXXXXXXXXXX" since she is  going to connect to an unsecured wireless network at my grandparents house. My guess is that this is where I'm going awry. I then test the device:

[B]hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ lsusb 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 001 Device 001: ID 0000:0000  
[/B]
Which seems OK. I then attempt to bring up the network: 

[B]hillary@hillary-desktop:~/WUSB11v4_08272004/Drivers$ sudo ifup wlan0
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.[/B]

Which obviously isn't OK. Does anyone have any ideas where I went wrong, and what I need to do to get back on track? By the way, one time that I tried to go thru this installation the wireless actually worked for awhile, but I rebooted and found myself back at square one. Any help would be greatly appreciated-

---

### Post by pollywog on 2007-03-20
Success at last!

I was finally able to get my wireless usb up and running by following a mish-mash of tips from the following pages:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

[http://ubuntuforums.org/showthread.php?t=372074&highlight=wusb11](http://ubuntuforums.org/showthread.php?t=372074&highlight=wusb11)

The exact procedure that worked for me, on a clean Edgy install was:

```
user@ubuntu:~$ sudo apt-get update 

```
```
user@ubuntu:~$ sudo apt-get install build-essential
```

```
user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`
``` 
```
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

```

Go to website:
[http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)
download latest ndiswrapper to home folder (version 1.38 here)
```

user@ubuntu:~$ tar xvzf ndiswrapper-1.38.tar.gz 
```

```
user@ubuntu:~$ cd ndiswrapper-1.38
```

```
user@ubuntu:~/ndiswrapper-1.28$ make distclean
```
```

user@ubuntu:~/ndiswrapper-1.28$ make
```

```
user@ubuntu:~/ndiswrapper-1.28$ sudo make install
```

Download driver (install in home folder) from:

[ftp://ftp.linksys.com/pub/network/WUSB11v4_08272004.exe](ftp://ftp.linksys.com/pub/network/WUSB11v4_08272004.exe)

enable all repositories and install these 3 packages:

 cabextract

 unshield

 unzip
```

user@ubuntu::~/ndiswrapper-1.28$ cd ~
``` 

```
user@ubuntu:~$ unzip WUSB11v4_08272004.exe 
```
```

user@ubuntu:~$ cd WUSB11v4_08272004/Drivers
```
```

user@ubuntu:~/WUSB11v4_08272004/Drivers$ sudo ndiswrapper -i WUSB11v4.inf
```

Go ahead and plug in your device

```
user@ubuntu:~/WUSB11v4_08272004/Drivers$ sudo depmod -a
```
```

user@ubuntu:~/WUSB11v4_08272004/Drivers$ sudo modprobe ndiswrapper
```

```
lsusb
```

Hopefully you now see your device
```

iwlist wlan0 scan
```

You should now see all available networks

```
sudo iwconfig wlan0 essid XXXX mode managed
```

Where XXXX  is your network

```
sudo ifconfig wlan0 up
```


If everthing ok then:

```
sudo ndiswrapper -m
```


It worked for me I hope it works for you! Good Luck!
-Pollywog (Working on Shellback)









3

---

### Post by pollywog on 2007-03-20
Oh Yeah, Don't forget to go into System>Administration>Networking to enable and name the wireless connection-P.W.

---

### Post by pollywog on 2007-03-22
Well, ran into a little trouble, but back up to speed now. After going thru the above procedure, on a clean install, the device worked- but occasionally on reboot I would have to unplug and replug it in order for the system to recognize the device. Furthermore, when I installed the 140+ updates something killed the connection, and I couldn't figure out why. Finally I reinstalled 6.10, installed all the additional stuff I wanted, and updated everything. After all of that I went thru the above procedure, and it now is working consistantly, and stably. Fingers crossed-P.W.:)

---


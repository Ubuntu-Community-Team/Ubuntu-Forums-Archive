---
title: "problem using ndiswrapper"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by awperk on 2007-03-20
i'm trying to use ndiswrapper to get my broadcom wireless working and i can't get ndiswrapper fully compiled. this is the output i get when i try to use the "make" command after succesfully completing the "make distclean" command.

awperk@awperk-laptop:~/ndiswrapper-1.38$ make
make -C driver
make[1]: Entering directory `/home/awperk/ndiswrapper-1.38/driver'
Can't find kernel build files in /lib/modules/2.6.15-28-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/awperk/ndiswrapper-1.38/driver'
make: *** [all] Error 2

what am i doing wrong? should i be in a different directory or something because i'm just trying to follow what is here [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
 thanks!

---

### Post by nathanhillinbl on 2007-03-20
seems to me that ndiswrapper has issues, i had no problems with it when i was using dapper lts, but once i upgraded to edgy, i cant get it working.

---

### Post by tomiu on 2007-03-20
> **awperk said:**
> 
make[1]: Entering directory `/home/awperk/ndiswrapper-1.38/driver'
Can't find kernel build files in /lib/modules/2.6.15-28-386/build;
  
I think u should install kernel headers

---

### Post by awperk on 2007-03-20
how do i install the kernal headers?

---

### Post by tomiu on 2007-03-20
> **awperk said:**
> how do i install the kernal headers?

Well i remember i installed the kernel header from Adept(KDE), if u use GNOME than Synaptic

or u can install from terminal:
sudo apt-get install linux-headers-`uname -r`

---

### Post by awperk on 2007-03-20
ok thanks for all the help thus far, but it seems like one problem after another....
i got ndiswrapper installed and compiled so now i'm installing the windows driver. i have the correct driver which needs the .inf and .sys files. is there a way to install them both or something because when i move them seperately this is what i get.

```
awperk@awperk-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
awperk@awperk-laptop:~$ sudo ndiswrapper -i bcmwl5.sys
Installing bcmwl5.sys
awperk@awperk-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
bcmwl5.sys      invalid driver!
```

am i supposed to only install the .inf file and put the .sys file somewhere else, please help. i feel like i'm so near i can smell it!

---

### Post by SactoBob on 2007-03-20
> bcmwl5.sys      invalid driver!

It looks like ndiswrapper does not like your driver.  Just because it is the "correct" driver for Windows does not mean that it will work with ndiswrapper.  Sometimes a different driver will work, and some Broadcom chips simply won't work.

Start by finding what type of chip you are dealing with, and check the various compat. lists to see if somebody got that chip working and how they did it.

You can find out which Broadcom by entering "lspci" if your card is pci or pcmcia.

---

### Post by Jose Catre-Vandis on 2007-03-20
Have a look here, this might help

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

I am not sure if you need to install the .sys file, then .inf should take care of that, well that was the case with my netgear device in dapper?

---

### Post by awperk on 2007-03-20
you are the man jose! there was a script in your link that loaded everything and my wireless light is on and the driver was recognized as correct.

now my only problem is that it wont show up in either network manager or wifi radar.

how do i get ubuntu to recognize and use my card?

---

### Post by Jose Catre-Vandis on 2007-03-21
Sometimes, when using ndiswrapper, you cannot use the GUI proggies to configure the adapter, and you have to do everything from the CLI (command line). if this is the case then the following commands will be your friends:

ifconfig
&
iwconfig

you can make all your settings using iwconfig, something like:

```
iwconfig wlan0 /*you can see some information about the setting*/

iwlist wlan0 scan /*you can see some information about your AP*/

iwconfig wlan0 essid YOURESSID mode managed

dhcpclient wlan0 
``` 

or go into your /etc/network/interfaces file and make sure you have this in it (assumes DHCP and no security, e.g. WEP) 

```
 # The primary wireless interface
auto wlan0
iface wlan0 inet dhcp
wireless-essid youressid
wireless-mode managed

```

or for a static IP, something like:

```
# The primary network interface
auto wlan0
iface wlan0 inet static
wireless-essid youressid
address 192.168.0.60
netmask 255.255.255.0
gateway 192.168.0.1
```

---


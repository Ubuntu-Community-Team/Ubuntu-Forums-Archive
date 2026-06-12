---
title: "“how to” for wireless broadcom BCM4329 at Hardy"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by rizitis on 2008-05-24
I will try to write a “how to” for wireless broadcom BCM4329 at Hardy.
unfortunately my English are not so good , so please forgive me.

First open synaptic and make sure that you have install the following:

ndisgtk 0.83-1
ndiswrapper-common 1.50
ndiswrapper-utils-1.9
b43-fwcutter  1:011-1 

then command at terminal
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

now you have to download the drivers  at the /tmp directory,from 
 [http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859959649&packedargs=sku%3DWMP300N&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5964959649B01&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859959649&packedargs=sku%3DWMP300N&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5964959649B01&displaypage=download#versiondetail)

 then rename the exe file (because for some reason some times we cant unzip it with the full name on it)  like this R20071019.exe
open the terminal and command

```
cd /tmp
unzip R20071019.exe
```

after that, open ndiswrapper and isntall the file bcmwl5.inf
you will find it at /tmp->WPMN300N->drivers->xp_2k

then command at terminal
```
ndiswrapper -l
```
if the answer is something like this 
```
Installed ndis drivers:
{name of driver}* driver present, hardware present
```

then we are in the right direction .
After command 
```
sudo depmod -a
sudo modprobe ndiswrapper
```

and 
```
gksu gedit /etc/modules
``` 
a window opens 
we add at the and the word
```
ndiswrapper
```
 save and exit.

Then follow these steps:
 Open the Networking Admin tool (System | Administration | Networking), select the Wireless connection and click Properties, ensure the Enable roaming mode checkbox is ticked. 
1.Click the Network Manager icon (computers icon in the top right corner of system tray), your network ESSID should be shown in the drop-down list. Select your network by clicking on it. 
2.If the Network requires any further configuration (eg WEP key), a dialog should appear, select the correct settings and paste in your key. 
Now you reboot and you are ready...

ps. this solution is based on these introductions [http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)
we found that it works as it is written here, for  broadcom BCM4329 at Hardy

---

### Post by Spondicious on 2008-05-25
I can't get past the bit about installing the driver

[INDENT]after that, open ndiswrapper and isntall the file bcmwl5.inf
you will find it at /tmp->WPMN300N->drivers->xp_2k

then command at terminal[/INDENT]


I am getting this in terminal

ndiswrapper
Error: no ndiswrapper utils found!

I am starting to believe that I will just have to get a USB wireless dongle that will be  supported with Ubuntu

I have tried so many of the solutions on the forum here a- all with now success I feel like I am banging my head against a brick wall.

Help Please.

---

### Post by rizitis on 2008-05-25
Ndiswrapper for Ubuntu comes in 2 parts, the ndiswrapper-common part which you'll have and ndiswrapper-utils, check to make sure they're the correct version, I recommend you have a look through packages.ubuntu.com [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=gutsy&release=all) those are the 2 you'll need to install, just search ndiswrapper on Adept assuming you have internet access on the machine. Otherwise download the .deb files from the website 

also command this and copy paste here the results 
```
sudo lspci
```

---

### Post by Spondicious on 2008-05-25
I downloaded the files you said and then here is the results of that commandline
> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

---

### Post by rizitis on 2008-05-25
> Network controller: Broadcom Corporation [COLOR="Red"]BCM4310[/COLOR] USB Controller (rev 01) 

you dont have bcm4329 but bcm4310. dont worry I have the same and its working, I will give you the commands in 10min at a new post.

---

### Post by rizitis on 2008-05-25
you have to do the same steps only the driver is different. 

downland the driver from here [http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe)

or follow the steps from here [http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

the driver for your bcm is the one i gave you.

good luck!

---

### Post by Spondicious on 2008-05-25
I downloaded the driver and this is what I am getting now

spondicious@Spondicious:~$ sudo ndiswrapper -i /tmp/DRIVER_ROW/bcmwl5.inf
couldn't open /tmp/DRIVER_ROW/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
spondicious@Spondicious:~$ sudo ndiswrapper -i /tmp/DRIVER_US/bcmwl5.inf
couldn't open /tmp/DRIVER_US/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.


The file is surely there ???


tomorrow  will have to resume this

---

### Post by rizitis on 2008-05-25
were did you downloaded the file? at /home or at /tmp  
did you unzip it ?
if yes,go 
system-admin-ndiswrapper
and try to install it from ndiswrapper
its the same.

---

### Post by rizitis on 2008-05-25
the link I gave you [http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe)
have 7 steps. now you are at 4 
if the 3 before steps was ok for you 
then the file must be at the /tmp
so if you cant install it by commandline 
go system-administration-ndiswrapper and try to find it from the button 
+install new driver
the file you are looking for is this
bcmwl5.inf
when you install it go back to finish the steps from
```
ndiswrapper -l
```

---

### Post by eperrone on 2008-05-25
I have BCM 4328 and I cannot get it to work with WPA.  I am connecting with the access point and I am able to browse the inter but with WPA enable my download speed slows to an absolute crawl even less than my upload speed on dsl.

When I put eithert no security or WEP security everything works like a champ.

Anyone see this before?


Thaks
Eric

---

### Post by r3a7amd on 2008-07-09
I have the bcm4328 as well and been searching for solution for past two/three weeks and tried everything and still doesnt work. its frustrating.

---

### Post by Spondicious on 2008-07-10
I was getting frustrated too but then I found that there are 2 versions of the driver ?? One is the correct driver and the other just doesn't work BUT both have the same name.
I downloaded the one suggested by rizitis and when I made sure that it was the one I was installing with the ndiswrapper installer it worked straight away after that

Keep trying 
 
Good Luck

---

### Post by rizitis on 2008-08-01
> **r3a7amd said:**
> I have the bcm4328 as well and been searching for solution for past two/three weeks and tried everything and still doesnt work. its frustrating.

[http://ubuntuforums.org/showthread.php?t=859193&highlight=bcm4328](http://ubuntuforums.org/showthread.php?t=859193&highlight=bcm4328)

[http://ubuntuforums.org/showpost.php?p=5537394&postcount=12](http://ubuntuforums.org/showpost.php?p=5537394&postcount=12)

---


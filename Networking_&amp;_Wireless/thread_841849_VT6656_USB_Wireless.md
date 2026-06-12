---
title: "VT6656 USB Wireless"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by e_swallie on 2008-06-26
I am trying to setup a Via VT6656 USB wireless card on my system but i am very new to Linix and cant get it to work.   Has anybody used this device and has it working on thier ubuntu system?


i am running ubuntu version 7.10

---

### Post by chili555 on 2008-06-26
This may help. It's all I can find on your device. [http://www.logicsupply.com/blog/2008/01/02/building-the-vt6656-linux-driver-for-ubuntu/](http://www.logicsupply.com/blog/2008/01/02/building-the-vt6656-linux-driver-for-ubuntu/)

---

### Post by e_swallie on 2008-06-27
well i am not at the machine now but i will look into this when i get home.  unfortunatly i am very new to linix in general, and have no experiance at all compiling and installing drivers.   i will give all this a go later and see what happens.  however with the posts by users talking about how the driver does not work for them i am not going to expect much i guess.    probably should have researched the wireless card before i bought it.   live and learn i guess.

---

### Post by chili555 on 2008-06-27
We will be glad to help you. If you don't understand an instruction, just ask us.

---

### Post by e_swallie on 2008-06-27
Ok i followd the instructions found there and it all seemed to be going ok up through the make process.   however then it tells me to run the ndiswrapper program and give it a few args.  however this does not seem to work.  i get an error when i type that in



EDIT--  OK i take that back.  when i type make i get several errors and i have no clue what it all means. there is some sort of a patch file he mentions in his document.  and i try to apply that but i have no clue if this works or not.  then i run make again, and still get errors.  however the errors seem to be different on the second pass.






Ok update:

i have the ndiswrapper working it seems.   i have a driver in there and it shows attached hardware.  but now i am stuck again.  what do i need to do to now enable this device and use it?

---

### Post by chili555 on 2008-06-28
> Via VT6656 Wireless LAN____Ubuntu 7.10Here is the procedure I worked out running kernel version 2.6.22-14-generic, which is what I assume you have. In a terminal:```
mkdir vt6656
cd vt6656
wget 'http://www.viaarena.com/Driver/vt6656-linux-x86-src-v113.rar'
unrar -y x vt6656-linux-x86-src-v113.rar
cd VT6656-Linux-x86-src-v113
unrar -y x VT6656-Linux-x86-113-src-CPUPlatfrom.rar
wget http://www.logicsupply.com/pub/vt6656.gutsy.patch
patch -p1 < vt6656.gutsy.patch
make
```'Make' runs with a few warnings but no errors. I do not have the device, so I did not go on to:```
sudo make install
sudo modprobe vntwusb
```And I have no way to know if it actually brings the device to life.

---

### Post by chili555 on 2008-06-28
> i have the ndiswrapper working it seems. i have a driver in there and it shows attached hardware. but now i am stuck again. what do i need to do to now enable this device and use it?Does the device now show up in:```
sudo lshw -C network
```with a logical name, *wlan0*, perhaps? If so, can you click the Network Manager icon, select your ESSID, supply your encryption details and connect?

You can use ndiswrapper OR the module I described above, but not both.

---

### Post by e_swallie on 2008-06-28
root@M200:/home/eric/Desktop/temp# lshw -C network
*-network:0 
description: Ethernet interface
product: RTL-8110SC/8169SC Gigabit Ethernet
vendor: Realtek Semiconductor Co., Ltd.
physical id: 9
bus info: pci@0000:00:09.0
logical name: eth0
version: 10
serial: 00:30:18:ab:f1:5f
size: 10MB/s
capacity: 1GB/s
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=10MB/s
*-network:1
description: Ethernet interface
product: RTL-8110SC/8169SC Gigabit Ethernet
vendor: Realtek Semiconductor Co., Ltd.
physical id: b
bus info: pci@0000:00:0b.0
logical name: eth1
version: 10
serial: 00:30:18:ab:f1:60
size: 10MB/s
capacity: 1GB/s
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=10MB/s
*-network:2
description: Ethernet interface
product: RTL-8110SC/8169SC Gigabit Ethernet
vendor: Realtek Semiconductor Co., Ltd.
physical id: c
bus info: pci@0000:00:0c.0
logical name: eth2
version: 10
serial: 00:30:18:ab:f1:61
size: 10MB/s
capacity: 1GB/s
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=10MB/s
*-network:3
description: Ethernet interface
product: VT6102 [Rhine-II]
vendor: VIA Technologies, Inc.
physical id: 12
bus info: pci@0000:00:12.0
logical name: eth3
version: 78
serial: 00:30:18:ad:61:c1
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
*-network DISABLED
description: Wireless interface
physical id: 1
logical name: eth4
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=vntwusb driverversion=1.13 multicast=yes wireless=802.11-a/b/g
 
 
 
 
 
 
EDIT--
 
OMG after i posted this i realized the last bit was the wireless card.  so i ran the network configuration utility, and sure eneugh the wireless card now is in the list.  unfortunatly i am not at home at this time, so i can't test this all out to see if it is actually working, but it looks VERY promising so far.   
 
 
Chilli if you were here in UAE id have to take you out for a night on the town.  you may have saved this linux box from a reformat into an XP box.  and i did so want to learn Linux.  lol now if you could just fix my LCD problems i mentioned in my other post.  :p

---

### Post by chili555 on 2008-06-28
> *-network DISABLED
description: Wireless interface
physical id: 1
logical name: eth4
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=vntwusb driverversion=1.13 multicast=yes wireless=802.11-a/b/gWe are certainly closer!

---

### Post by e_swallie on 2008-06-28
Yes looks very good so far. ill give it a go in a few hours when i get home from work
 
 
 
 
 
[EDIT]
 
Ok after very extensive help from Chili this is still not workoing.  If anybody else out there would like to take a stab at this let me know.  I would really like to get this resolved before I just give up and install windows on this system.
 
 
Anf thank you so much for your try at a solutio0n Chili, if you have any other ideas feel free to contact me and let me know.

---

### Post by SJCBColby on 2009-04-08
Gents,

I managed to get the Via VT6656 USB WiFi addapter working that came with my Zotac 9300 ITX Wifi board.

Here is the procedure I found worked.

Basically what needs to be done is down load the OEM source files and then compile them on your machine.


Preparing for the Install

You can down load the driver directly from Via and original manufacturer at

[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3160&SubCatID=176](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3160&SubCatID=176)

As of April 4 2009 the latest version was 1.19.12

It will download on your desktop as a zip file.

You can explore it by clicking on the folder.

Extract it to a folder on the desktop 

I found the following Ubuntu comunity documentation on how to compile this very helpful

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

You will need some tools – 
By default, Ubuntu does not come with the tools required. You need to install the package build-essential for making the package and checkinstall for putting it into your package manager. These can be found on the install CD or in the repositories, searching in Synaptic Package Manager 

I was able to get and install both using the Synaptic Package Manager.

Now you need to create a directory to work in and have sufficient permissions to copy the file there and work on it.

I made directory temp1

Open up under application, accessories, a terminal session.

Make a directory to work in ( I used temp1 for the name)

   Please enter the following commands at the UNIX prompt. Remember, UNIX is
    case sensitive and make sure your root login.

    1) Create a temporary directory:
        	sudo mkdir /temp1

    2) Change to the temporary directory:
       	 cd /temp1

    3) Make sure this directory is writable by you under yourusername. 
 		sudo chown yourusername /temp1



Now click on Places at the top of the desk top, 
A window will open, then click on Computer, then Filesystem and you should see the directory you just made.
 
Grab the via driver you extracted to the desk top and drop it into your directory temp1

Now make the name of the folder a little easier to work with 
	Right click and under Properties shorten the name 
	I shortened it to VT6656_Linux

Now change your directory to the file containing the extracted files.

Cd /temp1/VT6656_Linux



Note with this procedure you don’t need to copy from a DOS disk or untar the archive file as refrenced in the Via Txt doc.

Now you are ready to compile and prepare for installation

    4) Type the command sudo checkinstall
it will ask you for your password
You will be asked if you want to put in a description – do so then press – ENTER, press ENTER again on a blank line and it will then give you a screen of default values for building the package.
Leave them and press ENTER to continue

You will see computer generate a number of files 



When it is done you can check the log

I found when I shut down my computer and restarted it loaded and my wireless comes up with the desktop and worked with no problems. 

Hope this helps.


SJC

---

### Post by SJCBColby on 2009-04-08
This is the procedure I found worked for the VT6656 USB Wifi adapter under 8.10

Basically what needs to be done is down load the OEM source files and then compile them on your machine.


Preparing for the Install

You can down load the driver directly from Via and original manufacturer at

[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3160&SubCatID=176](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3160&SubCatID=176)

As of April 4 2009 the latest version was 1.19.12

It will download on your desktop as a zip file.

You can explore it by clicking on the folder.

Extract it to a folder on the desktop 

I found the following Ubuntu comunity documentation on how to compile this very helpful

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

You will need some tools – 
By default, Ubuntu does not come with the tools required. You need to install the package build-essential for making the package and checkinstall for putting it into your package manager. These can be found on the install CD or in the repositories, searching in Synaptic Package Manager 

I was able to get and install both using the Synaptic Package Manager.

Now you need to create a directory to work in and have sufficient permissions to copy the file there and work on it.

I made directory temp1

Open up under application, accessories, a terminal session.

Make a directory to work in ( I used temp1 for the name)

   Please enter the following commands at the UNIX prompt. Remember, UNIX is
    case sensitive and make sure your root login.

    1) Create a temporary directory:
        	sudo mkdir /temp1

    2) Change to the temporary directory:
       	 cd /temp1

    3) Make sure this directory is writable by you under yourusername. 
 		sudo chown yourusername /temp1



Now click on Places at the top of the desk top, 
A window will open, then click on Computer, then Filesystem and you should see the directory you just made.
 
Grab the via driver you extracted to the desk top and drop it into your directory temp1

Now make the name of the folder a little easier to work with 
	Right click and under Properties shorten the name 
	I shortened it to VT6656_Linux

Now change your directory to the file containing the extracted files.

Cd /temp1/VT6656_Linux



Note with this procedure you don’t need to copy from a DOS disk or untar the archive file as refrenced in the Via Txt doc.

Now you are ready to compile and prepare for installation

    4) Type the command sudo checkinstall
it will ask you for your password
You will be asked if you want to put in a description – do so then press – ENTER, press ENTER again on a blank line and it will then give you a screen of default values for building the package.
Leave them and press ENTER to continue

You will see computer generate a number of files 



When it is done you can check the log

I found when I shut down my computer and restarted it loaded and my wireless comes up with the desktop and worked with no problems. 

Hope this helps.


SJC

---

### Post by spkm on 2009-04-22
> **SJCBColby said:**
> This is the procedure I found worked for the VT6656 USB Wifi adapter under 8.10

Basically what needs to be done is down load the OEM source files and then compile them on your machine.


Preparing for the Install

You can down load the driver directly from Via and original manufacturer at

[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3160&SubCatID=176](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3160&SubCatID=176)

As of April 4 2009 the latest version was 1.19.12

It will download on your desktop as a zip file.

You can explore it by clicking on the folder.

Extract it to a folder on the desktop 

I found the following Ubuntu comunity documentation on how to compile this very helpful

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

You will need some tools – 
By default, Ubuntu does not come with the tools required. You need to install the package build-essential for making the package and checkinstall for putting it into your package manager. These can be found on the install CD or in the repositories, searching in Synaptic Package Manager 

I was able to get and install both using the Synaptic Package Manager.

Now you need to create a directory to work in and have sufficient permissions to copy the file there and work on it.

I made directory temp1

Open up under application, accessories, a terminal session.

Make a directory to work in ( I used temp1 for the name)

   Please enter the following commands at the UNIX prompt. Remember, UNIX is
    case sensitive and make sure your root login.

    1) Create a temporary directory:
            sudo mkdir /temp1

    2) Change to the temporary directory:
            cd /temp1

    3) Make sure this directory is writable by you under yourusername. 
         sudo chown yourusername /temp1



Now click on Places at the top of the desk top, 
A window will open, then click on Computer, then Filesystem and you should see the directory you just made.
 
Grab the via driver you extracted to the desk top and drop it into your directory temp1

Now make the name of the folder a little easier to work with 
    Right click and under Properties shorten the name 
    I shortened it to VT6656_Linux

Now change your directory to the file containing the extracted files.

Cd /temp1/VT6656_Linux



Note with this procedure you don’t need to copy from a DOS disk or untar the archive file as refrenced in the Via Txt doc.

Now you are ready to compile and prepare for installation

    4) Type the command sudo checkinstall
it will ask you for your password
You will be asked if you want to put in a description – do so then press – ENTER, press ENTER again on a blank line and it will then give you a screen of default values for building the package.
Leave them and press ENTER to continue

You will see computer generate a number of files 



When it is done you can check the log

I found when I shut down my computer and restarted it loaded and my wireless comes up with the desktop and worked with no problems. 

Hope this helps.


SJC

I'm having problems with the same motherboard and 8.10 64bits version. 

wpa_supplicant gives me errors compiling whatever kernel I use.
about the driver itself I can compile it with 2.6.27.7 and 2.6.27.11 (both versions are available in the repo) and I can load it, but if I do it without first killing the network manager the system freezes.
if I kill it first then everthing is OK, but when I try to use the original wpa_supplicant (since the modified version fails to compile) the systems freezes again.

Any solutions ?


Could you send me a copy of your kernel and wireless driver (as well as the wpa_supplicant) ? since your motherboard is the same, it would be easier for me.

thanks !

---

### Post by spkm on 2009-04-23
This is the error  compiling wpa_supplicant :

> 
root@xbmc:~/wireless/VT6656_Linux_src_v1.19_12_x86/wpa_supplicant/wpa_supplicant-0.5.8# make
cc -MMD -O2 -Wall -g -I. -I../utils -I../hostapd -I/usr/local/ssl/include -DCONFIG_BACKEND_FILE -DCONFIG_DRIVER_WEXT -DCONFIG_DRIVER_VIAWGET -I../../include -I../include -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MD5 -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_OTP -DEAP_LEAP -DEAP_TLV -DIEEE8021X_EAPOL -DEAP_TLS_FUNCS -DEAP_TLS_OPENSSL -DPKCS12_FUNCS -DCONFIG_SMARTCARD -DINTERNAL_SHA256 -DCONFIG_WIRELESS_EXTENSION -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX   -c -o driver_viawget.o driver_viawget.c
In file included from driver_viawget.c:30:
common.h:492: error: conflicting types for &#8216;__be64&#8217;
/usr/include/linux/types.h:159: error: previous declaration of &#8216;__be64&#8217; was here
make: *** [driver_viawget.o] Error 1



---

### Post by SJCBColby on 2009-04-25
SPKM

I believe I am running 32 bit Ubuntu - How can I best send you a copy of the driver, supplicant file and kernal - including how best to copy the driver and supplicant file out - I am fairly new to Linux and learning as I go.

Best Regards

SJC

---

### Post by spkm on 2009-04-26
> **SJCBColby said:**
> SPKM

I believe I am running 32 bit Ubuntu - How can I best send you a copy of the driver, supplicant file and kernal - including how best to copy the driver and supplicant file out - I am fairly new to Linux and learning as I go.

Best Regards

SJC


Thanks ! That would be nice :P

I completely forgot to try it under a 32 bits platform and I'm going to do that. In the meantime, could you please send me a PM with download link  ?

Thank ! :popcorn:

---

### Post by spkm on 2009-04-26
> **spkm said:**
> Thanks ! That would be nice :P

I completely forgot to try it under a 32 bits platform and I'm going to do that. In the meantime, could you please send me a PM with download link  ?

Thank ! :popcorn:


Hi,

I just want to say thanks for the tip. It just solved my problem (it was indeed a 32/64 bits issue).

Everybody who is going to try this be advised that this driver only works with 32 bits systems.

I'm still having problems with the wpa_supplicant (now I can compile but it keeps giving me segmentation fault) but  the original one seems to be 100% compatible with WPA/Tkip.

Thanks !

---

### Post by coskierken on 2009-07-04
I tried your instructions and it failed.  Here is the test from checkinstall:

set -e; for d in driver; do make -C $d install ; done
make[1]: Entering directory `/home/terry/Desktop/temp/VT6656l/driver'
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/terry/Desktop/temp/VT6656l/driver modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/terry/Desktop/temp/VT6656l/driver/iwctl.o
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c: In function ‘iwctl_giwscan’:
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:297: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:297: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:297: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:297: error: too few arguments to function ‘iwe_stream_add_event’
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:304: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:304: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:304: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:304: error: too few arguments to function ‘iwe_stream_add_point’
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:315: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:315: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:315: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:315: error: too few arguments to function ‘iwe_stream_add_event’
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:324: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:324: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:324: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:324: error: too few arguments to function ‘iwe_stream_add_event’
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:332: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:332: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:332: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:332: error: too few arguments to function ‘iwe_stream_add_event’
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:382: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:382: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:382: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:382: error: too few arguments to function ‘iwe_stream_add_event’
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:392: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:392: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:392: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:392: error: too few arguments to function ‘iwe_stream_add_point’
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:404: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:404: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:404: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:404: error: too few arguments to function ‘iwe_stream_add_value’
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:411: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:411: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:411: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:411: error: too few arguments to function ‘iwe_stream_add_value’
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:422: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:422: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:422: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:422: error: too few arguments to function ‘iwe_stream_add_point’
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:429: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:429: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:429: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:429: error: too few arguments to function ‘iwe_stream_add_point’
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:436: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:436: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:436: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/terry/Desktop/temp/VT6656l/driver/iwctl.c:436: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/terry/Desktop/temp/VT6656l/driver/iwctl.o] Error 1
make[2]: *** [_module_/home/terry/Desktop/temp/VT6656l/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/terry/Desktop/temp/VT6656l/driver'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK


Any Help?

---

### Post by coskierken on 2009-07-04
Oh, using on Ubuntu 9.04.

---

### Post by iankellogg on 2009-09-23
Feel the need to update this for everyone that is having issues finding the driver.

[http://www.viaarena.com/Driver/VT6656_Linux_src_v1.19_12_x86.zip](http://www.viaarena.com/Driver/VT6656_Linux_src_v1.19_12_x86.zip)

That is the newest version of the code. Sadly it took me way too long to find this driver.

---

### Post by SJCBColby on 2009-10-15
Good update on the location to for the Via VT6656 driver. iankellogg

Looks like they reorganized their site and made it hard to find.

Here are a few notes on my recent successful install under Jaunty

I just installed it on a new system with Jaunty 9.04 32 bit and it is working well after the first restart - make sure if you were using a hard wire connection for downloads to prep it you disconnect it before you restart. 

I could not find checkinstall or build-essential via the package manager but was able to download following the terminal command in the community documentation on how to download them. 

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

I found this driver is not as effective as the XP driver ( I dual boot one system) at connecting to weaker signals - works well with strong signals.

Off to watch Hulu now working smoothly full screen with "restricted extras" installed on a Zotac ITX 9300 Wifi/ Intel dual core E6300. 

Best of Luck

SJC

---

### Post by Bebop&amp;Rocksteady on 2009-10-18
Works beautifully, thank you. Am a new user to Linux and found the process very easy to follow. Will not have to switch back to windows now.

---

### Post by SJCBColby on 2009-11-13
Glad it helped.  

I am trying it out on 9.10 and running into some issues. 

Works great for me on 9.04 and 8.10

SJC

---

### Post by SJCBColby on 2009-11-28
Gents and fellow Via VT6656 USB wireless users 

- Thanks to some work done over on the launchpad [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/162671](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/162671)
and posted by Joe Clifford the wireless on my Zotac 9300 Wifi using the Via VT6656 USB wireless is now working under 9.10 

Here is what I did:

Downloaded modified driver using Joe's link

[http://launchpadlibrarian.net/35827105/vt6656_stage.ko](http://launchpadlibrarian.net/35827105/vt6656_stage.ko)

Then following Joe's instructions with some modifications:

Open a terminal session

Make a directory** extra **under the Kernel directory 

( Ignore the scott@mini -that is me at my little machine) 
( I will bold the commands I entered) 

scott@mini:~$** sudo mkdir /lib/modules/2.6.31-14-generic/extra**
[sudo] password for scott: 

I then found the directory I made by opening the file browser under 
**Places **on the desk top and exploring down through

**File System**
[B]Lib
Modules 
2.6.31-14-generic
extra[/B]

Then I believe this next adds the modules to the Kernel

scott@mini:~$**sudo insmod /lib/modules/2.6.31-14-generic/extra/vt6656_stage.ko**
[sudo] password for scott: 

Then create dependency file

scott@mini:~$ **sudo depmod -a**

Restart the network manager

scott@mini:~$**sudo service network-manager restart**
network-manager start/running, process 3613
scott@mini:~$ 

At this point my wireless card came up and I was able to direct it to connect to my network which I am writing this on.

Hope this helps - Thanks You Joe Clifford and everyone else that has contributed to make this work.

SJC:D

---

### Post by SJCBColby on 2009-11-29
2 additional items to add to my last post.

The Via wireless would not run automatically when I rebooted initially after installing the driver modules under the 2.6.32.-14 kernal.

I changed the refrences to 2.6.32-15 kernal ( such as which directory the driver module file is placed in) and it now starts up automatically when the PC is rebooted in both -15 or -14?

Maybe someone with more savy can explain.

One thing I did different was to change to the directory I created before proceeding with the rest of the installation:

[B]scott@mini:~$ cd /lib/modules/2.6.31-15-generic/extra 
[/B]

Also before you drag and drop the driver file into the directory you made for it you need to make sure you have permissions for the file folder. 

the terminal command
sudo chown yourname directory name should do it. 

[B]scott@mini:/lib/modules/2.6.31-15-generic/extra$ sudo chown scott  /lib/modules/2.6.31-15-generic/extra 
[/B]

Now it is working properly for me.


Best of luck

---

### Post by nETPOBu4 on 2010-02-05
Hello!
I have same zotac 9300 wifi motherboard. They updated driver to version
1.20.03_x86; Here's download link [http://www.viaarena.com/displaydrivers.aspx?PageID=1&OSID=60&CatID=3760&SubCatID=176](http://www.viaarena.com/displaydrivers.aspx?PageID=1&OSID=60&CatID=3760&SubCatID=176)
This kernel module compiles and works with 32 bit ubuntu.

But it compiles and DOESN'T work with 64bit version of ubuntu.
I get following warining during module build:
```

set -e; for d in driver; do make -C $d ; done
make[1]: Entering directory `/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver'
make -C /lib/modules/2.6.31-18-generic/build SUBDIRS=/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-18-generic'
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/main_usb.o
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/main_usb.c: In function ‘device_release_WPADEV’:
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:820: warning: assignment makes integer from pointer without a cast
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/main_usb.c: In function ‘device_ioctl’:
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:2616: warning: the frame size of 1872 bytes is larger than 1024 bytes
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/card.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/mac.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/baseband.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wctl.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/80211mgr.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wcmd.o
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wcmd.c: In function ‘vRunCommand’:
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wcmd.c:645: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wmgr.o
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wmgr.c: In function ‘s_vMgrRxAssocResponse’:
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wmgr.c:1058: warning: assignment makes integer from pointer without a cast
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wmgr.c: In function ‘s_vMgrRxDisassociation’:
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wmgr.c:1702: warning: assignment makes integer from pointer without a cast
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wmgr.c: In function ‘s_vMgrRxDeauthentication’:
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wmgr.c:1810: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/bssdb.o
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/bssdb.c: In function ‘BSSvSecondCallBack’:
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/bssdb.c:1503: warning: assignment makes integer from pointer without a cast
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/bssdb.c:1547: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/rxtx.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/dpc.o
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/dpc.c: In function ‘RXbBulkInProcessData’:
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/dpc.c:679: warning: assignment makes integer from pointer without a cast
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/dpc.c:841: warning: assignment makes integer from pointer without a cast
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/dpc.c:966: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/power.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/datarate.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/mib.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/rc4.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/tether.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/tcrc.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/ioctl.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/hostap.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wpa.o
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wpa.c: In function ‘WPA_ParseRSN’:
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wpa.c:173: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wpa.c:204: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/key.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/tkip.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/michael.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/rf.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/iwctl.o
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/iwctl.c: In function ‘iwctl_giwaplist’:
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/iwctl.c:1011: warning: the frame size of 1280 bytes is larger than 1024 bytes
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wpactl.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/wpa2.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/aes_ccmp.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/usbpipe.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/channel.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/control.o
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/firmware.o
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/firmware.c: In function ‘FIRMWAREbDownload’:
/home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/firmware.c:815: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/int.o
  LD [M]  /home/dmitry/opt/VT6656_linux_src_v1.20.03_x86/driver/vntwusb.o
  Building modules, stage 2.

```

Does anybody interested in patching it? :)

---

### Post by JoshCorp on 2010-03-17
I tried to install this driver this morning and really didnt have much luck. I followed the earlier set of instructions and it seemed to compile nicely but still no wifi. I guess it is worth mentioning that I am completely new to Linux and this is actually my first post here. 

Also, my boot when from under 20 seconds to several minutes. Any ideas? I considered trying again with the latest set of posted instructions but Im a bit reluctant after the way it affected my boot time. Thanks for any advice!

---

### Post by nETPOBu4 on 2010-03-18
VIA VT6656 driver aviable for download from their site
IS FOR 32bit OS ONLY. You can compile it under 64 bit
ubuntu but it wouldn't work.

---

### Post by JoshCorp on 2010-03-18
Im running the 32 bit. Any ideas why it extended my boot time?

---

### Post by NichoTL on 2010-04-22
Is anyone having issues upon Resume. Personally I need to manually restart network-manager every time I resume from sleep.

(On a side note for those of you who have the Zotac 9300 Wifi, can you get out of sleep mode by clicking on the mouse or pressing a key on the keyboard? It works for me on Win7 but not on Ubuntu, so I know it's not the board.)

---

### Post by NichoTL on 2010-04-24
I have now identified an issue. Not a really major one and I have found some workarounds but they are not very elegant IMO.

Here it is:
I have a Zotac 9300 board with the original wireless card (VT6656 plugged in an internal USB header).
So you can't really plug in or unplug the card when you want. So when you load the vntwusb module for the first time, chances are the card is already plugged in. The driver initialization procedure discovers the card (I can see that in dmesg), the new interface is added, and then the _usb device is reset_. Because network-manager was already up when the reset happened, the interface is not available ("device not ready").
Easy fix:
```
sudo restart network-manager
```Or (variation on the same theme): before you load the module,
```
sudo stop network-manager
```and then,
```
modprobe vntwusb
sudo start network-manager
```It's a one-time thing so that's perfectly manageable.

Now to the problem:
when I put the system to sleep and then restart, I'm back to 'device is not ready' again.
I could very well restart the network-manager job (that fixes it) but 1. I don't want to have to do it every time my system goes to sleep. 2. It's not very elegant, especially if the box ends up being a xbmc HTPC with limited use of keyboard and mouse...
I could also try to script the restart network-manager command and include it in the resume tasks. Not very elegant either.

But first the WHY: why is the device shown as not ready?

(this post is already big enough so I'll continue in another one)

---

### Post by NichoTL on 2010-04-24
(continued from the previous post)

The issue is the following (at least here is my understanding of it):
when the suspend procedure starts, there are a number of scripts being executed:
among those, the ones in /usr/lib/pm-utils/sleep.d
They are executed in alphabetical order when going to sleep/hibernation, and reverse alphabetical order for thaw/resume.
55NetworkManager is the interesting one as it instructs NetworkManager to go to sleep or wakeup. The problem is that when the computer returns from sleep, it needs to somehow reset the (vntwusb module / usb device) pair. which involves again some kind of reloading of the driver when the usb device comes back online:
This is a section of dmesg output:
[ 1952.488981] usb 2-3: USB disconnect, address 10
[ 1952.672022] usb 2-3: new high speed USB device using ehci_hcd and address 11
[ 1952.832142] usb 2-3: configuration #1 chosen from 1 choice
[ 1952.832443] VIA Networking Wireless LAN USB Driver Ver. 1.20.03
[ 1952.832447] Copyright (c) 2004 VIA Networking Technologies, Inc.
[ 1952.948024] usb 2-3: reset high speed USB device using ehci_hcd and address 11

The problem is that network manager wakes up before this is finished (normally before the last line). So the reset happens when the network-manager is already back up, hence the "device not ready" message.

What I did (for the moment) as a workaround, is to insert a line in the 55NetworkManager script:
```
resume_nm()
{
    # Wake up NetworkManager and make it do a new connection
**    sleep 0.5**
    dbus_send --print-reply --system                        \
        --dest=org.freedesktop.NetworkManager \
        /org/freedesktop/NetworkManager       \
        org.freedesktop.NetworkManager.wake 2>&1 > /dev/null
}
```0.5 being the lowest number I could get away with.

This works but I'm not really happy with it. I would like to deal with it with an event: I want to be able to pick the reset message from whichever daemon sends it and then generates an event for the network-manager to instruct it to start managing the new interface.

Anyone?

---

### Post by NichoTL on 2010-04-29
Good news: there is now a vt6656_stage module in 10.04 LTS. And it works out of the box (at least on my Zotac 9300 WiFi miniITX).

And now for the bad news: it doesn't feel complete. I have blacklisted the driver and I'm using vntwusb compiled from the VIA source instead.
Reason is: vt6656_stage  only works on boot. If you suspend, it stops working altogether; and there is no restarting it properly. I mean it starts but doesn't create the interface. Whereas vntwusb will assign a network interface when loaded with modprobe so a simple restart network-manager would get you up and running.

I'd be happy to help with the vt6656-stage driver but I don't know who to talk to and where...
Suggestions?

---

### Post by 1shawn on 2010-11-11
As far as 10.10 goes, the vt6656_stage module still does not seem to resume properly after a suspend.

I had to go back to the VIA driver. However, the VT6656_linux_src_v1.20.03_x86 driver was not compiling on the 10.10 default kernel (2.6.35-22-generic). It was failing with the following errors :
>   CC [M]  VT6656_linux_src_v1.20.03_x86/driver/main_usb.o
VT6656_linux_src_v1.20.03_x86/driver/main_usb.c: In function ‘device_set_multi’:
VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:2086: error: ‘struct net_device’ has no member named ‘mc_count’
VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:2098: error: ‘struct net_device’ has no member named ‘mc_list’
VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:2098: error: ‘struct net_device’ has no member named ‘mc_count’
VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:2099: error: dereferencing pointer to incomplete type
VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:2100: error: dereferencing pointer to incomplete type
make[3]: *** VT6656_linux_src_v1.20.03_x86/driver/main_usb.o] Error 1

Still, I managed to make a few updates to the driver to make it compile again. Here is the diff :
```
diff -ru VT6656_linux_src_v1.20.03_x86.old/driver/main_usb.c VT6656_linux_src_v1.20.03_x86/driver/main_usb.c
--- VT6656_linux_src_v1.20.03_x86.old/driver/main_usb.c	2009-11-13 16:05:21.000000000 +0100
+++ VT6656_linux_src_v1.20.03_x86/driver/main_usb.c	2010-11-11 19:34:35.000000000 +0100
@@ -2060,7 +2060,7 @@
     PSMgmtObject     pMgmt = &(pDevice->sMgmtObj);    
     u32              mc_filter[2];
     int              ii;          
-    struct dev_mc_list  *mclist;
+    struct netdev_hw_addr  *mclist;
     BYTE             pbyData[8] = {0xff,0xff,0xff,0xff,0xff,0xff,0xff,0xff};   
     BYTE             byTmpMode = 0; 
     int              rc;
@@ -2083,7 +2083,7 @@
         // Unconditionally log net taps. 
         pDevice->byRxMode |= (RCR_MULTICAST|RCR_BROADCAST|RCR_UNICAST);
     } 
-    else if ((dev->mc_count > pDevice->multicast_limit) || (dev->flags & IFF_ALLMULTI)) {
+    else if ((netdev_mc_count(dev) > pDevice->multicast_limit) || (dev->flags & IFF_ALLMULTI)) {
         CONTROLnsRequestOut(pDevice,
                             MESSAGE_TYPE_WRITE,
                             MAC_REG_MAR0,
@@ -2095,9 +2095,8 @@
     } 
     else {
         memset(mc_filter, 0, sizeof(mc_filter));
-        for (ii = 0, mclist = dev->mc_list; mclist && ii < dev->mc_count;
-             ii++, mclist = mclist->next) {                
-            int bit_nr = ether_crc(ETH_ALEN, mclist->dmi_addr) >> 26;
+        netdev_for_each_mc_addr(mclist,dev) {
+            int bit_nr = ether_crc(ETH_ALEN, mclist->addr) >> 26;
             mc_filter[bit_nr >> 5] |= cpu_to_le32(1 << (bit_nr & 31));
         }
         for (ii = 0; ii < 4; ii++) {
```

And now it works (I don't guarantee anything, YMMV). Suspend/resume is functional. And I'm happy with it. Better solution would be to fix the vt6656_stage driver, but I don't have the skills.

---


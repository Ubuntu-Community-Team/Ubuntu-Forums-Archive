---
title: "Linksys WMP54G (Ver. 4) Help Kubuntu"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by Matuku on 2007-02-13
I recently installed Kubuntu 6.10 as part of a dual boot on my PC. The problem comes to my wireless network; I bought a Linksys WMP54Gv4 as it was on the list of supported cards but it doesn't want to work.

Although there is only one wireless card, two wireless interfaces show up: wlan0 and wmaster0. Using KNetworkManager and the default installation, the RaLink showed up under the wired connection listing. Then I tried installing ndiswrapper and the drivers included with the card. This results in no network interfaces showing up in KNetworkManager at all, despite "ndiswrapper -l" giving

```
rt61    driver installed, hardware present
```

Please help!!

---

### Post by renzokuken on 2007-02-13
if your using ndiswrapper you may have to blacklist certain kernel modules to get it to work......sadly i dont know which ones for that particular card..........

---

### Post by Matuku on 2007-02-13
OK, have found the following in a readme file about building the driver for the RT61 chipset:
```

=======================================================================
Build Instructions:  
====================

1> $tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.
    
2> $cp Makefile.4  ./Makefile       # [kernel 2.4]
    or
   $cp Makefile.6  ./Makefile       # [kernel 2.6]
    or
   $cp Makefile.RTL865x ./Makefile  #  big endian platform
   
3> [kernel 2.4]
    $chmod 755 Configure
    $make config         # config build linux os version

4> $make all            # compile driver source code

5> $cp rt2561.bin /etc/Wireless/RT61STA/	# copy firmware
   $cp rt2561s.bin /etc/Wireless/RT61STA/
   $cp rt2661.bin /etc/Wireless/RT61STA/

6>  $dos2unix rt61sta.dat
    $cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat       
    # !!!check if it is a binary file before loading !!!  
    
7> $load                
    #[kernel 2.4]
    #    $/sbin/insmod rt61.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt61.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

        
Note: Script functionality:
load            load module to kernel
unload          unload module from kernel
Configure       retrieve linux version 


==============================================================

```
But there's quite a lot in there that I don't understand. For instance the "dos2unix" command at the beginning of part 6 gives the response "command not found"; how do I check if the file is binary for the rest of part 6 and what if i want to use DHCP instead of a given IP address in part 7?

(I'm assuming that I'm using at least kernel 2.6 as I just updated my Kubuntu but I don't know how to check.)

---

### Post by tpg on 2007-02-14
> **Matuku said:**
> For instance the "dos2unix" command at the beginning of part 6 gives the response "command not found"
OK, you just need to install this from the repositories. Just do
```
sudo apt-get install tofrodos
```
"tofrodos" is the package containing dos2unix (you find this out by running "apt-cache search dos2unix"). This program just converts DOS/Windows line endings to Unix line endings (because DOS and Unix have different newline characters).

To check your current kernel version, run
```
uname -r
``` at a terminal.

---

### Post by Matuku on 2007-02-14
OK thanks for that; I can now get to part 7 but again I get stuck; the terminal doesn't like the command "load /sbin/insmod rt61.ko" it returns "bash: load: command not found". Am I missing another package? Or am I simply misinterpreting how to do part 7? Also for the later part of stage 7 do I have to enter a static IP address? What if I want DHCP to assign one?

More help please cos I'm still very lost!

---

### Post by sdide on 2007-02-14
Hey,

I don't think you need to type load. Just do: 
# /sbin/insmod rt61.ko

after that, you can do a 
# dhclient <device_name>

---

### Post by Matuku on 2007-02-14
When you say <device_name> do you mean the name of the wireless card, the router or the network? Sorry to ask but still unsure.

---

### Post by renzokuken on 2007-02-15
type ifconfig, it should list all your network devices.....for example......

ethernet is usually called "eth0"
wireless is usually called "wlan0", or "ra0"

those are the device names.....ifconfig or iwconfig at the terminal should list them

---

### Post by Matuku on 2007-02-15
OK this can't be good; it was in that list before under ra0 but now its disappeared entirely; I tried using ndiswrapper before I found out about this other method and it seems to have removed it from the list. How do I get it back? Can I undo what ndiswrapper has done?

---

### Post by renzokuken on 2007-02-15
yeah you can, but first, make sure the ndiswrapper module is loaded into the kernel

sudo modprobe ndiswrapper

then check ifconfig/iwconfig again

---

### Post by Matuku on 2007-02-16
It appears to be loaded into the kernel; by that I mean that using modprobe made no difference to the readout from ifconfif/iwconfig. How do I go about rectifying what I did with ndiswrapper?

---

### Post by Matuku on 2007-02-19
Bump

---

### Post by renzokuken on 2007-02-19
to uninsall the driver from ndiswrapper use

```
sudo ndiswrapper -e name_of_driver
```

u can also remove ndiswrapper completely using

```
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper
```

---

### Post by Matuku on 2007-02-23
This is really becoming stupid now; I am sure that we installed it but when it enter that I get the output:
```

james@james-desktop:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
james@james-desktop:~$ sudo apt-get remove ndiswrapper
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndiswrapper
james@james-desktop:~$

```

Is there anyway I can list the modules installed so I can see if it is still detected as being there?

---

### Post by MeeMaw on 2007-02-23
OK, I'm not sure about ndiswrapper......   but
I have had my wireless configured on Ubuntu 6.10 using an rt61 driver, but not ndiswrapper.
You should probably open up a terminal and see what is actually listed if you type in 

sudo lspci 

The rt61 may still be there as ra0 and you can configure it.  Post your results here.

Someone else needs to jump in to help you with removal of ndiswrapper.

---

### Post by renzokuken on 2007-02-23
did you compile ndiswrapper from source? if so then apt-get remove wont work, sorry my bad, should have asked.

you can remove it with "make uninstall" if compiled from source, or just delete any directories/files called ndiswrapper

---


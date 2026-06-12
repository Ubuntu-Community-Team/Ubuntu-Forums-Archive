---
title: "Getting wireless pci card to work (VT6655 chipset)"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by h.hittini on 2014-01-09
Hello everyone,
I've been trying to get this WiFi card (vnt6655gma00) to work for a while and I didn't succeed yet; It uses VT6655 chipset
I wanna install the driver on Ubuntu 9.04
I've been trying to use this thread [http://ubuntuforums.org/showthread.php?t=1846809&highlight=vt6655](http://ubuntuforums.org/showthread.php?t=1846809&highlight=vt6655) and this guide [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
When trying to install the Windows XP driver using ndiswrapper and according using this code
```
[I]sudo ndiswrapper -i <DRIVERNAME>.inf
[I]
ndiswrapper -l[/I][/I]
```
The driver is installed but I get the following error; vnwl is the driver I attempted to install BTW
```
lspci: Duplicate entry at /usr/share/misc/pci.ids, line 7976

vnwl : driver installed


```
and I can't proceed to the next step according to the guide (second link)
This command  "locate vt6655_stage.ko" gives me the following output
```

/lib/modules/2.6.34.10-vortex86-sg/kernel/drivers/staging/vt6655/vt6655_stage.ko

```
I guess the driver is installed but not configured correctly, it doesn't show up in "ifconfig"
In addition, I found a Linux version for the driver here [http://www.viaarena.com/Driver/VT6655_Linux_src_v1.20.02_x86.rar](http://www.viaarena.com/Driver/VT6655_Linux_src_v1.20.02_x86.rar)
And these are the instructions but I couldn't follow up
     --------------------------------------------------------------------------------------------------------
1. Compile the source files and it will generate './driver/viawget.ko'.The file 'viawget.ko' 
        will copy to driver installation path.
          make clean
          make install
     2. Check configuration file (/etc/modules.conf or /etc/conf.modules or /etc/modules.conf,it 
        depend on your Linux distribution) for loading kernel modules. Make sure there is the following 
        content in the configuration file, where # is interface number (eg: alias eth0 vntwusb):
          alias eth# vntwusb
3. Install your driver module (If the driver module is in the wrong place, an error message will 
        appear, and say that can't find the driver module):
          insmod viawget.ko
     4. use iwconfig command to check your wireless device interface number
         iwconfig 
     5. Use ifconfig command to assign the IP address up device, where # is network 
        interface number:
         ifconfig eth# up <Ipaddress>
     6. Use iwconfig to setup wireless connection,where xxxx is desired ssid name:
        if authentication type is open and encryption is none:
         iwconfig eth# key off
         iwconfig eth# essid xxxx
        if authentication type is shared and encryption is wep key:
         iwconfig eth# key <key index> <passphrase> restricted
         iwconfig eth# essid xxxx 
        for more iwconfig user manual,please refer to "man iwconfig".
     7. Check if the interface works:
         ping <remote_host_IP>
     8. Disabled WLAN & remove module:
         ifconfig eth# up
         rmmod viawget.ko
--------------------------------------------------------------------------------------------------------
I didn't know how to compile the source files (first step)
Please note that I'm new to Linux
Thanks in advance

---

### Post by chili555 on 2014-01-09
I doubt that anyone is going to be able to help you. You see, you are running an obsolete version of Ubuntu, 9.04. Most of us here try out a fix before we propose it so that we know it works. 

We have made a lot of progress in Ubuntu in the last 4 1/2 years! I suggest you re-install at least 12.04 LTS.

---

### Post by h.hittini on 2014-01-09
The problem is my hardware doesn't support recent versions of Linux
If you have any suggestions I can try them and if they didn't work I will still appreciate your help
Thank you

---

### Post by chili555 on 2014-01-09
> **h.hittini said:**
> The problem is my hardware doesn't support recent versions of Linux
If you have any suggestions I can try them and if they didn't work I will still appreciate your help
Thank youIncluding lubuntu and xubuntu?

---

### Post by h.hittini on 2014-01-10
> **chili555 said:**
> Including lubuntu and xubuntu?

I'm using RB-110 as my computer; it has an i486 CPU, and I will be  installing two custom kernel versions (both are 2.6) in a while
that's why I need an old distro
So I would appreciate if we can troubleshoot the problem I have instead of going around it
Thank you

---

### Post by h.hittini on 2014-02-03
A complete guide A complete guide [http://ubuntuforums.org/showthread.php?t=2203395](http://ubuntuforums.org/showthread.php?t=2203395)

---


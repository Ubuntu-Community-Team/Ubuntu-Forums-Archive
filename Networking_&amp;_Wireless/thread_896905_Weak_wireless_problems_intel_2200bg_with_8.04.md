---
title: "Weak wireless problems intel 2200bg with 8.04"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by jp0213x on 2008-08-21
Hey all,

I am a newbie to Ubuntu, but after doing a fresh install of Ubuntu and apply all the update, I noticed that my signal strength is not all that strong, the signal tends to jump and down and usually stays in the 50% range I don't have this problems when xp is loaded on my laptop, this only seem to be a problem in Ubuntu. The hardware adviser does detect my 2200bg card and will connect to my D link router just not with a good signal. I've searched the forums for this problems, this seems like a common problem some people are having, but I could not locate a real true fix. I am not a real fan of the intel 2200bg cards but does anyone have any suggestions?

Thanks

---

### Post by pytheas22 on 2008-08-21
Please post the output of these commands so that we can figure out what to do:
```

lshw -C Network
lspci -nn
uname -m
dmesg | grep -e iwl -e ipw
```

Also, are you able to get online via ethernet at least temporarily (this is good to know so that we can tailor instructions to your situation)?

---

### Post by jp0213x on 2008-08-21
I am able to get online via ethernet, thats not a problem at all, that works great. For some reason I am having problem getting an internet connection even though it shows connected. Here is the info you are looking for.

*-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 11
       serial: 00:17:08:41:f0:85
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5751m-v3.29a latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:15:00:38:82:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.106 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g



6 (Mar 22 2005) ip=192.168.1.106 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
boopa@boopa-linux-mobile:~$ sudo lspci -nm
00:00.0 "0600" "8086" "2590" -r03 "103c" "0934"
00:01.0 "0604" "8086" "2591" -r03 "" ""
00:1c.0 "0604" "8086" "2660" -r03 "" ""
00:1c.1 "0604" "8086" "2662" -r03 "" ""
00:1d.0 "0c03" "8086" "2658" -r03 "103c" "0934"
00:1d.1 "0c03" "8086" "2659" -r03 "103c" "0934"
00:1d.2 "0c03" "8086" "265a" -r03 "103c" "0934"
00:1d.7 "0c03" "8086" "265c" -r03 -p20 "103c" "0934"
00:1e.0 "0604" "8086" "2448" -rd3 -p01 "" ""
00:1e.2 "0401" "8086" "266e" -r03 "103c" "0934"
00:1e.3 "0703" "8086" "266d" -r03 "103c" "0934"
00:1f.0 "0601" "8086" "2641" -r03 "103c" "0934"
00:1f.1 "0101" "8086" "266f" -r03 -p8a "103c" "0934"
01:00.0 "0300" "1002" "3150" "103c" "0934"
02:04.0 "0280" "8086" "4220" -r05 "103c" "12f5"
02:06.0 "0607" "104c" "8031" "103c" "0934"
02:06.2 "0c00" "104c" "8032" -p10 "103c" "0934"
02:06.3 "0180" "104c" "8033" "103c" "0934"
02:06.4 "0805" "104c" "8034" "103c" "0934"
02:06.5 "0780" "104c" "8035" "103c" "0934"
10:00.0 "0200" "14e4" "167d" -r11 "103c" "0934"


i686


[   25.513439] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   25.513443] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   25.827389] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   30.648466] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)


Let me know if there anymore info you need, thanks!

---

### Post by pytheas22 on 2008-08-21
Thanks for the information.  Please run these commands (make sure you're plugged into ethernet first), which will install ndiswrapper to drive the card (using Windows drivers).  Hopefully that will work better than the ipw2200 driver:
```

sudo apt-get install ndiswrapper*
echo 'blacklist ipw2200' | sudo tee -a /etc/modprobe.d/blacklist
wget http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/16617/eng/12.0.4.0_X_Drivers.zip&agr=&ProductID=1637&DwnldId=16617&strOSs=&OSFullName=&lang=eng
unzip 12.0.4.0_X_Drivers.zip
cd Disk/XP/Drivers/x32
sudo ndiswrapper -i w29n51.inf
```

Now reboot and see if your wireless works better.  If it still doesn't, please post:
```

dmesg | grep -e ipw -e ndis
cat /etc/modprobe.d/blacklist | grep ipw
ndiswrapper -l
lshw -C Network
```

---

### Post by jp0213x on 2008-08-21
> **pytheas22 said:**
> Thanks for the information.  Please run these commands (make sure you're plugged into ethernet first), which will install ndiswrapper to drive the card (using Windows drivers).  Hopefully that will work better than the ipw2200 driver:
```

sudo apt-get install ndiswrapper*
echo 'blacklist ipw2200' | sudo tee -a /etc/modprobe.d/blacklist
wget http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/16617/eng/12.0.4.0_X_Drivers.zip&agr=&ProductID=1637&DwnldId=16617&strOSs=&OSFullName=&lang=eng
unzip 12.0.4.0_X_Drivers.zip
cd Disk/XP/Drivers/x32
sudo ndiswrapper -i w29n51.inf
```

Now reboot and see if your wireless works better.  If it still doesn't, please post:
```

dmesg | grep -e ipw -e ndis
cat /etc/modprobe.d/blacklist | grep ipw
ndiswrapper -l
lshw -C Network
```

I seem to be running into the problems with downloading the drivers, this is what I get below:


 sudo apt-get install ndiswrapper*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ndiswrapper-common for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils for regex 'ndiswrapper*'
Note, selecting ndiswrapper-source for regex 'ndiswrapper*'
Note, selecting ndiswrapper-modules-1.9 for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils-1.9 for regex 'ndiswrapper*'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
boopa@boopa-linux-mobile:~$ echo 'blacklist ipw2200' | sudo tee -a /etc/modprobe.d/blacklist
blacklist ipw2200
boopa@boopa-linux-mobile:~$ wget [http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/16617/eng/12.0.4.0_X_Drivers.zip&agr=&ProductID=1637&DwnldId=16617&strOSs=&OSFullName=&lang=eng](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/16617/eng/12.0.4.0_X_Drivers.zip&agr=&ProductID=1637&DwnldId=16617&strOSs=&OSFullName=&lang=eng)
[1] 10956
--21:59:41--  [http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/16617/eng/12.0.4.0_X_Drivers.zip](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/16617/eng/12.0.4.0_X_Drivers.zip)
           => `confirm.aspx?httpDown=http:%2F%2Fdownloadmirror.intel.com%2F16617%2Feng%2F12.0.4.0_X_Drivers.zip'
Resolving downloadcenter.intel.com... [2] 10957
[3] 10958
[4] 10959
[5] 10960
[6] 10961
192.198.164.161
Connecting to downloadcenter.intel.com|192.198.164.161|:80... [2]   Done                    agr=
[3]   Done                    ProductID=1637
[4]   Done                    DwnldId=16617
[5]   Done                    strOSs=
[6]+  Done                    OSFullName=
boopa@boopa-linux-mobile:~$ unzip 12.0.4.0_X_Drivers.zipconnected.
HTTP request sent, awaiting response... 302 Found
Location: /redirect.htm?aspxerrorpath=/confirm.aspx [following]
--21:59:41--  [http://downloadcenter.intel.com/redirect.htm?aspxerrorpath=/confirm.aspx](http://downloadcenter.intel.com/redirect.htm?aspxerrorpath=/confirm.aspx)
           => `redirect.htm?aspxerrorpath=%2Fconfirm.aspx.4'
Reusing existing connection to downloadcenter.intel.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 58 [text/html]

100%[================================================>] 58            --.--K/s             

21:59:41 (1.49 MB/s) - `redirect.htm?aspxerrorpath=%2Fconfirm.aspx.4' saved [58/58]

Not to go off subject, I had to reboot because of sound problems and I realized that my wireless nic is disable, how do I enable the wireless nic again to do more testing?

---

### Post by gamerteck on 2008-08-22
First remove the drivers ndiswrapper just installed
> 
ndiswrapper -e w29n51.inf


Then remove the blacklist from ipw2200
> 
sudo sed s/"blacklist ipw2200"/ipw2200/g /etc/modprobe.d/blacklist


Reboot

---

### Post by pytheas22 on 2008-08-22
I'm not sure why the drivers don't want to download...maybe wget doesn't like the way that Intel's site serves its files.  I was able to download them manually however and put them on my site, which should work with wget without a problem.  Please try following these steps instead, which should work (don't worry if you already ran some of them successfully once; just run them again):
```

sudo apt-get install ndiswrapper*
echo 'blacklist ipw2200' | sudo tee -a /etc/modprobe.d/blacklist
wget http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz
tar -xzvf Intel*
cd Intel_ipw2200_x32_drivers/
sudo ndiswrapper -i w29n51.inf
```

That should work better.

> Not to go off subject, I had to reboot because of sound problems and I realized that my wireless nic is disable, how do I enable the wireless nic again to do more testing?

As the poster above says, removing ndiswrapper from the blacklist should get you back to where you currently are, using the ipw2200 native driver but with unreliable performance.

---

### Post by jp0213x on 2008-08-22
> **pytheas22 said:**
> I'm not sure why the drivers don't want to download...maybe wget doesn't like the way that Intel's site serves its files.  I was able to download them manually however and put them on my site, which should work with wget without a problem.  Please try following these steps instead, which should work (don't worry if you already ran some of them successfully once; just run them again):
```

sudo apt-get install ndiswrapper*
echo 'blacklist ipw2200' | sudo tee -a /etc/modprobe.d/blacklist
wget http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz
tar -xzvf Intel*
cd Intel_ipw2200_x32_drivers/
sudo ndiswrapper -i w29n51.inf
```

That should work better.



As the poster above says, removing ndiswrapper from the blacklist should get you back to where you currently are, using the ipw2200 native driver but with unreliable performance.


Ok so I rand the cmd line to remove the blacklist and this is what I got.

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

ipw2200
ipw2200
ipw2200
ipw2200
boopa@boopa-linux-mobile:~$


Then I was able to load the drivers by using your cmd

sudo tee -a /etc/modprobe.d/blacklist
blacklist ipw2200
boopa@boopa-linux-mobile:~$ wget [http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz](http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz)
--23:18:46--  [http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz](http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz)
           => `Intel_ipw2200_x32_drivers.tar.gz'
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,210,841 (4.0M) [application/x-gzip]

100%[====================================>] 4,210,841    727.38K/s    ETA 00:00

23:18:53 (683.19 KB/s) - `Intel_ipw2200_x32_drivers.tar.gz' saved [4210841/4210841]

boopa@boopa-linux-mobile:~$ tar -xzvf Intel*
Intel_ipw2200_x32_drivers/
Intel_ipw2200_x32_drivers/NETw2r32.dll
Intel_ipw2200_x32_drivers/iProDifX.dll
Intel_ipw2200_x32_drivers/iProDifX.exe
Intel_ipw2200_x32_drivers/dpinst32.exe
Intel_ipw2200_x32_drivers/NETw5c32.dll
Intel_ipw2200_x32_drivers/NETw5x32.cat
Intel_ipw2200_x32_drivers/NETw5x32.inf
Intel_ipw2200_x32_drivers/NETw5x32.sys
Intel_ipw2200_x32_drivers/NETw5r32.dll
Intel_ipw2200_x32_drivers/NETw2c32.dll
Intel_ipw2200_x32_drivers/w29n50.sys
Intel_ipw2200_x32_drivers/w29n51.cat
Intel_ipw2200_x32_drivers/w29n51.inf
Intel_ipw2200_x32_drivers/w29n51.sys
boopa@boopa-linux-mobile:~$ cd Intel_ipw2200_x32_drivers/
boopa@boopa-linux-mobile:~/Intel_ipw2200_x32_drivers$ sudo ndiswrapper -i w29n51.inf

Now what, my nic is still disabled?

---

### Post by pytheas22 on 2008-08-23
First of all, reboot.  If after rebooting your card is still not working, run:
```

sudo modprobe -r ipw ipw2200 ipw2100
sudo modprobe ndiswrapper
sudo ifconfig wlan0
```

Then wait a few seconds and see if you can connect.  If you still can't, please post the output of:
```

lshw -C Network
dmesg | grep -e ndis -e wlan
iwlist scan
ndiswrapper -l
```

---

### Post by jp0213x on 2008-08-23
> **pytheas22 said:**
> First of all, reboot.  If after rebooting your card is still not working, run:
```

sudo modprobe -r ipw ipw2200 ipw2100
sudo modprobe ndiswrapper
sudo ifconfig wlan0
```

Then wait a few seconds and see if you can connect.  If you still can't, please post the output of:
```

lshw -C Network
dmesg | grep -e ndis -e wlan
iwlist scan
ndiswrapper -l
```

Here are the result from the first cmd

 sudo modprobe -r ipw ipw2200 ipw2100
[sudo] password for boopa: 
boopa@boopa-linux-mobile:~$ sudo modprobe -r ipw ipw2200 ipw2100
[sudo] password for boopa: 
boopa@boopa-linux-mobile:~$ sudo modprobe -r ipw ipw2200 ipw2100
boopa@boopa-linux-mobile:~$ sudo modprobe ndiswrapper
boopa@boopa-linux-mobile:~$ sudo ifconfig wlan0
wlan0: error fetching interface information: Device not found
boopa@boopa-linux-mobile:~$ 

And here is the 2nd

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 11
       serial: 00:17:08:41:f0:85
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5751m-v3.29a latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
boopa@boopa-linux-mobile:~$ dmesg | grep -e ndis -e wlan
[  144.866725] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  144.904917] usbcore: registered new interface driver ndiswrapper
boopa@boopa-linux-mobile:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

boopa@boopa-linux-mobile:~$ ndiswrapper -l

let me know, thanks!

---

### Post by pytheas22 on 2008-08-23
Something weird is going on with ndiswrapper.  Are you sure it's installed?  The output of:
```

ndiswrapper -l
```

(that's a lowercase L) shouldn't be returning a blank line.  Could you try running all of these commands again please and posting all of the output:
```

sudo apt-get install ndiswrapper*
echo 'blacklist ipw2200' | sudo tee -a /etc/modprobe.d/blacklist
wget http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz
tar -xzvf Intel*
cd Intel_ipw2200_x32_drivers/
sudo ndiswrapper -i w29n51.inf
uname -m
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by jp0213x on 2008-08-23
> **pytheas22 said:**
> Something weird is going on with ndiswrapper.  Are you sure it's installed?  The output of:
```

ndiswrapper -l
```

(that's a lowercase L) shouldn't be returning a blank line.  Could you try running all of these commands again please and posting all of the output:
```

sudo apt-get install ndiswrapper*
echo 'blacklist ipw2200' | sudo tee -a /etc/modprobe.d/blacklist
wget http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz
tar -xzvf Intel*
cd Intel_ipw2200_x32_drivers/
sudo ndiswrapper -i w29n51.inf
uname -m
sudo modprobe ndiswrapper
dmesg | grep ndis
```

Nothing appears when I run the first cmd

boopa@boopa-linux-mobile:~$ ndiswrapper -l
boopa@boopa-linux-mobile:~$ ndiswrapper -l



here is the 2nd

boopa@boopa-linux-mobile:~$ sudo apt-get install ndiswrapper*
[sudo] password for boopa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ndiswrapper-common for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils for regex 'ndiswrapper*'
Note, selecting ndiswrapper-source for regex 'ndiswrapper*'
Note, selecting ndiswrapper-modules-1.9 for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils-1.9 for regex 'ndiswrapper*'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by pytheas22 on 2008-08-23
> Nothing appears when I run the first cmd

What do you get from:
```

ndiswrapper -v
ndiswrapper
modinfo ndiswrapper
sudo modprobe --verbose ndiswrapper
```

---

### Post by jp0213x on 2008-08-23
> **pytheas22 said:**
> What do you get from:
```

ndiswrapper -v
ndiswrapper
modinfo ndiswrapper
sudo modprobe --verbose ndiswrapper
```

Here you go


boopa@boopa-linux-mobile:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586 
boopa@boopa-linux-mobile:~$ ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
boopa@boopa-linux-mobile:~$ modinfo ndiswrapper
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
license:        GPL
version:        1.52
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     0B3A678F6DE891D9F074C3E
depends:        usbcore
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)
boopa@boopa-linux-mobile:~$ sudo modprobe --verbose ndiswrapper

---

### Post by pytheas22 on 2008-08-23
Please try running this:

```
mkdir ndiswrapper
cd ndiswrapper
wget http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz
tar -xzvf Intel*
cd Intel_ipw2200_x32_drivers/
sudo ndiswrapper -i w29n51.inf
```

and post all of the output.  I don't know why, but it seems like the Windows driver was never installed into ndiswrapper, even though there was never an error message to that effect.

---

### Post by jp0213x on 2008-08-23
> **pytheas22 said:**
> Please try running this:

```
mkdir ndiswrapper
cd ndiswrapper
wget http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz
tar -xzvf Intel*
cd Intel_ipw2200_x32_drivers/
sudo ndiswrapper -i w29n51.inf
```

and post all of the output.  I don't know why, but it seems like the Windows driver was never installed into ndiswrapper, even though there was never an error message to that effect.

ok done

boopa@boopa-linux-mobile:~/ndiswrapper$ wget [http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz](http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz)
--01:34:08--  [http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz](http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz)
           => `Intel_ipw2200_x32_drivers.tar.gz'
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,210,841 (4.0M) [application/x-gzip]

100%[===============================================================================>] 4,210,841    768.84K/s    ETA 00:00

01:34:14 (706.38 KB/s) - `Intel_ipw2200_x32_drivers.tar.gz' saved [4210841/4210841]

boopa@boopa-linux-mobile:~/ndiswrapper$ tar -xzvf Intel*
Intel_ipw2200_x32_drivers/
Intel_ipw2200_x32_drivers/NETw2r32.dll
Intel_ipw2200_x32_drivers/iProDifX.dll
Intel_ipw2200_x32_drivers/iProDifX.exe
Intel_ipw2200_x32_drivers/dpinst32.exe
Intel_ipw2200_x32_drivers/NETw5c32.dll
Intel_ipw2200_x32_drivers/NETw5x32.cat
Intel_ipw2200_x32_drivers/NETw5x32.inf
Intel_ipw2200_x32_drivers/NETw5x32.sys
Intel_ipw2200_x32_drivers/NETw5r32.dll
Intel_ipw2200_x32_drivers/NETw2c32.dll
Intel_ipw2200_x32_drivers/w29n50.sys
Intel_ipw2200_x32_drivers/w29n51.cat
Intel_ipw2200_x32_drivers/w29n51.inf
Intel_ipw2200_x32_drivers/w29n51.sys
boopa@boopa-linux-mobile:~/ndiswrapper$ cd Intel_ipw2200_x32_drivers/
boopa@boopa-linux-mobile:~/ndiswrapper/Intel_ipw2200_x32_drivers$ sudo ndiswrapper -i w29n51.inf

---

### Post by pytheas22 on 2008-08-23
I don't know what's going on, but I think that there may be a problem with ndiswrapper.  When you run the command:
```

sudo ndiswrapper -i w29n51.inf
```

You should get feedback that looks like:
```

installing driver...
```

but I guess there's none.  The easiest solution, depending on how much you have invested in your system already, might be to reinstall Ubuntu and then run these commands again:
```

sudo apt-get install ndiswrapper*
echo 'blacklist ipw2200' | sudo tee -a /etc/modprobe.d/blacklist
wget http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz
tar -xzvf Intel*
cd Intel_ipw2200_x32_drivers/
sudo ndiswrapper -i w29n51.inf
```

If you don't want to or can't reinstall Ubuntu, however, there are other things we can try, so let me know.  I probably won't  be back till sometime tomorrow.

---

### Post by jp0213x on 2008-08-23
> **pytheas22 said:**
> I don't know what's going on, but I think that there may be a problem with ndiswrapper.  When you run the command:
```

sudo ndiswrapper -i w29n51.inf
```

You should get feedback that looks like:
```

installing driver...
```

but I guess there's none.  The easiest solution, depending on how much you have invested in your system already, might be to reinstall Ubuntu and then run these commands again:
```

sudo apt-get install ndiswrapper*
echo 'blacklist ipw2200' | sudo tee -a /etc/modprobe.d/blacklist
wget http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz
tar -xzvf Intel*
cd Intel_ipw2200_x32_drivers/
sudo ndiswrapper -i w29n51.inf
```

If you don't want to or can't reinstall Ubuntu, however, there are other things we can try, so let me know.  I probably won't  be back till sometime tomorrow.

I got this after I put in my password

installing w29n51 ...
boopa@boopa-linux-mobile:~/ndiswrapper/Intel_ipw2200_x32_drivers$ 
boopa@boopa-linux-mobile:~/ndiswrapper/Intel_ipw2200_x32_drivers$ sudo ndiswrapper -i w29n51.inf
driver w29n51 is already installed
boopa@boopa-linux-mobile:~/ndiswrapper/Intel_ipw2200_x32_drivers$

---

### Post by pytheas22 on 2008-08-23
> 
I got this after I put in my password

Alright, then maybe ndiswrapper is working the way it's supposed to, but I'm not sure because I don't know why "ndiswrapper -l" is returning nothing if it thinks that the driver has been installed.

Please reboot, then run these commands:
```

lsmod | grep ndis
sudo modprobe ndiswrapper
dmesg | grep ndis
ndiswrapper -l
uname -m
```

and post the output.  I'm sorry this is turning out to be so complicated but thanks for sticking with it.

---

### Post by jp0213x on 2008-08-23
> **pytheas22 said:**
> Alright, then maybe ndiswrapper is working the way it's supposed to, but I'm not sure because I don't know why "ndiswrapper -l" is returning nothing if it thinks that the driver has been installed.

Please reboot, then run these commands:
```

lsmod | grep ndis
sudo modprobe ndiswrapper
dmesg | grep ndis
ndiswrapper -l
uname -m
```

and post the output.  I'm sorry this is turning out to be so complicated but thanks for sticking with it.


When I ran the cmd something weird happened. I noticed my wireless light came on which never worked, and my system froze.I had to reboot the pc. But the card still looks disabled. I do an option to edit wireless networks but nic still disabled. I am appreciating the help.


I also ran this again and got:

boopa@boopa-linux-mobile:~$ ndiswrapper -l
w29n51 : driver installed
	device (8086:4220) present (alternate driver: ipw2200)
boopa@boopa-linux-mobile:~$

---

### Post by gamerteck on 2008-08-23
Can you report what the display message reports.

First
> 
sudo /etc/init.d/networking restart


Once it's done do:
> 
dmesg | tail -n 25

and copy it here

---

### Post by jp0213x on 2008-08-23
> **gamerteck said:**
> Can you report what the display message reports.

First


Once it's done do:

and copy it here

Here we go


boopa@boopa-linux-mobile:~$ sudo /etc/init.d/networking restart 
[sudo] password for boopa: 
 * Reconfiguring network interfaces...                                   [ OK ] 
boopa@boopa-linux-mobile:~$ dmesg | tail -n 25 
[   44.374602] swsusp: Basic memory bitmaps freed
[   44.487302] usb 4-6.4.1: USB disconnect, address 4
[   44.630391] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[a5ffffff00508b71]
[   44.738246] usb 4-6.4.1: new low speed USB device using ehci_hcd and address 8
[   44.855378] usb 4-6.4.1: configuration #1 chosen from 1 choice
[   44.864508] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1d.7/usb4/4-6/4-6.4/4-6.4.1/4-6.4.1:1.0/input/input14
[   44.885868] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:1d.7-6.4.1
[   44.898325] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1d.7/usb4/4-6/4-6.4/4-6.4.1/4-6.4.1:1.1/input/input15
[   44.925796] input,hidraw1: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:1d.7-6.4.1
[   45.125582] usb 4-6.4.2: new low speed USB device using ehci_hcd and address 9
[   45.223214] usb 4-6.4.2: configuration #1 chosen from 1 choice
[   45.229905] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb4/4-6/4-6.4/4-6.4.2/4-6.4.2:1.0/input/input16
[   45.257208] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.7-6.4.2
[   50.207340] tg3.c:v3.86 (November 9, 2007)
[   50.207394] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   50.207407] PCI: Setting latency timer of device 0000:10:00.0 to 64
[   50.252068] eth0: Tigon3 [partno(BCM95751M) rev 4101 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:17:08:41:f0:85
[   50.252076] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   50.252079] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   50.434649] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   51.615905] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   53.109372] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[   53.109377] tg3: eth0: Flow control is on for TX and on for RX.
[   53.110742] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  148.710238] eth0: no IPv6 routers present
boopa@boopa-linux-mobile:~$

---

### Post by gamerteck on 2008-08-23
So now your back to using the intel drivers right?

Download the ndiswrapper gui

> 
sudo apt-get install ndisgtk


Then launch it with

> 
gksudo ndisgtk


what is listed there?

---

### Post by jp0213x on 2008-08-23
> **gamerteck said:**
> So now your back to using the intel drivers right?

Download the ndiswrapper gui



Then launch it with



what is listed there?


Here you go


boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ sudo apt-get install ndisgtk 
[sudo] password for boopa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ndisgtk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.9kB of archives.
After this operation, 352kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main ndisgtk 0.8.3-1 [20.9kB]
Fetched 20.9kB in 0s (44.7kB/s)
Selecting previously deselected package ndisgtk.
(Reading database ... 117555 files and directories currently installed.)
Unpacking ndisgtk (from .../ndisgtk_0.8.3-1_i386.deb) ...
Setting up ndisgtk (0.8.3-1) ...

boopa@boopa-linux-mobile:~$ gksudo ndisgtk 


When the gui comes up I see w29n51 listed uder windows driver.

---

### Post by pytheas22 on 2008-08-23
Alright, so the driver should be installed correctly now.  If you run:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
lshw -C Network
dmesg | grep ndis
sudo ifconfig wlan0 up
iwlist scan
```

what do you get?

---

### Post by jp0213x on 2008-08-23
> **pytheas22 said:**
> Alright, so the driver should be installed correctly now.  If you run:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
lshw -C Network
dmesg | grep ndis
sudo ifconfig wlan0 up
iwlist scan
```

what do you get?

Here we go

boopa@boopa-linux-mobile:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ sudo modprobe ndiswrapper
boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 11
       serial: 00:17:08:41:f0:85
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5751m-v3.29a latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 05
       serial: 00:15:00:38:82:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w29n51 driverversion=1.52+Intel,12/19/2007,9.0.4.39 latency=64 maxlatency=24 mingnt=3 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ dmesg | grep ndis
[ 2816.590129] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2816.737139] ndiswrapper: driver w29n51 (Intel,12/19/2007,9.0.4.39) loaded
[ 2816.744697] ndiswrapper: using IRQ 22
[ 2817.432650] usbcore: registered new interface driver ndiswrapper
boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ sudo ifconfig wlan0 up
boopa@boopa-linux-mobile:~$ 
boopa@boopa-linux-mobile:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:F0:EF:90:5A
                    ESSID:"Heath St"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

### Post by pytheas22 on 2008-08-23
Alright, that's good!

You should be able to connect now.  Go to Network Manager (should be in the top-right corner of your screen), left click to view a list of wireless networks, and select the one you want to connect to.  Does it work?

Note that if you reboot, you will probably need to run these commands again to get wireless to work (once we straighten everything out, we can write a script to do this automatically):
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod ssb
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

---

### Post by gamerteck on 2008-08-23
checkout this post.

[http://backports.ubuntuforums.com/showthread.php?t=887960](http://backports.ubuntuforums.com/showthread.php?t=887960)

---

### Post by jp0213x on 2008-08-23
> **pytheas22 said:**
> Alright, that's good!

You should be able to connect now.  Go to Network Manager (should be in the top-right corner of your screen), left click to view a list of wireless networks, and select the one you want to connect to.  Does it work?

Note that if you reboot, you will probably need to run these commands again to get wireless to work (once we straighten everything out, we can write a script to do this automatically):
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod ssb
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

The only cmd that works is the  sudo modprobe ndiswrapper, my wireless light comes on the laptop. All the other cmds error out.
When I try to go to the connection manager and put in my password, the whole password will not fit for WPA. With the wireless activated my system locks up then I have to reboot. To get to the menu I have to pref, administration, and click on networks and unlock it.

---

### Post by pytheas22 on 2008-08-23
> The only cmd that works is the sudo modprobe ndiswrapper, my wireless light comes on the laptop. All the other cmds error out.
When I try to go to the connection manager and put in my password, the whole password will not fit for WPA. With the wireless activated my system locks up then I have to reboot. To get to the menu I have to pref, administration, and click on networks and unlock it.

It's ok if you get errors (like "module XXX does not exist in /proc/modules") running some of those commands.  As long as "sudo modprobe ndiswrapper" works and you can see networks thereafter using the command "iwlist scan," then things should be working.

In the Network box where you enter your password, make sure you have WPA-PSK selected, not WEP.  This is probably why you can't enter your full password there.  You might also want to try enabling Roaming Mode, which will allow you to click on the Network Manager applet to select the network you want to connect to.

Finally, you may want to try using [wicd ]("http://wicd.sourceforge.net")to connect instead of Network Manager; it may work better.

Please let us know if any of this gets you connected.  If not, we can at least get you back to where you were before using the ipw2200 driver.

---


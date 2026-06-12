---
title: "Cannot install On Networks N150 Wifi adapter on Lubuntu 12.04."
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by vladislav4 on 2014-06-11
Hello.

I'm trying to get my wifi adapter running. The exact model of the adapter is here: [https://wikidevi.com/wiki/On_Networks_%28Netgear%29_N150MA](https://wikidevi.com/wiki/On_Networks_%28Netgear%29_N150MA).  I don't know whether or not it works on newer versions of Ubuntu, but  my laptop can only run 12.04 because of the pesky SiS 671 graphics  chipset.


  The adapter is recognized by the computer as 0846:9042 NetGear, Inc., and that's pretty much it. It runs on Windows just fine.


  I've tried installing the RTL8192CU drivers from the Realtek site,  didn't work. Also tried installing the Windows drivers on the  installation CD via ndiswrapper, it showed "invalid driver".

Here is the wireless-info.txt from the script in the sticky:

```


########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


##### kernel #####


Linux v-laptop 3.2.0-64-generic #97-Ubuntu SMP Wed Jun 4 22:03:48 UTC 2014 i686 i686 i386 GNU/Linux


##### lspci #####


00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
    Subsystem: Elitegroup Computer Systems Device [1019:5a00]
    Kernel driver in use: sis190


##### lsusb #####


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9042 NetGear, Inc. 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 003 Device 002: ID 046d:c05b Logitech, Inc. M-U0004 810-001317 [B110 Optical USB Mouse]


##### PCMCIA Card Info #####


##### rfkill #####


##### iw reg get #####


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #####


nameserver 127.0.0.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sis190
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             85.253.0.2
    DNS:             85.253.0.130


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


##### iwlist channel #####


##### lsmod #####


##### modinfo #####


##### modules #####


lp


##### blacklist #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


##### udev rules #####


# PCI device 0x1039:/sys/devices/pci0000:00/0000:00:04.0 (sis190)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #####


########## wireless info END ############



```


  Any help would be appreciated.

---

### Post by chili555 on 2014-06-11
The people in the back room are laughing and taking bets; they are betting that I'll try to get this seemingly unworkable device working. Then they all have side bets that I won't actually get it working! Then there seems to be a separate pool on whether this reaches 100 replies! I had to reply just to get them to shut up!!

First, determine your kernel version:

```
uname -r
```
If your kernel is -pae, then do:

```
sudo apt-get install linux-backports-modules-cw-3.12-precise-generic-pae
```
If not, then do:

```
sudo apt-get install linux-backports-modules-cw-3.12-precise-generic
```
Then do:

```
sudo modprobe rtl8192cu
echo 0846 9042 | sudo tee /sys/bus/usb/drivers/rtl8192cu/new_id
```
Your wireless should be working. If it is working, we'll have a further step to do to make it persistent.

---

### Post by mörgæs on 2014-06-11
I don't like to interrupt a thread in which Chili is giving advice but my bet is that the computer does run a live boot of Lubuntu 14.04 (but not 12.10 and 13.*)

If that's the case I recommend a fresh install in stead of 12.04 which is out of support.

---

### Post by chili555 on 2014-06-11
I'm always willing to take all the help I can get, mörgæs! Thanks.

---

### Post by vladislav4 on 2014-06-12
> **chili555 said:**
> The people in the back room are laughing and taking bets; they are betting that I'll try to get this seemingly unworkable device working. Then they all have side bets that I won't actually get it working! Then there seems to be a separate pool on whether this reaches 100 replies! I had to reply just to get them to shut up!!

First, determine your kernel version:

```
uname -r
```
If your kernel is -pae, then do:

```
sudo apt-get install linux-backports-modules-cw-3.12-precise-generic-pae
```
If not, then do:

```
sudo apt-get install linux-backports-modules-cw-3.12-precise-generic
```
Then do:

```
sudo modprobe rtl8192cu
echo 0846 9042 | sudo tee /sys/bus/usb/drivers/rtl8192cu/new_id
```
Your wireless should be working. If it is working, we'll have a further step to do to make it persistent.

Thanks for the reply, but it didn't work. After the last command, the system became very slow until I rebooted. Tried it three times, it was the same.

> **mörgæs said:**
> I don't like to interrupt a thread in which Chili is giving advice but my bet is that the computer does run a live boot of Lubuntu 14.04 (but not 12.10 and 13.*)

If that's the case I recommend a fresh install in stead of 12.04 which is out of support.

I can't upgrade, unfortunately. My graphics card drivers can only be run on 12.04, according to this site [https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis).

---

### Post by chili555 on 2014-06-12
> After the last command, the system became very slow until I rebooted. Perhaps we can troubleshoot why. First, be sure the ethernet is disconnected as you run the test. Next, run the two commands and then:```
cat /var/log/syslog | tail -n50  >  syslog.txt
```Now unload the module:```
sudo modprobe -r rtl8192cu
```Find the file syslog.txt in your user directory and hook up the ethernet so you can post it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/) Give us the link in your reply.

---

### Post by vladislav4 on 2014-06-12
[http://paste.ubuntu.com/7634088/](http://paste.ubuntu.com/7634088/)

Edit:

Oops, the first link is where I didn't run the 2 commands in your previous post, this is probably the one you were asking for: [http://paste.ubuntu.com/7634183/](http://paste.ubuntu.com/7634183/).

---

### Post by mörgæs on 2014-06-12
> **vladislav4 said:**
> 
I can't upgrade, unfortunately. My graphics card drivers can only be run on 12.04, according to this site [https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis).

I would trust a live boot experiment more than a web page which might be outdated. I can't promise that it works for the 671 but I know for a fact that 14.04 works for some of its close relatives like 661/662.

---

### Post by vladislav4 on 2014-06-12
> **mörgæs said:**
> I would trust a live boot experiment more than a web page which might be outdated. I can't promise that it works for the 671 but I know for a fact that 14.04 works for some of its close relatives like 661/662.

After reading your thread [http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422) I tried installing both 13.10 and 14.04, none of them allowed my resolution to go over 640x480, I've searched everywhere for fixes, and none of them worked. The graphics card on this 8 year old laptop is an ancient ***Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)***, so the only fix I found that worked was only for 12.04.

---

### Post by mörgæs on 2014-06-12
14.04 could likely have been brought to a better resolution by using VESA drivers. 

If you want something in the 12.04 family I suggest Bodhi Linux or LXLE which are supported through 2017 (unlike Lubuntu 12.04). 

Anyway, enough about that. Over to you, Chili.

---

### Post by vladislav4 on 2014-06-13
[http://askubuntu.com/questions/246236/compile-and-install-rtl8192cu-driver](http://askubuntu.com/questions/246236/compile-and-install-rtl8192cu-driver)

Did a fresh install, followed these instructions and it started working, but the system is experiencing some sort of slowdown. I can see how choppy the cursor movement is until I unload the rtl8192cu module. The laptop fan is also working faster when the module is loaded. Strangely enough, the CPU and memory usage numbers are very low.

Here is the syslog.txt: [http://paste.ubuntu.com/7641183/](http://paste.ubuntu.com/7641183/)

If it's impossible to determine why the system is slowing down, can you please tell me how to create scripts that enable and disable Wifi through loading and unloading of the rtl8192 module, so I can switch it on only when I need it?

---

### Post by chili555 on 2014-06-14
> After the last command, the system became very slow until I rebooted. Tried it three times, it was the same.Frankly, after examining the pastebin, I see no reason that would cause a slowdown. On the other hand, if it only occurs when you issue the two rtl8192cu commands, then it is probably useless to continue.

I suggest our next steps be ndiswrapper. With a working connection:```
sudo apt-get install nidiswrapper-common ndiswrapper-utils-1.9 
```Do you have the Windows XP .inf and .sys files available? If not, I'll be happy to see if I can assist you to find them.

---

### Post by kurt18947 on 2014-06-14
> **vladislav4 said:**
> [http://askubuntu.com/questions/246236/compile-and-install-rtl8192cu-driver](http://askubuntu.com/questions/246236/compile-and-install-rtl8192cu-driver)

Did a fresh install, followed these instructions and it started working, but the system is experiencing some sort of slowdown. I can see how choppy the cursor movement is until I unload the rtl8192cu module. The laptop fan is also working faster when the module is loaded. Strangely enough, the CPU and memory usage numbers are very low.

Here is the syslog.txt: [http://paste.ubuntu.com/7641183/](http://paste.ubuntu.com/7641183/)

If it's impossible to determine why the system is slowing down, can you please tell me how to create scripts that enable and disable Wifi through loading and unloading of the rtl8192 module, so I can switch it on only when I need it?

If I may butt in here, are you seeing the rtl8192cu module in use?  Did you try the patched driver mentioned in the last post of the AskUbuntu thread? I'm using that patch on a Thinkpad with an Edimax EW-7811Un/RTL8188CUs chipset and also a generic RTL-8192CU chipset based device, both work very well.  When I type "lsmod",  I see "8192cu", not "rtl8192cu".  I think though I'm not certain that "rtl8192" says you're still using the included flawed driver, not the patched driver.  I've not tried that particular fix on 12.04, only on 13.10 and14.04.  If you don't have ready access, here's the fix I use:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

---


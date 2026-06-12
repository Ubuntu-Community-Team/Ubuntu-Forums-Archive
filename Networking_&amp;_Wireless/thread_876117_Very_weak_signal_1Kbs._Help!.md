---
title: "Very weak signal 1Kb/s. Help!"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by gleble on 2008-07-31
I  connect my laptop through the router which is running the computer I'm writing this on. On my laptop my wireless light is on. I can't connect to any websites. When I go to Network Tools/ Devices State is active. Both transmitted and received are both about 1Kb/s. I cannot ping this computer.  What is wrong?

---

### Post by pytheas22 on 2008-07-31
Please post the output of:
```

lshw -C Network
lspci
```

so that we can figure out what kind of wireless card you have and how to solve the problem.

Also are you able to connect to a wireless network without a problem using Network Manager?

---

### Post by gleble on 2008-07-31
neil@neil-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:36:c8:83:b9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:36:c8:83:b9  
          inet addr:169.254.8.132  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1467 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1467 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:75670 (73.8 KB)  TX bytes:75670 (73.8 KB) 




 lshw -C network 

  *-network               
       description: Ethernet interface 
       product: 88E8038 PCI-E Fast Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 14 
       serial: 00:16:36:c8:83:b9 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes 
  *-network 
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 3 
       bus info: pci@0000:0a:03.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master

---

### Post by gleble on 2008-08-01
More info. Please if anyone understands HELP

neil@neil-laptop:~$ iwlist scan 
```
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan0     No scan results 

```

---

### Post by gleble on 2008-08-01
In case it helps, I use an Acer 3680 and am running Hardy.

---

### Post by gleble on 2008-08-01
Sorry to bump but I'm going away and I need my laptop

---

### Post by PmDematagoda on 2008-08-01
> **gleble said:**
> Sorry to bump but I'm going away and I need my laptop

I had this similar problem with a desktop once, and the culprit turned out to be a defective ethernet card. Are you sure that the ethernet card is not defective?

---

### Post by gleble on 2008-08-01
It's not ethernet it's wireless I'm worried about.

---

### Post by gleble on 2008-08-01
Tried conneccting an ethernet cable, no luck but the RS232 lights up just like the wireless light. They  are both strangely constant.

---

### Post by pytheas22 on 2008-08-01
Sorry to not respond faster, but first of all, try this and see if it helps (it will switch you to an alternate driver for your card).  If you can get online using the ethernet, that would be the best way to do this, because you will need to download a little bit of stuff and I don't know if the speed will be too slow using the wireless (moving really close to your router, like within a few feet, may improve the speed).  If you can't get ethernet connected and the wireless is too slow, let me know and I'll give you instructions for doing this using an offline install.
```

sudo -s
apt-get install bcm43xx-fwcutter
```

At some point now you should be asked if you want to download some firmware automatically; say yes.  Then continue with these commands:
```

sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
sed 's/blacklist bcm43xx//' /etc/modprobe.d/blacklist
```

Then reboot.  If your wireless doesn't work already, type:
```

sudo modprobe bcm43xx
sudo ifconfig eth1 up
```

See if it works better then.  If it still doesn't work, see my next post.

---

### Post by pytheas22 on 2008-08-01
If my first post doesn't help, then the next thing to try is using ndiswrapper.  I am assuming for these instructions that 1) you are using a 32-bit Linux kernel and 2) you can get online with ethernet.  If either assumption is incorrect, please let me know so that I can change the instructions accordingly.

First, go to System>Administration>Software Sources and under the Ubuntu Software tab, make sure that all repositories are enabled.  Then run:

```
sudo -s
echo 'blacklist bcm43xx' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper* cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
ndiswrapper -i bcmwl5.inf
ndiswrapper -l
depmod -a
modprobe ndiswrapper
cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
rmmod ndiswrapper
rmmod bcm43xx
modprobe ndiswrapper
ifconfig wlan0 up
```

If your card doesn't work already, reboot and see if it does now.

By the way, this is all based on the very nice (if a bit outdated) tutorial for Broadcom cards and ndiswrapper at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) .

---

### Post by gleble on 2008-08-01
I,m afraid I can't get internet. Is is possible to download the driver to a Windows machine then copy it to the laptop?

---

### Post by pytheas22 on 2008-08-01
> I,m afraid I can't get internet. Is is possible to download the driver to a Windows machine then copy it to the laptop?

Yes; in that case things will be a little harder, but they will still work.  First, on a computer that has Internet, click [here]("http://ubuntu.secs.oakland.edu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb") to download the bcm43xx-fwcutter package.  Also download this [file]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o").  Transfer both of those files to your Ubuntu system and save them on the desktop there.

Then on Ubuntu, run these commands:
```

cd ~/Desktop
sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
sed 's/blacklist bcm43xx//' /etc/modprobe.d/blacklist
dpkg --install bcm43xx*
cd /lib/firmware
bcm43xx-fwcutter wl_apsta-3.130.20.0.o
```

then, so long as you haven't gotten any error messages, reboot and hopefully the wireless will work.  If it still doesn't, I can give instructions for using the ndiswrapper method without being online.  But bcm43xx (the method in this post) should work for your card, according to what I'm reading on the Internet.

---

### Post by gleble on 2008-08-02
OK tried that
```
neil@neil-laptop:~$ cd Desktop 
neil@neil-laptop:~/Desktop$ sudo dpkg --install bcm43xx* 
sudo: unable to resolve host neil-laptop 
dpkg-split: error reading bcm43xx-fwcutter-006: Is a directory 
dpkg: error processing bcm43xx-fwcutter-006 (--install): 
 subprocess dpkg-split returned error exit status 2 
(Reading database ... 106225 files and directories currently installed.) 
Preparing to replace bcm43xx-fwcutter 1:006-3 (using bcm43xx-fwcutter_006-3_i386.deb) ... 
Unpacking replacement bcm43xx-fwcutter ... 
Setting up bcm43xx-fwcutter (1:006-3) ... 
--10:27:57--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o 
           => `wl_apsta.o' 
Resolving downloads.openwrt.org... failed: Name or service not known. 
dpkg: error processing bcm43xx-fwcutter (--install): 
 subprocess post-installation script returned error exit status 1 
Errors were encountered while processing: 
 bcm43xx-fwcutter-006 
 bcm43xx-fwcutter 
neil@neil-laptop:~/Desktop$ 
```

It tries to download wl_apsta-3.130.20.0.o but obviously can't. It's on the desktop, how can I make  bcm43xx-fwcutter use it

---

### Post by gleble on 2008-08-02
Now when I run
```
cd ~/Desktop
sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
sed 's/blacklist bcm43xx//' /etc/modprobe.d/blacklist
dpkg --install bcm43xx*
cd /lib/firmware
bcm43xx-fwcutter wl_apsta-3.130.20.0.o
```

I get

```
neil@neil-laptop:~$ cd ~/Desktop 
neil@neil-laptop:~/Desktop$ sudo -s 
sudo: unable to resolve host neil-laptop 
root@neil-laptop:~/Desktop# echo 'blacklist b43' >> /etc/modprobe.d/blacklist 
root@neil-laptop:~/Desktop# echo 'blacklist ssb' >> /etc/modprobe.d/blacklist 
root@neil-laptop:~/Desktop# echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist 
root@neil-laptop:~/Desktop# echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist 
root@neil-laptop:~/Desktop# sed 's/blacklist bcm43xx//' /etc/modprobe.d/blacklist 
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


# most apps now use garmin usb driver directly (Ubuntu: #114565) 
blacklist garmin_gps 

# replaced by asus-laptop (Ubuntu: #184721) 
blacklist asus_acpi 

blacklist b43 
blacklist ssb 
blacklist b43legacy 
blacklist b43 ssb 
blacklist b43 
blacklist ssb 
blacklist b43legacy 
blacklist b43 ssb 
blacklist b43 
blacklist ssb 
blacklist b43legacy 
blacklist b43 ssb 
blacklist b43 
blacklist ssb 
blacklist b43legacy 
blacklist b43 ssb 
root@neil-laptop:~/Desktop# dpkg --install bcm43xx* 
dpkg-split: error reading bcm43xx-fwcutter-006: Is a directory 
dpkg: error processing bcm43xx-fwcutter-006 (--install): 
 subprocess dpkg-split returned error exit status 2 
(Reading database ... 106225 files and directories currently installed.) 
Preparing to replace bcm43xx-fwcutter 1:006-3 (using bcm43xx-fwcutter_006-3_i386.deb) ... 
Unpacking replacement bcm43xx-fwcutter ... 
Setting up bcm43xx-fwcutter (1:006-3) ... 

Errors were encountered while processing: 
 bcm43xx-fwcutter-006 
root@neil-laptop:~/Desktop# cd /lib/firmware 
root@neil-laptop:/lib/firmware# bcm43xx-fwcutter wl_apsta-3.130.20.0.o 

  filename   :  wl_apsta.o 
  version    :  3.130.20.0 
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3 
  microcodes :  2 4 5 11 
  pcms       :  4 5 

  microcode  :  2 
  revision   :  0x0127 
  patchlevel :  0x000e 
  date       :  2005-04-18 
  time       :  02:36:27 

  microcode  :  4 
  revision   :  0x0127 
  patchlevel :  0x000e 
  date       :  2005-04-18 
  time       :  02:36:27 

  microcode  :  5 
  revision   :  0x0127 
  patchlevel :  0x000e 
  date       :  2005-04-18 
  time       :  02:36:27 
 
  microcode  :  11 
  revision   :  0x0127 
  patchlevel :  0x000e 
  date       :  2005-04-18 
  time       :  02:36:27 

extracting bcm43xx_microcode2.fw ... 
extracting bcm43xx_microcode4.fw ... 
extracting bcm43xx_microcode5.fw ... 
extracting bcm43xx_microcode11.fw ... 
extracting bcm43xx_pcm4.fw ... 
extracting bcm43xx_pcm5.fw ... 
extracting bcm43xx_initval01.fw ... 
extracting bcm43xx_initval02.fw ... 
extracting bcm43xx_initval03.fw ... 
extracting bcm43xx_initval04.fw ... 
extracting bcm43xx_initval05.fw ... 
extracting bcm43xx_initval06.fw ... 
extracting bcm43xx_initval07.fw ... 
extracting bcm43xx_initval08.fw ... 
extracting bcm43xx_initval09.fw ... 
extracting bcm43xx_initval10.fw ... 
root@neil-laptop:/lib/firmware# 
```

Completely overwhelmed and confused. Please help

---

### Post by gleble on 2008-08-02
Desperate bump

---

### Post by pytheas22 on 2008-08-02
Sorry, I've been away.  What is the output of:

```
ls /lib/firmware
lshw -C Network
dmesg | grep bcm43xx
```

And if you run:
```

sudo modprobe bcm43xx
sudo ifconfig eth1 up
```

does the Internet work?

---

### Post by gleble on 2008-08-02
```
neil@neil-laptop:~$ ls /lib/firmware 
2.6.24-19-generic   b43-fwcutter-011.tar.bz2      bcm43xx_microcode11.fw 
a0g0bsinitvals2.fw  b43legacy                     bcm43xx_microcode2.fw 
a0g0bsinitvals5.fw  bcm43xx-fwcutter_006-3_i386   bcm43xx_microcode4.fw 
a0g0initvals2.fw    bcm43xx-fwcutter-006.tar.bz2  bcm43xx_microcode5.fw 
a0g0initvals5.fw    bcm43xx_initval01.fw          bcm43xx_pcm4.fw 
a0g1bsinitvals5.fw  bcm43xx_initval02.fw          bcm43xx_pcm5.fw 
a0g1initvals5.fw    bcm43xx_initval03.fw          pcm4.fw 
b0g0bsinitvals2.fw  bcm43xx_initval04.fw          pcm5.fw 
b0g0bsinitvals5.fw  bcm43xx_initval05.fw          ucode11.fw 
b0g0initvals2.fw    bcm43xx_initval06.fw          ucode2.fw 
b0g0initvals5.fw    bcm43xx_initval07.fw          ucode4.fw 
b43                 bcm43xx_initval08.fw          ucode5.fw 
b43-all-fw.zip      bcm43xx_initval09.fw          wl_apsta-3.130.20.0.o 
b43-fwcutter-011    bcm43xx_initval10.fw 
neil@neil-laptop:~$ 

neil@neil-laptop:~$ sudo modprobe bcm43xx 
neil@neil-laptop:~$ sudo ifconfig eth1 up 
eth1: ERROR while getting interface flags: No such device 
neil@neil-laptop:~$ 
```

---

### Post by pytheas22 on 2008-08-02
Alright, try:
```

sudo rmmod b43
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod bcm43xx
sudo modprobe bcm43xx
sudo ifconfig eth1 up
```

If you get any errors, post them please.  If it still doesn't work at this point, post:
```

lshw -C Network
```

---

### Post by gleble on 2008-08-02
```
neil@neil-laptop:~$ sudo rmmod b43 
[sudo] password for neil: 
ERROR: Module b43 does not exist in /proc/modules 
neil@neil-laptop:~$ sudo rmmod b43 
ERROR: Module b43 does not exist in /proc/modules 
neil@neil-laptop:~$ sudo rmmod b43legacy 
ERROR: Module b43legacy does not exist in /proc/modules 
neil@neil-laptop:~$ sudo rmmod ssb 
ERROR: Module ssb is in use by b44 
neil@neil-laptop:~$ sudo rmmod bcm43xx 
neil@neil-laptop:~$ sudo modprobe bcm43xx 
neil@neil-laptop:~$ sudo ifconfig eth1 up 
eth1: ERROR while getting interface flags: No such device 
neil@neil-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: 88E8038 PCI-E Fast Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 14 
       serial: 00:16:36:c8:83:b9 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.54 latency=0 module=sky2 multicast=yes 
  *-network 
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 3 
       bus info: pci@0000:0a:03.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
neil@neil-laptop:~$ 
```

---

### Post by pytheas22 on 2008-08-02
ok, I know what's going on, this should solve it:
```

sudo -s
echo 'blacklist b44' >> /etc/modprobe.d/blacklist
sudo rmmod b44
sudo rmmod ssb
sudo rmmod bcm43xx
sudo modprobe bcm43xx
sudo ifconfig eth1 up
```

Now you should have wireless.  Each time you restart your computer, you may need to run those commands again for the wireless to work, for now--you can apply the fix permanently but I don't have time to explain right now.  I'll be back in a couple of hours; if you're still here then I'll explain.  But this should at least make the wireless work.

---

### Post by gleble on 2008-08-02
You won't believe this but still no luck. Back where I started, wireless light is on but glows constantly whereas it should flicker
```
neil@neil-laptop:~$ sudo -s 
[sudo] password for neil: 
root@neil-laptop:~# sudo -s 
root@neil-laptop:~# echo 'blacklist b44' >> /etc/modprobe.d/blacklist 
root@neil-laptop:~# sudo rmmod b44 
root@neil-laptop:~# sudo rmmod ssb 
root@neil-laptop:~# sudo rmmod bcm43xx 
ERROR: Module bcm43xx does not exist in /proc/modules 
root@neil-laptop:~# sudo modprobe bcm43xx 
root@neil-laptop:~# sudo ifconfig eth1 up 
root@neil-laptop:~# lshw -C network 
  *-network               
       description: Ethernet interface 
       product: 88E8038 PCI-E Fast Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 14 
       serial: 00:16:36:c8:83:b9 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.54 latency=0 link=no module=sky2 multicast=yes port=twisted pair 
  *-network 
       description: Wireless interface 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 3 
       bus info: pci@0000:0a:03.0 
       logical name: eth1 
       version: 02 
       serial: 00:19:7d:34:6b:2e 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master ethernet physical wireless 
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.24-19-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g 
root@neil-laptop:~# 
```

---

### Post by pytheas22 on 2008-08-02
It's using the new driver, at least.  Do you see any wireless networks?  What is the output of:
```

iwlist scan
dmesg | grep bcm43xx
```

Also, how much longer do you have to solve this before you leave?

---

### Post by gleble on 2008-08-02
```
neil@neil-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

eth1      No scan results 

neil@neil-laptop:~$ dmesg | grep bcm43xx 
[   90.825623] bcm43xx driver 
[   91.024164] bcm43xx: Radio disabled by hardware 
neil@neil-laptop:~$ 
```

---

### Post by pytheas22 on 2008-08-02
> [   90.825623] bcm43xx driver 
[   91.024164] bcm43xx: Radio disabled by hardware 

Something weird is going on...can you check your BIOS to make sure that your wireless card is enabled?  Also on some laptops there's a physical switch that you need to turn on to make the wireless work, or you need to press some function keys...do you ever have to do something like that?

---

### Post by gleble on 2008-08-02
Can't find Broadcom in the BIOS. I assume it should be under the information tab. There is a switch but whichever way it is the light stays on.

---

### Post by pytheas22 on 2008-08-02
Try turning the switch back and forth...the light may be on regardless of whether or not the switch is actually on.  If the card is really turned on, then:
```

dmesg | grep bcm43xx
```

should say something about radio being enabled.
```

iwlist eth1 scan
```

should give you a list of wireless networks.

If you don't make any progress, please post the total output of:
```

dmesg
```

(it will be very long, but please post it all).

---

### Post by pytheas22 on 2008-08-02
Also, try running:
```

sudo ifconfig eth1 up
```

a few times, and then "dmesg | grep bcm43xx" to see if it mentions the radio being enabled.  Any luck?

---

### Post by gleble on 2008-08-02
There,s dmseg in full . The eth1 scan is at the bottom there are 2 networks , mine is the WANADOO-C994.

```
[    0.000000] Enabling fast FPU save and restore... done. 
[    0.000000] Enabling unmasked SIMD FPU exception support... done. 
[    0.000000] Initializing CPU#0 
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes) 
[    0.000000] Detected 1600.082 MHz processor. 
[   15.621954] Console: colour VGA+ 80x25 
[   15.621959] console [tty0] enabled 
[   15.622112] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
[   15.622314] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
[   15.633210] Memory: 498048k/514624k available (2177k kernel code, 15892k reserved, 1006k data, 368k init, 0k highmem) 
[   15.633219] virtual kernel memory layout: 
[   15.633220]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB) 
[   15.633221]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[   15.633223]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB) 
[   15.633224]     lowmem  : 0xc0000000 - 0xdf690000   ( 502 MB) 
[   15.633225]       .init : 0xc0421000 - 0xc047d000   ( 368 kB) 
[   15.633227]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB) 
[   15.633228]       .text : 0xc0100000 - 0xc0320474   (2177 kB) 
[   15.633232] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[   15.633270] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1 
[   15.633427] hpet clockevent registered 
[   15.713311] Calibrating delay using timer specific routine.. 3203.89 BogoMIPS (lpj=6407786) 
[   15.713332] Security Framework initialized 
[   15.713340] SELinux:  Disabled at boot. 
[   15.713355] AppArmor: AppArmor initialized 
[   15.713360] Failure registering capabilities with primary security module. 
[   15.713368] Mount-cache hash table entries: 512 
[   15.713492] Initializing cgroup subsys ns 
[   15.713498] Initializing cgroup subsys cpuacct 
[   15.713510] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000 00000000 
[   15.713518] monitor/mwait feature present. 
[   15.713520] using mwait in idle threads. 
[   15.713525] CPU: L1 I cache: 32K, L1 D cache: 32K 
[   15.713528] CPU: L2 cache: 1024K 
[   15.713531] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000 00000000 
[   15.713541] Compat vDSO mapped to ffffe000. 
[   15.713555] Checking 'hlt' instruction... OK. 
[   15.729736] SMP alternatives: switching to UP code 
[   15.731659] Freeing SMP alternatives: 11k freed 
[   15.731772] Early unpacking initramfs... done 
[   16.111765] ACPI: Core revision 20070126 
[   16.111852] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found. 
[   16.116565] CPU0: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz stepping 08 
[   16.116591] Total of 1 processors activated (3203.89 BogoMIPS). 
[   16.116798] ENABLING IO-APIC IRQs 
[   16.116992] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
[   16.264513] Brought up 1 CPUs 
[   16.264538] CPU0 attaching sched-domain: 
[   16.264541]  domain 0: span 01 
[   16.264543]   groups: 01 
[   16.264722] net_namespace: 64 bytes 
[   16.264732] Booting paravirtualized kernel on bare hardware 
[   16.265219] Time: 21:28:10  Date: 08/02/08 
[   16.265245] NET: Registered protocol family 16 
[   16.265452] EISA bus registered 
[   16.265459] ACPI: bus type pci registered 
[   16.290646] PCI: PCI BIOS revision 2.10 entry at 0xfd6c2, last bus=12 
[   16.290650] PCI: Using configuration type 1 
[   16.290662] Setting up standard PCI resources 
[   16.292672] ACPI: EC: Look up EC in DSDT 
[   16.294929] ACPI: BIOS _OSI(Linux) query ignored via DMI 
[   16.294932] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org 
[   16.891589] ACPI: Interpreter enabled 
[   16.891593] ACPI: (supports S0 S3 S4 S5) 
[   16.891607] ACPI: Using IOAPIC for interrupt routing 
[   16.913399] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62 
[   16.913404] ACPI: EC: driver started in poll mode 
[   16.913447] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[   16.914282] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO 
[   16.914287] PCI quirk: region 1180-11bf claimed by ICH6 GPIO 
[   16.915128] PCI: Transparent bridge - 0000:00:1e.0 
[   16.915221] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[   16.915570] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT] 
[   16.915709] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT] 
[   16.915844] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT] 
[   16.915995] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT] 
[   16.920786] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11 
[   16.920897] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15) 
[   16.921004] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15) 
[   16.921110] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10 
[   16.921217] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15) 
[   16.921323] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15) 
[   16.921429] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15) 
[   16.921535] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15) 
[   16.921675] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   16.921710] pnp: PnP ACPI init 
[   16.921717] ACPI: bus type pnp registered 
[   16.924548] pnp: PnP ACPI: found 9 devices 
[   16.924551] ACPI: ACPI bus type pnp unregistered 
[   16.924555] PnPBIOS: Disabled by ACPI PNP 
[   16.924849] PCI: Using ACPI for IRQ routing 
[   16.924852] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[   16.924856] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0 
[   16.924859] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0 
[   16.924861] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0 
[   16.924864] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1 
[   16.924866] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1 
[   16.924869] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1 
[   16.924871] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2 
[   16.924874] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2 
[   16.924876] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2 
[   16.967390] NET: Registered protocol family 8 
[   16.967393] NET: Registered protocol family 20 
[   16.967430] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0 
[   16.967435] hpet0: 3 64-bit timers, 14318180 Hz 
[   16.968481] AppArmor: AppArmor Filesystem Enabled 
[   16.971376] Time: tsc clocksource has been installed. 
[   16.971395] Switched to high resolution mode on CPU 0 
[   16.979335] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved 
[   16.979339] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved 
[   16.979342] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved 
[   16.979346] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved 
[   16.979349] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved 
[   16.979353] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved 
[   16.979356] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved 
[   16.979359] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved 
[   16.979367] system 00:03: iomem range 0xfed00000-0xfed003ff could not be reserved 
[   16.979375] system 00:05: ioport range 0x800-0x80f has been reserved 
[   16.979378] system 00:05: ioport range 0x1000-0x107f has been reserved 
[   16.979381] system 00:05: ioport range 0x1180-0x11bf has been reserved 
[   16.979384] system 00:05: ioport range 0x1600-0x166f has been reserved 
[   16.979387] system 00:05: ioport range 0xfe10-0xfe11 has been reserved 
[   16.979390] system 00:05: ioport range 0xfe00-0xfe00 has been reserved 
[   17.009825] PCI: Bridge: 0000:00:1c.0 
[   17.009830]   IO window: 2000-2fff 
[   17.009836]   MEM window: 30000000-300fffff 
[   17.009840]   PREFETCH window: disabled. 
[   17.009846] PCI: Bridge: 0000:00:1c.1 
[   17.009848]   IO window: disabled. 
[   17.009854]   MEM window: disabled. 
[   17.009858]   PREFETCH window: disabled. 
[   17.009864] PCI: Bridge: 0000:00:1c.2 
[   17.009865]   IO window: disabled. 
[   17.009871]   MEM window: disabled. 
[   17.009875]   PREFETCH window: disabled. 
[   17.009885] PCI: Bus 11, cardbus bridge: 0000:0a:09.0 
[   17.009887]   IO window: 00001400-000014ff 
[   17.009893]   IO window: 00001c00-00001cff 
[   17.009898]   PREFETCH window: 34000000-37ffffff 
[   17.009904]   MEM window: 38000000-3bffffff 
[   17.009909] PCI: Bridge: 0000:00:1e.0 
[   17.009910]   IO window: disabled. 
[   17.009916]   MEM window: d0100000-d01fffff 
[   17.009921]   PREFETCH window: disabled. 
[   17.009954] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003) 
[   17.009962] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16 
[   17.009971] PCI: Setting latency timer of device 0000:00:1c.0 to 64 
[   17.009996] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17 
[   17.010004] PCI: Setting latency timer of device 0000:00:1c.1 to 64 
[   17.010028] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18 
[   17.010035] PCI: Setting latency timer of device 0000:00:1c.2 to 64 
[   17.010047] PCI: Enabling device 0000:00:1e.0 (0004 -> 0006) 
[   17.010054] PCI: Setting latency timer of device 0000:00:1e.0 to 64 
[   17.010071] PCI: Enabling device 0000:0a:09.0 (0000 -> 0003) 
[   17.010077] ACPI: PCI Interrupt 0000:0a:09.0[A] -> GSI 20 (level, low) -> IRQ 19 
[   17.010095] NET: Registered protocol family 2 
[   17.047258] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
[   17.047460] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
[   17.047564] TCP bind hash table entries: 16384 (order: 5, 131072 bytes) 
[   17.047668] TCP: Hash tables configured (established 16384 bind 16384) 
[   17.047671] TCP reno registered 
[   17.059299] checking if image is initramfs... it is 
[   17.804359] Freeing initrd memory: 7319k freed 
[   17.804557] Simple Boot Flag at 0x36 set to 0x1 
[   17.805109] audit: initializing netlink socket (disabled) 
[   17.805126] audit(1217712492.064:1): initialized 
[   17.807275] VFS: Disk quotas dquot_6.5.1 
[   17.807352] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[   17.807501] io scheduler noop registered 
[   17.807504] io scheduler anticipatory registered 
[   17.807506] io scheduler deadline registered 
[   17.807518] io scheduler cfq registered (default) 
[   17.807531] Boot video device is 0000:00:02.0 
[   17.807745] PCI: Setting latency timer of device 0000:00:1c.0 to 64 
[   17.807804] assign_interrupt_mode Found MSI capability 
[   17.807856] Allocate Port Service[0000:00:1c.0:pcie00] 
[   17.807895] Allocate Port Service[0000:00:1c.0:pcie02] 
[   17.808000] PCI: Setting latency timer of device 0000:00:1c.1 to 64 
[   17.808058] assign_interrupt_mode Found MSI capability 
[   17.808104] Allocate Port Service[0000:00:1c.1:pcie00] 
[   17.808142] Allocate Port Service[0000:00:1c.1:pcie02] 
[   17.808248] PCI: Setting latency timer of device 0000:00:1c.2 to 64 
[   17.808306] assign_interrupt_mode Found MSI capability 
[   17.808352] Allocate Port Service[0000:00:1c.2:pcie00] 
[   17.808389] Allocate Port Service[0000:00:1c.2:pcie02] 
[   17.808677] isapnp: Scanning for PnP cards... 
[   18.162492] isapnp: No Plug & Play device found 
[   18.194053] Real Time Clock Driver v1.12ac 
[   18.194300] hpet_resources: 0xfed00000 is busy 
[   18.194332] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   18.195616] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   18.195691] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[   18.195798] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[   18.210234] i8042.c: Detected active multiplexing controller, rev 1.1. 
[   18.216688] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   18.216692] serio: i8042 AUX0 port at 0x60,0x64 irq 12 
[   18.216695] serio: i8042 AUX1 port at 0x60,0x64 irq 12 
[   18.216698] serio: i8042 AUX2 port at 0x60,0x64 irq 12 
[   18.216700] serio: i8042 AUX3 port at 0x60,0x64 irq 12 
[   18.225436] mice: PS/2 mouse device common for all mice 
[   18.225554] EISA: Probing bus 0 at eisa.0 
[   18.225562] Cannot allocate resource for EISA slot 1 
[   18.225564] Cannot allocate resource for EISA slot 2 
[   18.225591] EISA: Detected 0 cards. 
[   18.225595] cpuidle: using governor ladder 
[   18.225597] cpuidle: using governor menu 
[   18.225695] NET: Registered protocol family 1 
[   18.225723] Using IPI No-Shortcut mode 
[   18.225758] registered taskstats version 1 
[   18.225864]   Magic number: 4:316:499 
[   18.225988] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[   18.225991] EDD information not available. 
[   18.226171] Freeing unused kernel memory: 368k freed 
[   18.269338] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[   19.465418] fuse init (API version 7.9) 
[   19.486857] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3]) 
[   19.486865] ACPI: Processor [CPU0] (supports 8 throttling states) 
[   19.486880] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126] 
[   19.490717] ACPI: Thermal Zone [THRM] (68 C) 
[   19.501796] ACPI: EC: non-query interrupt received, switching to interrupt mode 
[   20.226327] usbcore: registered new interface driver usbfs 
[   20.226354] usbcore: registered new interface driver hub 
[   20.230357] usbcore: registered new device driver usb 
[   20.254230] USB Universal Host Controller Interface driver v3.0 
[   20.254303] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20 
[   20.254316] PCI: Setting latency timer of device 0000:00:1d.0 to 64 
[   20.254321] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[   20.254590] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
[   20.254628] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820 
[   20.254778] usb usb1: configuration #1 chosen from 1 choice 
[   20.254803] hub 1-0:1.0: USB hub found 
[   20.254809] hub 1-0:1.0: 2 ports detected 
[   20.327084] SCSI subsystem initialized 
[   20.358146] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21 
[   20.358160] PCI: Setting latency timer of device 0000:00:1d.1 to 64 
[   20.358165] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[   20.358191] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
[   20.358227] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001840 
[   20.358349] usb usb2: configuration #1 chosen from 1 choice 
[   20.358378] hub 2-0:1.0: USB hub found 
[   20.358384] hub 2-0:1.0: 2 ports detected 
[   20.409597] libata version 3.00 loaded. 
[   20.462009] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18 
[   20.462023] PCI: Setting latency timer of device 0000:00:1d.2 to 64 
[   20.462028] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[   20.462057] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
[   20.462093] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860 
[   20.462211] usb usb3: configuration #1 chosen from 1 choice 
[   20.462235] hub 3-0:1.0: USB hub found 
[   20.462241] hub 3-0:1.0: 2 ports detected 
[   20.565825] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16 
[   20.565840] PCI: Setting latency timer of device 0000:00:1d.3 to 64 
[   20.565845] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
[   20.565870] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4 
[   20.565907] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880 
[   20.566029] usb usb4: configuration #1 chosen from 1 choice 
[   20.566054] hub 4-0:1.0: USB hub found 
[   20.566060] hub 4-0:1.0: 2 ports detected 
[   20.669884] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20 
[   20.669901] PCI: Setting latency timer of device 0000:00:1d.7 to 64 
[   20.669906] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[   20.669933] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5 
[   20.673847] ehci_hcd 0000:00:1d.7: debug port 1 
[   20.673854] PCI: cache line size of 32 is not supported by device 0000:00:1d.7 
[   20.673862] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0544000 
[   20.689509] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   20.689657] usb usb5: configuration #1 chosen from 1 choice 
[   20.689682] hub 5-0:1.0: USB hub found 
[   20.689689] hub 5-0:1.0: 8 ports detected 
[   20.793535] ACPI: PCI Interrupt 0000:0a:03.0[A] -> GSI 18 (level, low) -> IRQ 18 
[   20.813372] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243) 
[   20.813382] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243) 
[   20.813390] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243) 
[   20.813398] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243) 
[   20.853329] ssb: Sonics Silicon Backplane found on PCI device 0000:0a:03.0 
[   20.853506] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21 
[   20.853546] PCI: Setting latency timer of device 0000:00:1f.2 to 64 
[   20.853560] ACPI: PCI interrupt for device 0000:00:1f.2 disabled 
[   20.858452] ata_piix 0000:00:1f.2: version 2.12 
[   20.858460] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ] 
[   21.013030] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21 
[   21.013076] PCI: Setting latency timer of device 0000:00:1f.2 to 64 
[   21.013396] scsi0 : ata_piix 
[   21.013599] scsi1 : ata_piix 
[   21.013742] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14 
[   21.013745] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15 
[   21.068991] usb 5-7: new high speed USB device using ehci_hcd and address 2 
[   21.177259] ata1.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC70P, max UDMA/100 
[   21.177264] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[   21.193241] ata1.00: configured for UDMA/100 
[   21.208667] usb 5-7: configuration #1 chosen from 1 choice 
[   21.232659] Clocksource tsc unstable (delta = -219873762 ns) 
[   21.244097] Time: hpet clocksource has been installed. 
[   21.388071] ata2.00: ATAPI: Optiarc DVD RW AD-7530A, EX31, max UDMA/33 
[   21.414641] ata2.00: configured for UDMA/33 
[   21.414770] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5 
[   21.415642] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530A  EX31 PQ: 0 ANSI: 5 
[   21.429517] Driver 'sd' needs updating - please use bus_type methods 
[   21.429612] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[   21.429626] sd 0:0:0:0: [sda] Write Protect is off 
[   21.429629] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   21.429647] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   21.429697] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[   21.429707] sd 0:0:0:0: [sda] Write Protect is off 
[   21.429710] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   21.429726] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   21.429731]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[   21.451956]  sda1 sda2 < sda5 sda6 > sda3 
[   21.482863] sd 0:0:0:0: [sda] Attached SCSI disk 
[   21.488959] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[   21.488980] sr 1:0:0:0: Attached scsi generic sg1 type 5 
[   21.491363] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray 
[   21.491369] Uniform CD-ROM driver Revision: 3.20 
[   21.491426] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[   21.752082] Attempting manual resume 
[   21.752086] swsusp: Resume From Partition 8:5 
[   21.752088] PM: Checking swsusp image. 
[   21.752297] PM: Resume from disk failed. 
[   21.806288] kjournald starting.  Commit interval 5 seconds 
[   21.806302] EXT3-fs: mounted filesystem with ordered data mode. 
[   28.669029] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   28.719263] nf_conntrack version 0.5.0 (8192 buckets, 32768 max) 
[   30.070328] Linux agpgart interface v0.102 
[   30.234730] agpgart: Detected an Intel 945GM Chipset. 
[   30.235057] agpgart: Detected 7932K stolen memory. 
[   30.251299] agpgart: AGP aperture is 256M @ 0xc0000000 
[   30.307075] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   30.358495] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   30.742678] input: Power Button (FF) as /devices/virtual/input/input2 
[   30.757731] ACPI: Power Button (FF) [PWRF] 
[   30.757847] input: Lid Switch as /devices/virtual/input/input3 
[   30.757950] ACPI: Lid Switch [LID] 
[   30.758017] input: Power Button (CM) as /devices/virtual/input/input4 
[   30.769726] ACPI: Power Button (CM) [PWRB] 
[   30.769856] input: Sleep Button (CM) as /devices/virtual/input/input5 
[   30.785702] ACPI: Sleep Button (CM) [SLPB] 
[   30.877701] ACPI: AC Adapter [ACAD] (off-line) 
[   31.068886] ACPI: Battery Slot [BAT1] (battery present) 
[   31.068969] ACPI: WMI-Acer: Mapper loaded 
[   31.378577] PCI: Enabling device 0000:02:00.0 (0000 -> 0003) 
[   31.378588] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16 
[   31.378604] PCI: Setting latency timer of device 0000:02:00.0 to 64 
[   31.378642] sky2 0000:02:00.0: v1.20 addr 0x30000000 irq 16 Yukon-FE (0xb7) rev 1 
[   31.379148] sky2 eth0: addr 00:16:36:c8:83:b9 
[   31.729104] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6 
[   31.744172] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no) 
[   32.403264] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22 
[   32.403299] PCI: Setting latency timer of device 0000:00:1b.0 to 64 
[   33.229839] iTCO_vendor_support: vendor-support=0 
[   33.265295] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007) 
[   33.265863] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060) 
[   33.269752] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[   33.337823] input: PC Speaker as /devices/platform/pcspkr/input/input7 
[   33.413540] intel_rng: FWH not detected 
[   33.953229] Yenta: CardBus bridge found at 0000:0a:09.0 [1025:0110] 
[   33.953255] Yenta: Using CSCINT to route CSC interrupts to PCI 
[   33.953257] Yenta: Routing CardBus interrupts to PCI 
[   33.953263] Yenta TI: socket 0000:0a:09.0, mfunc 0x01321b22, devctl 0x66 
[   34.185130] Yenta: ISA IRQ mask 0x0cf8, PCI irq 19 
[   34.185136] Socket status: 30000006 
[   34.185139] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e 
[   34.185146] pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd01fffff 
[   34.292149] ACPI: PCI Interrupt 0000:0a:09.2[A] -> GSI 20 (level, low) -> IRQ 19 
[   34.721536] acer_acpi: Acer Laptop ACPI Extras version 0.11.1 
[   34.721545] acer_acpi: Detected Acer WMID interface 
[   34.911859] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000 
[   34.968737] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8 
[   35.894081] sky2 eth0: enabling interface 
[   36.809881] cs: IO port probe 0x100-0x3af: clean. 
[   36.811914] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7 
[   36.812775] cs: IO port probe 0x820-0x8ff: clean. 
[   36.813474] cs: IO port probe 0xc00-0xcf7: clean. 
[   36.814343] cs: IO port probe 0xa00-0xaff: clean. 
[   37.209999] lp: driver loaded but no devices found 
[   37.253591] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[   37.338093] usbcore: registered new interface driver ndiswrapper 
[   37.458079] NET: Registered protocol family 10 
[   37.458354] lo: Disabled Privacy Extensions 
[   37.458824] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   37.467646] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k 
[   37.498807] EXT3 FS on sda1, internal journal 
[   38.847251] ACPI: ACPI Dock Station Driver 
[   39.952858] apm: BIOS not found. 
[   40.113154] ppdev: user-space parallel port driver 
[   40.207645] audit(1217712515.330:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5159 profile="/usr/sbin/cupsd" namespace="default" 
[   40.931547] vboxdrv: Trying to deactivate the NMI watchdog permanently... 
[   40.931554] vboxdrv: Successfully done. 
[   40.931556] vboxdrv: Found 1 processor cores. 
[   40.931559] vboxdrv: fAsync=0 u64DiffCores=1. 
[   40.932151] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'. 
[   40.932155] vboxdrv: Successfully loaded version 1.6.2 (interface 0x00070002). 
[   48.265110] Bluetooth: Core ver 2.11 
[   48.265884] NET: Registered protocol family 31 
[   48.265889] Bluetooth: HCI device and connection manager initialized 
[   48.265894] Bluetooth: HCI socket layer initialized 
[   48.293180] Bluetooth: L2CAP ver 2.9 
[   48.293185] Bluetooth: L2CAP socket layer initialized 
[   48.357050] Bluetooth: RFCOMM socket layer initialized 
[   48.357277] Bluetooth: RFCOMM TTY layer initialized 
[   48.357281] Bluetooth: RFCOMM ver 1.8 
[   50.925584] [drm] Initialized drm 1.1.0 20060810 
[   50.929013] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16 
[   50.929022] PCI: Setting latency timer of device 0000:00:02.0 to 64 
[   50.929107] [drm] Initialized i915 1.6.0 20060119 on minor 0 
[   78.287353] UDF-fs: No VRS found 
[   78.312708] ISO 9660 Extensions: Microsoft Joliet Level 3 
[   78.361289] ISO 9660 Extensions: RRIP_1991A 
[   89.635532] ACPI: PCI interrupt for device 0000:0a:03.0 disabled 
[   90.512341] ieee80211_crypt: registered algorithm 'NULL' 
[   90.517077] ieee80211: 802.11 data/management/control stack, git-1.1.13 
[   90.517083] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com> 
[   90.567341] bcm43xx driver 
[   90.568526] ACPI: PCI Interrupt 0000:0a:03.0[A] -> GSI 18 (level, low) -> IRQ 18 
[   90.765862] bcm43xx: Radio disabled by hardware 
[   90.947175] ADDRCONF(NETDEV_UP): eth1: link is not ready 
[   93.572798] bcm43xx: Radio hardware status changed to enabled 
[   97.688018] bcm43xx: Radio hardware status changed to disabled 
[   97.712943] bcm43xx: Radio hardware status changed to enabled 
[   98.147037] bcm43xx: Radio hardware status changed to disabled 
[   98.227576] bcm43xx: Radio hardware status changed to enabled 
[  593.637838] bcm43xx: Radio hardware status changed to disabled 
[  594.045212] bcm43xx: Radio hardware status changed to enabled 
[  594.163490] bcm43xx: Radio hardware status changed to disabled 
[  594.246327] bcm43xx: Radio hardware status changed to enabled 
[  594.353159] bcm43xx: Radio hardware status changed to disabled 
[  594.588192] bcm43xx: Radio hardware status changed to enabled 
[  594.669723] bcm43xx: Radio hardware status changed to disabled 
[  594.721982] bcm43xx: Radio hardware status changed to enabled 
[  594.735877] bcm43xx: Radio hardware status changed to disabled 
[  595.349938] bcm43xx: Radio hardware status changed to enabled 
root@neil-laptop:~# 

eth1      Scan completed : 
          Cell 01 - Address: 00:0E:9B:A9:73:50 
                    ESSID:"WANADOO-C994" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Frequency:2.412 GHz (Channel 1) 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality=88/100  Signal level=-45 dBm  Noise level=-70 dBm 
                    Extra: Last beacon: 444ms ago 
          Cell 02 - Address: 00:18:F6:79:F5:2D 
                    ESSID:"BTHomeHub-A75B" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Frequency:2.462 GHz (Channel 11) 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality=68/100  Signal level=-72 dBm  Noise level=-72 dBm 
                    Extra: Last beacon: 124ms ago 

```

---

### Post by pytheas22 on 2008-08-02
It looks like the card should be working now.> 

[   90.947175] ADDRCONF(NETDEV_UP): eth1: link is not ready 
[   93.572798] bcm43xx: Radio hardware status changed to enabled 
[   97.688018] bcm43xx: Radio hardware status changed to disabled 
[   97.712943] bcm43xx: Radio hardware status changed to enabled 
[   98.147037] bcm43xx: Radio hardware status changed to disabled 
[   98.227576] bcm43xx: Radio hardware status changed to enabled 
[  593.637838] bcm43xx: Radio hardware status changed to disabled 
[  594.045212] bcm43xx: Radio hardware status changed to enabled 
[  594.163490] bcm43xx: Radio hardware status changed to disabled 
[  594.246327] bcm43xx: Radio hardware status changed to enabled 
[  594.353159] bcm43xx: Radio hardware status changed to disabled 
[  594.588192] bcm43xx: Radio hardware status changed to enabled 
[  594.669723] bcm43xx: Radio hardware status changed to disabled 
[  594.721982] bcm43xx: Radio hardware status changed to enabled 
[  594.735877] bcm43xx: Radio hardware status changed to disabled 
[  595.349938] bcm43xx: Radio hardware status changed to enabled 

I assume that all of this back-and-forth with the radio status was the result either of flipping the switch on and off, or using "ifconfig eth1 up."  Were you doing that?

And since "iwlist scan" returns results, then the card is seeing your network without a problem (which it was not doing when the radio was disabled).

So please go to Network Manager (the applet in the top-right corner of the screen; it looks like two computer monitors) and left-click.  It should list wireless networks.  If none is listed, try flipping the wireless switch again or running "sudo ifconfig eth1 up," wait a few seconds, and see if networks are visible then.  Then try to connect to your network.  Does it work?

---

### Post by gleble on 2008-08-02
WANADOO-C994 is there and has a tickked box. The wep key is filled in correctly and dhcp is selected

---

### Post by pytheas22 on 2008-08-02
> WANADOO-C994 is there and has a tickked box. The wep key is filled in correctly and dhcp is selected

I'm not sure what you mean.  If you're using the utility at System>Administration>Network, just switch it back to roaming mode, and use Network Manager to connect normally (by selecting the network name from the list).  Otherwise, please post a screenshot, because I'm not sure what you're trying to do to connect.

---

### Post by pytheas22 on 2008-08-02
Also, you could try connecting from the command line with:
```

sudo dhclient -r eth1
sudo iwconfig eth1 mode managed channel 1 essid "WANADOO-C994" key "YOUR WEP KEY HERE, IN QUOTES"
sudo dhclient eth1
```

---

### Post by gleble on 2008-08-02
Enabling roaming mode doesn't produce any results. I've always connected by filling in the details.

---

### Post by gleble on 2008-08-02
I have to get to bed now. Long journey tomorrow. If I get near a computer tomorrow we can continue.

---

### Post by pytheas22 on 2008-08-02
> Enabling roaming mode doesn't produce any results. I've always connected by filling in the details. 

Are you sure that the wireless switch was in the right position when you were in roaming mode?  If you get scan results from the command:
```

iwlist eth1 scan
```

then Network Manager should list networks when the card is in roaming mode, and you should be able to connect to them.

Also, what output do you get if you try connecting from the command line?

---

### Post by pytheas22 on 2008-08-02
> I have to get to bed now. Long journey tomorrow. If I get near a computer tomorrow we can continue.

Alright, but just in case you don't get to a computer, by all indications, everything should be working now.  I would just try playing with a few settings--move the switch back and forth, and see if roaming mode gives you better results (I really think it will), or try to connect using the command-line.

Either way, please let us know if the changes ended up working.

---

### Post by gleble on 2008-08-03
Surely this should be working but it isn't
```
@neil-laptop:~$ sudo -s 
[sudo] password for neil: 
root@neil-lneilaptop:~# sudo dhclient -r  eth1 
There is already a pid file /var/run/dhclient.pid with pid 134519072 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/eth1/00:19:7d:34:6b:2e 
Sending on   LPF/eth1/00:19:7d:34:6b:2e 
Sending on   Socket/fallback 
DHCPRELEASE on eth1 to 192.168.1.1 port 67 
root@neil-laptop:~#  sudo iwconfig eth1 mode managed channel 1 essid "WANADOO-C994" key "9E1EBAC6FF5A2582F337A0AA3E" 
root@neil-laptop:~# sudo dhclient eth1 
There is already a pid file /var/run/dhclient.pid with pid 134519072 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/eth1/00:19:7d:34:6b:2e 
Sending on   LPF/eth1/00:19:7d:34:6b:2e 
Sending on   Socket/fallback 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 
DHCPOFFER of 192.168.1.108 from 192.168.1.1 
DHCPREQUEST of 192.168.1.108 on eth1 to 255.255.255.255 port 67 
DHCPACK of 192.168.1.108 from 192.168.1.1 
bound to 192.168.1.108 -- renewal in 42066 seconds. 
root@neil-laptop:~# 
```

---

### Post by pytheas22 on 2008-08-03
> DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 
DHCPOFFER of 192.168.1.108 from 192.168.1.1 
DHCPREQUEST of 192.168.1.108 on eth1 to 255.255.255.255 port 67 
DHCPACK of 192.168.1.108 from 192.168.1.1 
bound to 192.168.1.108 -- renewal in 42066 seconds.

Yeah, it should definitely work now...that stuff above is exactly what you wanted to see.  What still isn't working?

If you still can't load websites after getting an IP, it could be a DNS problem.  Try putting just these numbers in your browser address bar:
```

64.233.187.99
91.189.94.250
```

Do they bring you to a website?

Also, can you ping your router:
```

ping 192.168.1.1
```

and what is the output of:

```
cat /etc/resolv.conf
```

---

### Post by gleble on 2008-08-12
See attachment: View of System/Networking
Can't ping 192.168.1.1
cat /etc/resolv.conf
gives nameserver 192.168.1.1
other strange things: it worked once on anoter wireless system. When I came home it worked,then it didn't, then it did, now it doesn't work atall

---

### Post by pytheas22 on 2008-08-12
> See attachment: View of System/Networking
Can't ping 192.168.1.1
cat /etc/resolv.conf
gives nameserver 192.168.1.1
other strange things: it worked once on anoter wireless system. When I came home it worked,then it didn't, then it did, now it doesn't work atall

Are you sure that you have an IP address?  If you do, the output of "ifconfig eth1" would look similar to:

```
eth1      Link encap:Ethernet  HWaddr 00:19:e0:67:8a:f1  
          **inet addr:192.168.1.3**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e0ff:fe67:8af1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1004027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1074844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1031774559 (983.9 MB)  TX bytes:96244032 (91.7 MB)

```

If you have an IP but it still doesn't work, have you tried enabling roaming mode yet?  I know I've mentioned this before, but I really think there's a good chance that it would solve the problem.

You might also want to see if you have better luck using a different connection manager, like [wicd]("http://wicd.sourceforge.net").

---

### Post by gleble on 2008-08-12
```
neil@neil-laptop:~$ ifconfig eth1 
eth1      Link encap:Ethernet  HWaddr 00:19:7d:34:6b:2e  
          inet addr:192.168.1.54  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::219:7dff:fe34:6b2e/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:119 errors:0 dropped:113 overruns:0 frame:0 
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:18482 (18.0 KB)  TX bytes:6269 (6.1 KB) 
          Interrupt:18 Base address:0x4000 
```
So it has an IP address. And it's it's transmitting and receiving a bit?
I'll try wicd if you've run out of ideas

---

### Post by gleble on 2008-08-12
Success, I used wicd and got a connection easily. Thank you very much for all your advice. At least I learnt alot about wireless and we got there in the end.

---

### Post by pytheas22 on 2008-08-12
Glad to hear that it finally works.  I should probably have suggested wicd much earlier.  Sometimes Network Manager does dumb things; wicd seems often to get people connected where NM fails or causes strange behavior.

---


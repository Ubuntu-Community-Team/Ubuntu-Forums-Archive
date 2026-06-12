---
title: "Realtek not allowing wired internet connection"
date: 2014-12-31
forum: Networking &amp; Wireless
---

### Post by Barsoom88 on 2014-12-31
I am currently running ubuntu 12.04 LDS that does not allow intenet connection. WiFi works perfectly here is the code 
```
*-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000 [Condor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 00
       serial: 74:e5:0b:04:bc:be
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-43-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:45 memory:d2500000-d2501fff
  *-network

       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 06
       serial: 78:84:3c:ea:b9:d5
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:d1404000-d1404fff memory:d1400000-d1403fff

```
Thanks for any help. This is a Sony Vaio laptop.

---

### Post by praseodym on 2014-12-31
Change the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by Barsoom88 on 2015-01-10
Praseodym:
Thanks for the quick reply! I have tried your suggestion on different flavors and get the same result.
```
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
tar: 3005217-r8168-dkms-8.039.00.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
```
The first works but the second(even after reboot) gives the same message as above. I have tried all sudo together and individually all after reboot without any result.
Any more suggestions?
Thanks in advance.
B

---

### Post by praseodym on 2015-01-11
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz
```

Remove the file and try it again, maybe a broken download?!

---

### Post by Barsoom88 on 2015-01-12
No didn't work.
  	 	 	 	   ```
 sudo dkms install -m r8168-dkms -v 8.039.00  

 Error! Could not find module source directory.  
 Directory: /usr/src/r8168-dkms-8.039.00 does not exist.  
  $ sudo depmod -a  
 $ sudo update-initramfs -u  
 update-initramfs: Generating /boot/initrd.img-3.13.0-37-generic  
 Warning: No support for locale: en_US.utf8  
 $ sudo update-initramfs -u  

 update-initramfs: Generating /boot/initrd.img-3.13.0-37-generic  
 Warning: No support for locale: en_US.utf8  

```
I'm open to all suggestions to get a fix. But it does seem a bit weird as it worked before any of the recent upgrades.

---

### Post by praseodym on 2015-01-12
Lets start clean. Uninstall it

```
sudo dkms remove -m r8168-dkms -v 8.039.00 --all
sudo rm -r /usr/src/r8168-dkms-8.039.00 
```
Errors can be ignored. Download the file directly and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz)

Installation:

```
cd ~/Downloads/
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
sudo depmod -a
sudo update-initramfs -u 
```
Reboot

---

### Post by Barsoom88 on 2015-01-13
Praseodym,
I followed the code but the wired connection is still not working with a reboot. Got anything else? I don't mind trying until it's working.
  	 	 	 	   ```
-pc:~$ sudo dkms remove -m r8168-dkms -v 8.039.00 --all  

 [sudo] password for hobbes:  
 sudo: dkms: command not found  
 -pc:~$ sudo rm -r /usr/src/r8168-dkms-8.039.00  
 -pc:~$ cd ~/Downloads/  
 -pc:~/Downloads$ sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src  
 r8168-dkms-8.039.00/src/Makefile_linux24x 
 r8168-dkms-8.039.00/src/rtltool.h 
 r8168-dkms-8.039.00/src/r8168_realwow.h 
 r8168-dkms-8.039.00/src/rtltool.c 
 r8168-dkms-8.039.00/autorun.sh 
 r8168-dkms-8.039.00/README 
 r8168-dkms-8.039.00/src/r8168_asf.h 
 r8168-dkms-8.039.00/src/r8168_asf.c 
 r8168-dkms-8.039.00/src/ 
 r8168-dkms-8.039.00/src/Makefile 
 r8168-dkms-8.039.00/dkms.conf 
 r8168-dkms-8.039.00/src/r8168.h 
 r8168-dkms-8.039.00/src/r8168_dash.h 
 r8168-dkms-8.039.00/src/r8168_n.c 
 r8168-dkms-8.039.00/ 
 r8168-dkms-8.039.00/src/rtl_eeprom.h 
 r8168-dkms-8.039.00/Makefile 
 r8168-dkms-8.039.00/src/rtl_eeprom.c 
 -pc:~/Downloads$ sudo dkms add -m r8168-dkms -v 8.039.00  
 sudo: dkms: command not found  
 -pc:~/Downloads$ sudo dkms build -m r8168-dkms -v 8.039.00  
 sudo: dkms: command not found  
 -pc:~/Downloads$ sudo dkms install -m r8168-dkms -v 8.039.00  
 sudo: dkms: command not found  
 -pc:~/Downloads$ sudo depmod -a  
 -pc:~/Downloads$ sudo update-initramfs -u  
 update-initramfs: Generating /boot/initrd.img-3.13.0-44-generic  
 -pc:~/Downloads$  

```
Thanks for all the help!
B

---

### Post by praseodym on 2015-01-13
[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Install this file via double-click and try it again

---

### Post by Barsoom88 on 2015-01-13
Got a little further but didn't connect or see wired connection.
  	 	 	 	   ```
-pc:~/Downloads$ sudo dkms add -m r8168-dkms -v 8.039.00  

 

 Creating symlink /var/lib/dkms/r8168-dkms/8.039.00/source ->  
                  /usr/src/r8168-dkms-8.039.00  
 

 DKMS: add completed. 
 -pc:~/Downloads$ sudo dkms build -m r8168-dkms -v 8.039.00  
 

 Kernel preparation unnecessary for this kernel.  Skipping...  
   
 Building module:  
 cleaning build area....  
 'make' -C src/ all...............  
 cleaning build area....  
 

 DKMS: build completed.  
 -pc:~/Downloads$ sudo dkms install -m r8168-dkms -v 8.039.00  
 

 r8168:  
 Running module version sanity check.  
 

 Good news! Module version 8.039.00-NAPI for r8168.ko  
 exactly matches what is already found in kernel 3.13.0-44-generic.  
 DKMS will not replace this module.  

 You may override by specifying --force.  
 

 depmod........  
 

 DKMS: install completed.  
 -pc:~/Downloads$ sudo depmod -a  
 -pc:~/Downloads$ sudo update-initramfs -u  
 update-initramfs: Generating /boot/initrd.img-3.13.0-44-generic  
 -pc:~/Downloads$  

```

---

### Post by praseodym on 2015-01-14
Ok, now try
```

sudo modprobe -rfv r8169 r8168
sudo modprobe -v r8168
sudo service network-manager restart
```

---

### Post by Barsoom88 on 2015-01-16
Not working. But to double check I ran the sequence from the beginning and rebooted with the cable connected as before with wifi network disabled. It does see the neighbors wifi every time.
  	 	 	 	   ```
-pc:~/Downloads$ sudo modprobe -rfv r8169 r8168  

 rmmod r8169  
 rmmod mii  
 modprobe: FATAL: Module r8168 not found.  
 -pc:~/Downloads$ sudo modprobe -v r8168  
 modprobe: FATAL: Module r8168 not found.  
 -pc:~/Downloads$ sudo service network-manager restart  
 network-manager stop/waiting  
 network-manager start/running, process 14806  
 -pc:~/Downloads$ sudo service network-manager restart  
 network-manager stop/waiting  
 network-manager start/running, process 15002  
 -pc:~/Downloads$ sudo service network-manager restart  
 network-manager stop/waiting  
 network-manager start/running, process 15203  
 -pc:~/Downloads$  

```

---

### Post by praseodym on 2015-01-16
Please check:

```
dkms status
locate r8168.ko | grep lib

```

---


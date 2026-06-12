---
title: "rtl8822be bluetooth issue"
date: 2018-06-10
forum: Networking &amp; Wireless
---

### Post by Welly Wu on 2018-06-10
I own an ASUS ROG STRIX GL702ZC and I installed Ubuntu 18.04.0 64 bit LTS. I can't get jeremyb31's code to build and install his patched Bluetooth fix properly and Bluetooth 4.2 does not work. Can someone help me?

```
wellywu@GL702ZC:/usr/src$ sudo git clone https://github.com/jeremyb31/bluetooth-4.4.gitCloning into 'bluetooth-4.4'...
remote: Counting objects: 59, done.
remote: Total 59 (delta 0), reused 0 (delta 0), pack-reused 59
Unpacking objects: 100% (59/59), done.
wellywu@GL702ZC:/usr/src$ ls
bluetooth-4.4  linux-headers-4.15.0-22
libdvd-pkg     linux-headers-4.15.0-22-generic
wellywu@GL702ZC:/usr/src$ sudo dkms add ./bluetooth-4.4
Error! DKMS tree already contains: bluetooth-4.4-0.1
You cannot add the same module/version combo more than once.
wellywu@GL702ZC:/usr/src$ ls
bluetooth-4.4      libdvd-pkg               linux-headers-4.15.0-22-generic
bluetooth-4.4-0.1  linux-headers-4.15.0-22
wellywu@GL702ZC:/usr/src$ sudo dkms install bluetooth-4.4/0.1


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area...(bad exit status: 2)
make -j16 KERNELRELEASE=4.15.0-22-generic -C /lib/modules/4.15.0-22-generic/build M=/var/lib/dkms/bluetooth-4.4/0.1/build...(bad exit status: 2)
ERROR (dkms apport): binary package for bluetooth-4.4: 0.1 not found
Error! Bad return status for module build on kernel: 4.15.0-22-generic (x86_64)
Consult /var/lib/dkms/bluetooth-4.4/0.1/build/make.log for more information.
wellywu@GL702ZC:/usr/src$ sudo gedit /var/lib/dkms/bluetooth-4.4/0.1/build/make.log


** (gedit:3003): WARNING **: 11:44:07.061: Set document metadata failed: Setting attribute metadata::gedit-position not supported
wellywu@GL702ZC:/usr/src$ 
```

I attached my make.log output in this thread. Please take a look at it JeremyB.

I also looked at the rtl_bt tree and I downloaded the RTL8822B.bin file, but do I need to copy it somewhere to get Bluetooth to work?

```
wellywu@GL702ZC:~$ dmesg | egrep -i 'blue|firm'[    0.084981] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.108749] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    1.084339] [drm] Found UVD firmware Version: 1.130 Family ID: 16
[    1.084963] [drm] Found VCE firmware Version: 52.4 Binary ID: 3
[    2.312763] usb 1-10: Product: Bluetooth Radio 
[   35.207564] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[   35.255958] r8822be: Using firmware rtlwifi/rtl8822befw.bin
[   36.178183] Bluetooth: Core ver 2.22
[   36.178209] Bluetooth: HCI device and connection manager initialized
[   36.178212] Bluetooth: HCI socket layer initialized
[   36.178214] Bluetooth: L2CAP socket layer initialized
[   36.178220] Bluetooth: SCO socket layer initialized
[   36.378085] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.378086] Bluetooth: BNEP filters: protocol multicast
[   36.378089] Bluetooth: BNEP socket layer initialized
wellywu@GL702ZC:~$
```

---

### Post by jeremy31 on 2018-06-11
Maybe you don't have a bluetooth chip on the wifi card?  The patch I used in the 4.4 kernel source is included in 4.15

---

### Post by Welly Wu on 2018-06-11
Yes, I am using Linux kernel 4.15.0-22 generic AMD64. How do I check to determine if I do have a Bluetooth chip on the 802.11 Wi-Fi NIC? On the product description page, it says that Bluetooth 4.2 should be included with this product. Bluetooth was working when Microsoft Windows 10 Home and Pro 64 bit was installed on my GL702ZC.

---

### Post by jeremy31 on 2018-06-11
Something should show up in ```
lsusb; rfkill list
```

---

### Post by Welly Wu on 2018-06-11
```
wellywu@GL702ZC:~$ sudo lsusb[sudo] password for wellywu: 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0b05:1845 ASUSTek Computer, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0b05:1837 ASUSTek Computer, Inc. 
Bus 001 Device 002: ID 0bda:57fa Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 13d3:3526 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
wellywu@GL702ZC:~$ sudo rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
wellywu@GL702ZC:~$ 
```

I remember copying the firmware files for the RTL8822BE to the Bluetooth folder; my question is that should I remove these firmware files when trying to compile using Jeremy's code to get Bluetooth to enable itself or does it not matter?

What is going on here? It looks like Bluetooth does indeed exist on my GL702ZC, but it's not enabled.

---

### Post by jeremy31 on 2018-06-11
I will have to edit some code on another of my github projects for that USB ID as I can't do it on this phone

---

### Post by Welly Wu on 2018-06-11
Thank you Jeremy for taking a look at the USB ID. Do provide step by step instructions on how to enable Bluetooth for my GL702ZC and I will let you know about the output if it is a success or failure and the error messages. Thank you for taking a look into this and working with me.

Jeremy:

Just to let you know, I removed the rtl8822b_config.bin and rtl8822b_fw.bin from /lib/firmware/rtl_bt folder on my GL702ZC gaming notebook PC because those Realtek Bluetooth firmware files don't work. I did not want them to interfere with your updated Github code when you are ready. This should be okay, right?

---

### Post by jeremy31 on 2018-06-11
You will need those files as the bluetooth will need the firmware, so add them back before doing the following
```
sudo apt install git build-essential dkms
git clone https://github.com/jeremyb31/newbtfix-4.15.git
sudo dkms add ./newbtfix-4.15
sudo dkms install btusb/4.0
```

Reboot, disable Secure Boot if enabled
You can see what I changed at [https://github.com/jeremyb31/newbtfix-4.15/commit/4f8a73ef0aa8a1c31a69ca97d66b321ee0f81135](https://github.com/jeremyb31/newbtfix-4.15/commit/4f8a73ef0aa8a1c31a69ca97d66b321ee0f81135) all that does is tell the bluetooth system to use btrtl module for firmware loading as now all the system knows is that it is a bluetooth device without any idea of whether it needs firmware or what device it is

---

### Post by Welly Wu on 2018-06-11
I will follow your instructions and keep my fingers crossed. Booting up my GL702ZC now. I will report back. Thanks thus far.

Bluetooth 4.2 is enabled. It's working. Thank you Jeremy. I backed up those RTL8822BE Bluetooth firmware files just in case and I am going to subscribe to this Ubuntu Forums thread for future reference. Again, thank you so very much.

---

### Post by jeremy31 on 2018-06-11
You shouldn't have to worry about the bluetooth as long as you stick with the 4.15 kernel as the dkms should install the fix with any new 4.15 kernel install

---

### Post by Welly Wu on 2018-06-11
I have a new question for you Jeremy. What happens when Ubuntu 18.04.2 64 bit LTS is released and say a newer Linux kernel above 4.15 is available? I am assuming that Linux kernel 4.17 and above should fix this RTL8822BE Bluetooth issue automatically, correct? What do I need to keep in mind about future Ubuntu Hardware Enablement Stacks?

---

### Post by jeremy31 on 2018-06-11
I wouldn't use the newer short term release kernels if 4.15 works, stay with it.  The patch I used was only submitted to the upstream kernel less than 2 weeks ago so it might not be in 4.17 yet

---

### Post by Welly Wu on 2018-06-11
Jeremy:

I'm getting this problem upon trying to update to Linux kernel 4.15.0-23 generic AMD64:

```
wellywu@GL702ZC:~$ sudo apt upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-headers-4.15.0-23-generic (4.15.0-23.25) ...
/etc/kernel/header_postinst.d/dkms:
Error! Could not locate dkms.conf file.
File:  does not exist.
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 4
dpkg: error processing package linux-headers-4.15.0-23-generic (--configure):
 installed linux-headers-4.15.0-23-generic package post-installation script subprocess returned error exit status 1
Setting up linux-image-4.15.0-23-generic (4.15.0-23.25) ...
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-4.15.0-23-generic; however:
  Package linux-headers-4.15.0-23-generic is not configured yet.


dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 4.15.0.23.25); however:
  Package linux-headers-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic:
 linux-signed-generic depends on linux-generic; however:
  Package linux-generic is not configured yet.


dpkg: error processing package linux-signed-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for linux-image-4.15.0-23-generic (4.15.0-23.25) ...
/etc/kernel/postinst.d/dkms:
Error! Could not locate dkms.conf file.
File:  does not exist.
run-parts: /etc/kernel/postinst.d/dkms exited with return code 4
dpkg: error processing package linux-image-4.15.0-23-generic (--configure):
 installed linux-image-4.15.0-23-generic package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-4.15.0-23-generic
 linux-headers-generic
 linux-generic
 linux-signed-generic
 linux-image-4.15.0-23-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
wellywu@GL702ZC:~$
```

What's going on here?

---

### Post by Welly Wu on 2018-06-11
```
wellywu@GL702ZC:/usr/src$ lsbtusb-4.0                linux-headers-4.15.0-22-generic  newbtfix-4.15
libdvd-pkg               linux-headers-4.15.0-23
linux-headers-4.15.0-22  linux-headers-4.15.0-23-generic
wellywu@GL702ZC:/usr/src$ sudo dkms install btusb/4.0
Module btusb/4.0 already installed on kernel 4.15.0-22-generic/x86_64
wellywu@GL702ZC:/usr/src$
```

---

### Post by Welly Wu on 2018-06-11
```
wellywu@GL702ZC:/usr/src$ sudo dpkg-reconfigure linux-headers-4.15.0-23wellywu@GL702ZC:/usr/src$ sudo dkms status
bluetooth-4.4, 0.1: added
btusb, 4.0, 4.15.0-22-generic, x86_64: installedError! Could not locate dkms.conf file.
File:  does not exist.


wellywu@GL702ZC:/usr/src$ ls
btusb-4.0                linux-headers-4.15.0-22-generic  newbtfix-4.15
libdvd-pkg               linux-headers-4.15.0-23
linux-headers-4.15.0-22  linux-headers-4.15.0-23-generic
wellywu@GL702ZC:/usr/src$ ls -R /var/lib/dkms
/var/lib/dkms:
bluetooth-4.4  btusb  dkms_dbversion  rtlwifi-new


/var/lib/dkms/bluetooth-4.4:
0.1


/var/lib/dkms/bluetooth-4.4/0.1:
build  source


/var/lib/dkms/bluetooth-4.4/0.1/build:
ath3k.c        btbcm.h           btqca.h      hci_ath.c    hci_ll.c
bcm203x.c      btintel.c         btrtl.c      hci_ath.o    hci_ll.o
bcm203x.o      btintel.h         btrtl.h      hci_bcm.c    hci_qca.c
bfusb.c        btmrvl_debugfs.c  btsdio.c     hci_bcsp.c   hci_uart.h
bfusb.o        btmrvl_drv.h      btuart_cs.c  hci_h4.c     hci_vhci.c
bluecard_cs.c  btmrvl_main.c     btusb.c      hci_h4.o     Kconfig
bpa10x.c       btmrvl_sdio.c     btwilink.c   hci_h5.c     Makefile
bt3c_cs.c      btmrvl_sdio.h     dkms.conf    hci_intel.c  make.log
btbcm.c        btqca.c           dtl1_cs.c    hci_ldisc.c  README.md


/var/lib/dkms/btusb:
4.0  kernel-4.15.0-22-generic-x86_64


/var/lib/dkms/btusb/4.0:
4.15.0-22-generic  source


/var/lib/dkms/btusb/4.0/4.15.0-22-generic:
x86_64


/var/lib/dkms/btusb/4.0/4.15.0-22-generic/x86_64:
log  module


/var/lib/dkms/btusb/4.0/4.15.0-22-generic/x86_64/log:
make.log


/var/lib/dkms/btusb/4.0/4.15.0-22-generic/x86_64/module:
btusb.ko


/var/lib/dkms/rtlwifi-new:
0.6  kernel-4.15.0-22-generic-x86_64


/var/lib/dkms/rtlwifi-new/0.6:
4.15.0-22-generic  source


/var/lib/dkms/rtlwifi-new/0.6/4.15.0-22-generic:
x86_64


/var/lib/dkms/rtlwifi-new/0.6/4.15.0-22-generic/x86_64:
log  module


/var/lib/dkms/rtlwifi-new/0.6/4.15.0-22-generic/x86_64/log:
make.log


/var/lib/dkms/rtlwifi-new/0.6/4.15.0-22-generic/x86_64/module:
btcoexist.ko  rtl8192c-common.ko  rtl8192ee.ko  rtl8723-common.ko  rtl_pci.ko
halmac.ko     rtl8192ce.ko        rtl8192se.ko  rtl8723de.ko       rtl_usb.ko
phydm_mod.ko  rtl8192cu.ko        rtl8723ae.ko  rtl8821ae.ko       rtlwifi.ko
rtl8188ee.ko  rtl8192de.ko        rtl8723be.ko  rtl8822be.ko
wellywu@GL702ZC:/usr/src$
```

---

### Post by Welly Wu on 2018-06-11
```
wellywu@GL702ZC:/usr/src$ for i in /var/lib/dkms/*/[^k]*/source; do [ -e "$i" ] || echo "$i";done/var/lib/dkms/bluetooth-4.4/0.1/source
/var/lib/dkms/rtlwifi-new/0.6/source
wellywu@GL702ZC:/usr/src$
```

---

### Post by Welly Wu on 2018-06-11
This seemed to solve it:

```
wellywu@GL702ZC:/usr/src$ cd /var/lib/dkmswellywu@GL702ZC:/var/lib/dkms$ ls
bluetooth-4.4  btusb  dkms_dbversion  rtlwifi-new
wellywu@GL702ZC:/var/lib/dkms$ mkdir $HOME/Downloads/dkms_backup
wellywu@GL702ZC:/var/lib/dkms$ sudo cp -R /var/lib/dkms $HOME/Downloads/dkms_backup
wellywu@GL702ZC:/var/lib/dkms$ ls
bluetooth-4.4  btusb  dkms_dbversion  rtlwifi-new
wellywu@GL702ZC:/var/lib/dkms$ sudo rm -r -f bluetooth-4.4
wellywu@GL702ZC:/var/lib/dkms$ sudo rm -r -f rtlwifi-new
wellywu@GL702ZC:/var/lib/dkms$ cd /usr/src
wellywu@GL702ZC:/usr/src$ ls
btusb-4.0                linux-headers-4.15.0-22-generic  newbtfix-4.15
libdvd-pkg               linux-headers-4.15.0-23
linux-headers-4.15.0-22  linux-headers-4.15.0-23-generic
wellywu@GL702ZC:/usr/src$ sudo dpkg-reconfigure linux-headers-4.15.0-23
wellywu@GL702ZC:/usr/src$ sudo dpkg-reconfigure linux-headers-4.15.0-23-generic
/usr/sbin/dpkg-reconfigure: linux-headers-4.15.0-23-generic is broken or not fully installed
wellywu@GL702ZC:/usr/src$ sudo apt update
Hit:1 http://repo.sinew.in stable InRelease
Hit:2 http://ppa.launchpad.net/apt-fast/stable/ubuntu bionic InRelease         
Hit:3 http://archive.canonical.com/ubuntu bionic InRelease                     
Hit:4 http://linux-packages.resilio.com/resilio-sync/deb resilio-sync InRelease
Hit:5 https://deb.opera.com/opera-stable stable InRelease                      
Hit:6 http://apt.insynchq.com/ubuntu bionic InRelease                          
Hit:7 http://mirror.math.princeton.edu/pub/ubuntu bionic InRelease             
Ign:8 https://dl.bintray.com/resin-io/debian stable InRelease                  
Hit:9 http://mirror.math.princeton.edu/pub/ubuntu bionic-updates InRelease     
Hit:10 http://dist.jriver.com/latest/mediacenter jessie InRelease              
Hit:11 http://mirror.math.princeton.edu/pub/ubuntu bionic-backports InRelease  
Hit:12 http://linux.teamviewer.com/deb stable InRelease                        
Hit:13 http://mirror.math.princeton.edu/pub/ubuntu bionic-security InRelease   
Get:14 https://dl.bintray.com/resin-io/debian stable Release [1,878 B]         
Hit:15 http://linux.teamviewer.com/deb preview InRelease                       
Hit:16 http://ppa.launchpad.net/gerardpuig/ppa/ubuntu bionic InRelease   
Hit:17 http://ppa.launchpad.net/jtaylor/keepass/ubuntu bionic InRelease       
Hit:18 http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu bionic InRelease    
Hit:19 http://ppa.launchpad.net/teejee2008/ppa/ubuntu bionic InRelease
Hit:20 http://ppa.launchpad.net/unit193/encryption/ubuntu bionic InRelease    
Hit:21 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease       
Hit:22 http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu bionic InRelease
Fetched 1,878 B in 3s (608 B/s)                     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
wellywu@GL702ZC:/usr/src$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-headers-4.15.0-23-generic (4.15.0-23.25) ...
/etc/kernel/header_postinst.d/dkms:
Secure Boot not enabled on this system.
Warning: Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.
Setting up linux-image-4.15.0-23-generic (4.15.0-23.25) ...
Setting up linux-headers-generic (4.15.0.23.25) ...
Setting up linux-generic (4.15.0.23.25) ...
Setting up linux-signed-generic (4.15.0.23.25) ...
Processing triggers for linux-image-4.15.0-23-generic (4.15.0-23.25) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-23-generic
/etc/kernel/postinst.d/zz-update-grub:
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.15.0-23-generic
Found initrd image: /boot/initrd.img-4.15.0-23-generic
Found linux image: /boot/vmlinuz-4.15.0-22-generic
Found initrd image: /boot/initrd.img-4.15.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
W: APT had planned for dpkg to do more than it reported back (9 vs 16).
   Affected packages: linux-headers-4.15.0-23-generic:amd64 linux-image-4.15.0-23-generic:amd64
wellywu@GL702ZC:/usr/src$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wellywu@GL702ZC:/usr/src$
```

---

### Post by Welly Wu on 2018-06-11
OK. I know that this is going to sound confusing, but hear me out.

```
wellywu@GL702ZC:~$ sudo apt update
[sudo] password for wellywu: 
Hit:1 http://mirror.math.princeton.edu/pub/ubuntu bionic InRelease
Get:2 http://mirror.math.princeton.edu/pub/ubuntu bionic-updates InRelease [83.2 kB]
Hit:3 http://linux-packages.resilio.com/resilio-sync/deb resilio-sync InRelease
Hit:4 https://deb.opera.com/opera-stable stable InRelease                      
Get:5 http://mirror.math.princeton.edu/pub/ubuntu bionic-backports InRelease [74.6 kB]
Get:6 http://mirror.math.princeton.edu/pub/ubuntu bionic-security InRelease [83.2 kB]
Hit:7 http://apt.insynchq.com/ubuntu bionic InRelease                          
Hit:8 http://ppa.launchpad.net/apt-fast/stable/ubuntu bionic InRelease         
Hit:9 http://dist.jriver.com/latest/mediacenter jessie InRelease               
Hit:10 http://archive.canonical.com/ubuntu bionic InRelease                    
Hit:11 http://ppa.launchpad.net/gerardpuig/ppa/ubuntu bionic InRelease         
Hit:12 http://repo.sinew.in stable InRelease                                   
Hit:13 http://linux.teamviewer.com/deb stable InRelease                        
Hit:14 http://linux.teamviewer.com/deb preview InRelease                       
Hit:15 http://ppa.launchpad.net/jtaylor/keepass/ubuntu bionic InRelease        
Ign:16 https://dl.bintray.com/resin-io/debian stable InRelease           
Hit:17 http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu bionic InRelease    
Get:18 https://dl.bintray.com/resin-io/debian stable Release [1,878 B]         
Hit:19 http://ppa.launchpad.net/teejee2008/ppa/ubuntu bionic InRelease         
Hit:20 http://ppa.launchpad.net/unit193/encryption/ubuntu bionic InRelease
Hit:21 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease      
Hit:22 http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu bionic InRelease
Fetched 243 kB in 3s (84.7 kB/s)                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
wellywu@GL702ZC:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode intel-microcode iucode-tool thermald
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wellywu@GL702ZC:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  amd64-microcode intel-microcode iucode-tool thermald
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 2,341 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 185001 files and directories currently installed.)
Removing amd64-microcode (3.20171205.1) ...
update-initramfs: deferring update (trigger activated)
Removing intel-microcode (3.20180425.1~ubuntu0.18.04.1) ...
update-initramfs: deferring update (trigger activated)
Removing iucode-tool (2.3.1-1) ...
Removing thermald (1.7.0-5ubuntu1) ...
Processing triggers for initramfs-tools (0.130ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-22-generic
Processing triggers for man-db (2.8.3-2) ...
Processing triggers for dbus (1.12.2-1ubuntu1) ...
wellywu@GL702ZC:~$ uname -r
4.15.0-22-generic
wellywu@GL702ZC:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic
wellywu@GL702ZC:~$
```

When I do a sudo apt update followed by sudo apt upgrade, I don't see an update available for linux-kernel-4.15.0-23 available anymore. Is there a way to be able to download and install it so that the DKMS error does not show up again?

---

### Post by Welly Wu on 2018-06-11
In my post #27, what dkms modules are needed and which ones can be safely removed? When I removed bluetooth-4.4 and rtlwifi-new dkms modules and Linux kernel 4.15.0-23 was partially installed, I restarted my GL702ZC and Bluetooth was unavailable again. In the GNOME Power settings, the ability to turn on or off my Bluetooth radio disappeared. In the GNOME Bluetooth settings, it was permanently disabled.

---

### Post by Welly Wu on 2018-06-11
```
wellywu@GL702ZC:~$ cd /usr/src
wellywu@GL702ZC:/usr/src$ ls
btusb-4.0                linux-headers-4.15.0-22-generic  newbtfix-4.15
libdvd-pkg               linux-headers-4.15.0-23
linux-headers-4.15.0-22  linux-headers-4.15.0-23-generic
wellywu@GL702ZC:/usr/src$ sudo dkms install btusb/4.0
[sudo] password for wellywu: 
Module btusb/4.0 already installed on kernel 4.15.0-23-generic/x86_64
wellywu@GL702ZC:/usr/src$ cd /var/lib/dkms
wellywu@GL702ZC:/var/lib/dkms$ ls
btusb  dkms_dbversion
wellywu@GL702ZC:/var/lib/dkms$ uname -r
4.15.0-23-generic
wellywu@GL702ZC:/var/lib/dkms$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic
wellywu@GL702ZC:/var/lib/dkms$

wellywu@GL702ZC:/var/lib/dkms$ cd /lib/firmware/rtl_bt
wellywu@GL702ZC:/lib/firmware/rtl_bt$ ls
rtl8192ee_fw.bin  rtl8723d_config.bin  rtl8821a_fw.bin      rtl8822b_fw.bin
rtl8192eu_fw.bin  rtl8723d_fw.bin      rtl8821c_config.bin
rtl8723a_fw.bin   rtl8761a_fw.bin      rtl8821c_fw.bin
rtl8723b_fw.bin   rtl8812ae_fw.bin     rtl8822b_config.bin
wellywu@GL702ZC:/lib/firmware/rtl_bt$

```

I got the same problem. GNOME Power does not show a switch for Bluetooth to turn it on or off and the Bluetooth is permanently disabled again. I removed the same rtlwifi-new and bluetooth-4.4 folders from /var/lib/dkms. Jeremy, please help.

---

### Post by Welly Wu on 2018-06-12
I had to remove Linux-kernel-4.15.0-23 because I could not use Bluetooth 4.2. There is something about the modified Github page that makes it work with Linux-kernel-4.15.0-22 only. It appears that DKMS does work and the new bluetooth modifications successfully compile with the updated Linux kernel version, but after restarting there is no Bluetooth. I downgraded to the slightly older version for now. This is getting to be confusing and difficult.

---

### Post by jeremy31 on 2018-06-12
Strange that it didn't work in 4.15.0-23.  If it doesn't work in another new kernel post results for ```
modinfo btusb
```
It built fine and worked on 4.15.0-23 for me but I use a different bluetooth chipset

---

### Post by Welly Wu on 2018-06-12
```
wellywu@GL702ZC:~$ uname -r
4.15.0-22-generic
wellywu@GL702ZC:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic
wellywu@GL702ZC:~$ sudo modinfo btusb
[sudo] password for wellywu: 
filename:       /lib/modules/4.15.0-22-generic/updates/dkms/btusb.ko
license:        GPL
version:        0.9
description:    Generic Bluetooth USB driver ver 0.9
author:         Marcel Holtmann <marcel@holtmann.org>
srcversion:     1D6083B408C7B58E4CB86C7
alias:          usb:v8087p0A5Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v413Cp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v13D3p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v050Dp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0B05p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0A5Cp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v04CAp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0489p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0BB4p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v105Bp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v19FFp0239d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v413Cp8197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C10p0000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDBp1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BFp030Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp3800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8281d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8218d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8213d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5Cp21E1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp763Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v*p*d*dc*dsc*dp*icE0isc01ip01in*
alias:          usb:v*p*d*dcE0dsc01dp04ic*isc*ip*in*
alias:          usb:v*p*d*dcE0dsc01dp01ic*isc*ip*in*
alias:          of:N*T*Cusb1286,204eC*
alias:          of:N*T*Cusb1286,204e
depends:        btbcm,bluetooth,btrtl,btintel
retpoline:      Y
name:           btusb
vermagic:       4.15.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           disable_scofix:Disable fixup of wrong SCO buffer size (bool)
parm:           force_scofix:Force fixup of wrong SCO buffers size (bool)
parm:           reset:Send HCI reset command on initialization (bool)
wellywu@GL702ZC:~$
```

---

### Post by Welly Wu on 2018-06-12
Jeremy:

Did that code help you to help me in the near future?

---

### Post by QIII on 2018-06-12
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2383787](https://ubuntuforums.org/showthread.php?t=2383787)

Welly Wu -- jeremy31 will help when he gets to it.

---

### Post by jeremy31 on 2018-06-13
Welly do a ```
sudo -H gedit /usr/src/btusb-4.0/Makefile
```
Make the file contents be
```
KVER ?= $(shell uname -r)
obj-m += btusb.o
 
all:
	make -C /lib/modules/$(KVER)/build M=$(PWD) modules
 
clean:
	make -C /lib/modules/$(KVER)/build M=$(PWD) clean
```
Save and it should work in the future for kernel updates

---

### Post by Welly Wu on 2018-06-13
Jeremy:

It worked. Linux kernel 4.15.0-23 generic AMD64 and Bluetooth 4.2 are working again. Thank you.

---

### Post by Welly Wu on 2018-07-10
I know that this might drive you crazy, but I switched to Red Hat Fedora Workstation 28. It comes with Linux kernel 4.17 after the DNF software updates. Again, Bluetooth is not enabled within GNOME and I need your help once again Jeremy to update your software code on your Github page to fix it. What kind of information do you need from me again? It's my GL702ZC. Thank.

---

### Post by jeremy31 on 2018-07-10
See if you can file a bug with Red Hat and ask them to include this commit into the kernel as it fixes bluetooth for you [https://git.kernel.org/pub/scm/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth/btusb.c?id=1cd2fabf4bdcf95eda6a1bcebc4a0a965509da36](https://git.kernel.org/pub/scm/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth/btusb.c?id=1cd2fabf4bdcf95eda6a1bcebc4a0a965509da36)
I don't have an easy way to get source code for the 4.17 kernel

---

### Post by Welly Wu on 2018-07-10
Thank you so very much Jeremy. I created a free Red Hat Bugzilla account and I did my best to file a proper bug report to request the commit to the Linux kernel for Red Hat Fedora Workstation 28 64 bit and I added myself to their CC list to be notified in the future. Your expertise and help is going to get my RTL8822BE to be enabled for my ASUS ROG STRIX GL702ZC again.

---

### Post by Welly Wu on 2018-07-13
I installed Linux kernel 4.17.6 64 bit for Red Hat Fedora Workstation 28 64 bit and it solved my problem. Thanks again.

---

### Post by castor_fou on 2019-06-17
Anyone with an option to solve it with ubuntu (or helping with troubleshooting)? Installing Fedora is not an option for me.

---

### Post by QIII on 2019-06-17
Please start a new thread rather than attempting to resurrect a fossil one.  You probably won't get much help in an old thread.  You may refer to the URL for this one in your new thread if you think that would be helpful.

RIP.

Closed.

---


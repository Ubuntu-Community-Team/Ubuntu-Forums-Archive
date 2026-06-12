---
title: "BrosTrend (AC5) AC600 driver installation instructions."
date: 2018-12-21
forum: Networking &amp; Wireless
---

### Post by moonchow on 2018-12-21
Hi everyone,   I have been looking around for awhile now for the solution to my problem however I can't seem to find one and I'm on the verge of pulling my hair out. The issue in question is that I'm trying to install the drivers associated with my wifi card but I'm rather new to linux so I'm not quite sure what I should be doing with the driver files.  If anyone can explain to me what it is I have to do that would be great. Keep in mind that this computer has no access to internet whatsoever.   Ubuntu 18.04 LTS Wifi Card: [https://www.trendtechcn.com/Product.aspx?ProductId=324](https://www.trendtechcn.com/Product.aspx?ProductId=324) Drivers: [https://www.trendtechcn.com/userfiles/BrosTrend_AC5_Linux_Driver.zip](https://www.trendtechcn.com/userfiles/BrosTrend_AC5_Linux_Driver.zip)

---

### Post by slickymaster on 2018-12-21
Thread moved to **Networking & Wireless** for a better fit

---

### Post by praseodym on 2018-12-21
Try this driver installation via cable

```
wget https://launchpad.net/~timchen119/+archive/ubuntu/mt7610u-dkms/+files/mt7610u-dkms_1.0_amd64.deb
sudo dpkg -i mt7610u-dkms_1.0_amd64.deb 
```
Reboot

---

### Post by moonchow on 2018-12-22
> **praseodym said:**
> Try this driver installation via cable

```
wget https://launchpad.net/~timchen119/+archive/ubuntu/mt7610u-dkms/+files/mt7610u-dkms_1.0_amd64.deb
sudo dpkg -i mt7610u-dkms_1.0_amd64.deb 
```
Reboot

Thank you for the quick reply. 
Currently not home right now but I will give this a shot and post my results when I do get home.

---

### Post by moonchow on 2018-12-22
Unfortuately I can't give internet access to the computer so that method wont work since ubuntu needs dkms.
And the fresh install doesn't come with it.

---

### Post by wildmanne39 on 2018-12-22
Do you have a cell phone that you can tether to your computer?

---

### Post by moonchow on 2018-12-22
I do, going to do that now.

---

### Post by moonchow on 2018-12-22
Alright so I managed to tether the connection to the desktop and ran the commands, apt-get update and apt-get upgrade.

After that completed I rebooted the PC and ran these commands,

```
wget https://launchpad.net/~timchen119/+archive/ubuntu/mt7610u-dkms/+files/mt7610u-dkms_1.0_amd64.deb
sudo dpkg -i mt7610u-dkms_1.0_amd64.deb
```

However after running ```
sudo dpkg -i mt7610u-dkms_1.0_amd64.deb
```

I get this error.

```
Selecting previously unselected package mt7610u-dkms.
(Reading database ... 161925 files and directories currently installed.)
Preparing to unpack mt7610u-dkms_1.0_amd64.deb ...
Unpacking mt7610u-dkms (1.0) ...
dpkg: dependency problems prevent configuration of mt7610u-dkms:
 mt7610u-dkms depends on dkms (>= 1.95); however:
  Package dkms is not installed.

dpkg: error processing package mt7610u-dkms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mt7610u-dkms
```

So after that I ran this to install dkms ```
sudo apt-get install dkms
``` 

After doing that I got this error. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 dkms : Depends: gcc but it is not going to be installed
        Depends: dpkg-dev but it is not going to be installed
        Depends: make or
                 build-essential but it is not going to be installed
        Recommends: fakeroot
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

What do I do now? Do I run this command? ```
apt --fix-broken install
```

---

### Post by moonchow on 2018-12-22
So I got impatient and ended up just running the command:

```
sudo apt --fix-broken install
```

It installed everything including dkms so I went ahead and ran this command again:

```
sudo dpkg -i mt7610u-dkms_1.0_amd64.deb
```

Got this return:

```
(Reading database ... 167316 files and directories currently installed.)
Preparing to unpack mt7610u-dkms_1.0_amd64.deb ...
Unpacking mt7610u-dkms (1.0) over (1.0) ...
Setting up mt7610u-dkms (1.0) ...
chmod: cannot access '/usr/src/mt7610u-1.0/.git/hooks/pre-rebase.sample': No such file or directory
dpkg: error processing package mt7610u-dkms (--install):
 installed mt7610u-dkms package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 mt7610u-dkms
```

What now?

---

### Post by praseodym on 2018-12-22
Ok, that didnt work. Lets check
```

lsusb
```

---

### Post by moonchow on 2018-12-22
lsusb:   Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer Bus 002 Device 003: ID 0781:556b SanDisk Corp.  Bus 002 Device 002: ID 0e8d:7610 MediaTek Inc.  Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 004 Device 003: ID 1532:0053 Razer USA, Ltd  Bus 004 Device 002: ID 413c:2107 Dell Computer Corp.  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by praseodym on 2018-12-22
> ```
Bus 002 Device 002: ID 0e8d:7610 MediaTek Inc.
```

Try this one, Reply #215

[https://linuxforums.org.uk/index.php?topic=852.210](https://linuxforums.org.uk/index.php?topic=852.210)

---

### Post by moonchow on 2018-12-22
> **praseodym said:**
> Try this one, Reply #215  [https://linuxforums.org.uk/index.php?topic=852.210](https://linuxforums.org.uk/index.php?topic=852.210)  This worked!

---

### Post by praseodym on 2018-12-22
Great. This is how it works
```

sudo apt-get update
sudo apt-get dist-upgrade
```
Reboot, if necessary, and run

```
sudo apt-get install build-essential linux-headers-$(uname -r) git dkms
mkdir ~/mt7610u-driver
cd ~/mt7610u-driver
git clone https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes.git
cd ~/mt7610u-driver/mt7610u-linksys-ae6000-wifi-fixes
sudo cp -R . /usr/src/mt7610u_sta-1.0
sudo dkms add mt7610u_sta/1.0
sudo dkms build mt7610u_sta/1.0
sudo dkms install mt7610u_sta/1.0
sudo modprobe -v mt7610u_sta
```

modinfo mt7610u_sta ```

filename:       /lib/modules/4.4.0-141-generic/kernel/drivers/net/wireless/mt7610u_sta.ko
version:        3.0.0.2
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
license:        GPL
srcversion:     E6A5241C6891F1DFF8957C4
alias:          usb:v0E8Dp7650d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v0E8Dp7630d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v20F4p806Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB31d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v293Cp5702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8502d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0951d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p7610d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3425d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3D02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0075d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17DBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0105d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp760Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p010Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp761Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pC711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pB711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp7610d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp7610d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
retpoline:      Y
vermagic:       4.4.0-141-generic SMP mod_unload modversions retpoline 
parm:           mac:wireless mac addr (charp)
parm:           debug:log verbosity level (0: off, 1: error only [default], 2: warnings, 3: trace, 4: info, 5: loud) (long)
```

To uninstall, if required, run

```
sudo dkms remove mt7610u_sta/1.0 --all
```

---

### Post by alwayslearner on 2019-05-26
> **praseodym said:**
> Great. This is how it works
```

sudo apt-get update
sudo apt-get dist-upgrade
```
Reboot, if necessary, and run

```
sudo apt-get install build-essential linux-headers-$(uname -r) git dkms
mkdir ~/mt7610u-driver
cd ~/mt7610u-driver
git clone https://github.com/xtknight/mt7610u-linksys-ae6000-wifi-fixes.git
cd ~/mt7610u-driver/mt7610u-linksys-ae6000-wifi-fixes
sudo cp -R . /usr/src/mt7610u_sta-1.0
sudo dkms add mt7610u_sta/1.0
sudo dkms build mt7610u_sta/1.0
sudo dkms install mt7610u_sta/1.0
sudo modprobe -v mt7610u_sta
```

modinfo mt7610u_sta ```

filename:       /lib/modules/4.4.0-141-generic/kernel/drivers/net/wireless/mt7610u_sta.ko
version:        3.0.0.2
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
license:        GPL
srcversion:     E6A5241C6891F1DFF8957C4
alias:          usb:v0E8Dp7650d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v0E8Dp7630d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v20F4p806Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB31d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v293Cp5702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8502d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0951d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p7610d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3425d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3D02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0075d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17DBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0105d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp760Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p010Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp761Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pC711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pB711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp7610d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp7610d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
retpoline:      Y
vermagic:       4.4.0-141-generic SMP mod_unload modversions retpoline 
parm:           mac:wireless mac addr (charp)
parm:           debug:log verbosity level (0: off, 1: error only [default], 2: warnings, 3: trace, 4: info, 5: loud) (long)
```

To uninstall, if required, run

```
sudo dkms remove mt7610u_sta/1.0 --all
```
______________________________________

"May I use this help also to install the AVM Stick AC 860 ? Thanks in advance !"

---

### Post by praseodym on 2019-05-26
Should work. Alternatively, update to kernel 5.1

---


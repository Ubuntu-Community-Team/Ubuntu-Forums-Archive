---
title: "wifi driver not installed on HP-Laptop-15-da0xxx:"
date: 2019-07-05
forum: Networking &amp; Wireless
---

### Post by l1d2t on 2019-07-05
Dear all,
my HP-Laptop-15-da0xxx: installed ubuntu 18.04 but there is no wireless connection driver

I would be happy if anyone can fix this for me



best regards,

---

### Post by jeremy31 on 2019-07-05
What is the results from terminal for
```
lspci -nnk | grep -iA3 net
```

---

### Post by milankantony on 2019-08-27
```
tony@techyoga:~$ lspci -nnk | grep -iA3 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:84ad]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]
    Kernel modules: wl
tony@techyoga:~$
```

---

### Post by milankantony on 2019-08-27
Solved !!! 

Instal dkms if not installed

```
tony@techyoga:~$ sudo apt install git dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version (2.3-3ubuntu9.5).
dkms set to manually installed.
git is already the newest version (1:2.17.1-1ubuntu0.4).  
upgraded, 0 newly installed, 0 to remove and 79 not upgraded.

tony@techyoga:~$ git clone -b extended --single-branch [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
Cloning into 'rtlwifi_new'...
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
^Cceiving objects:  29% (1019/3504), 6.61 MiB | 18.00 KiB/s     

tony@techyoga:~$ git clone -b extended --single-branch [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
Cloning into 'rtlwifi_new'...
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3504 (delta 3), reused 1 (delta 1), pack-reused 3500
Receiving objects: 100% (3504/3504), 11.58 MiB | 86.00 KiB/s, done.
Resolving deltas: 100% (2823/2823), done
.
tony@techyoga:~$ sudo dkms add rtlwifi_new

Creating symlink /var/lib/dkms/rtlwifi-new/0.6/source ->
                 /usr/src/rtlwifi-new-0.6

DKMS: add completed.

tony@techyoga:~$ sudo dkms install rtlwifi-new/0.6

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
make -j4 KERNELRELEASE=4.15.0-58-generic -C /lib/modules/4.15.0-58-generic/build M=/var/lib/dkms/rtlwifi-new/0.6/build..........................
cleaning build area....(bad exit status: 2)

DKMS: build completed.

rtl_pci.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl_usb.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtlwifi.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

btcoexist.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

halmac.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

phydm_mod.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8188ee.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8192c-common.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8192ce.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8192cu.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8192de.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8192ee.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8192se.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8723ae.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8723be.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8723de.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8723-common.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8821ae.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

rtl8822be.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.15.0-58-generic/updates/dkms/

depmod..........
```

DKMS: install completed.:)

by[ https://www.techyo.ga]("https://www,techyo.ga")  or Millen

---


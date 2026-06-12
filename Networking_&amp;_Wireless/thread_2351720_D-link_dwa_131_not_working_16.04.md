---
title: "D-link dwa 131 not working 16.04"
date: 2017-02-06
forum: Networking &amp; Wireless
---

### Post by ebbxss on 2017-02-06
Can not install wireless adapter 
tried this:
sudo apt-get install git build-essential
git clone [https://github.com/Mange/rtl8192eu-linux-driver.git](https://github.com/Mange/rtl8192eu-linux-driver.git)
cd rtl8192eu-linux-driver
sudo make
sudo make install

and


sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192eu-dkms

---

### Post by chili555 on 2017-02-06
> sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192eu-dkmsPlease help us help you. We assume that when you tried this, something happened or didn't happen or crashed or sparks or smoke or ... something; however, we can't help you fix it if we don't know what it is! Please tell us.

Also, please tell us the result of the terminal command:```
lsusb
dmesg | grep 8192
```

---

### Post by ebbxss on 2017-02-06
lsusb:

---

### Post by chili555 on 2017-02-06
> **ebbxss said:**
> lsusb:Did you forget the results?

---

### Post by ebbxss on 2017-02-07
$ sudo add-apt-repository ppa:hanipouspilot/rtlwifi


 This is ppa for Realtek drivers from Larry Finger's github.


rtl8192eu is packaged from the Realtek site with some compat patches.
 More info: [https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi)
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpf3ksuhgk/secring.gpg' created
gpg: keyring `/tmp/tmpf3ksuhgk/pubring.gpg' created
gpg: requesting key 2F22E44A from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpf3ksuhgk/trustdb.gpg: trustdb created
gpg: key 2F22E44A: public key "Launchpad PPA for Pilot6" imported
gpg: Total number processed: 1
gpg:               import

~$ sudo apt-get update
Hit:1 [http://ru.archive.ubuntu.com/ubuntu](http://ru.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://ru.archive.ubuntu.com/ubuntu](http://ru.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Hit:3 [http://ru.archive.ubuntu.com/ubuntu](http://ru.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:6 [http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu](http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu) xenial InRelease   
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Hit:9 [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) xenial InRelease
0% [Release.gpg gpgv 1 189 B]                     
                              
Reading package lists... Done

sudo apt-get install rtl8192eu-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtl8192eu-dkms is already the newest version (4.4).
The following packages were automatically installed and are no longer required:
  kde-l10n-engb linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic
  linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
  linux-signed-image-4.4.0-31-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.



~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 1a2c:0e24 China Resource Semico Co., Ltd 
Bus 001 Device 004: ID 2001:3319 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


~$ dmesg | grep 8192
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88016ec00000 s98264 r8192 d28712 u1048576
[    0.000000] pcpu-alloc: s98264 r8192 d28712 u1048576 alloc=1*2097152
[    0.031172] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.031176] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    4.262857] 8192eu: module verification failed: signature and/or required key missing - tainting kernel
[    4.264778] RTL871X: rtl8192eu v4.3.15_14701.20150715_BTCOEX20150615-41
[    4.264779] RTL871X: rtl8192eu BT-Coex version = BTCOEX20150615-41
[    4.264831] RTL871X: CHIP TYPE: RTL8192E
[    4.265166] RTL871X: Chip Version Info: CHIP_8192E_Normal_Chip_SMIC_B_CUT_2T2R_RomVer(0)
[    4.265168] RTL871X: _ConfigChipOutEP_8192E OutEpQueueSel(0x07), OutEpNumber(3) 
[    4.265169] RTL871X: ====> ReadAdapterInfo8192EU
[    4.325381] RTL871X: hal_ReadMACAddress_8192EU MAC Address from EFUSE = 54:2a:a2:97:7b:0b
[    4.325382] RTL871X: Hal_ReadPowerSavingMode8192E...bHWPwrPindetect(0)-bHWPowerdown(0) ,bSupportRemoteWakeup(1)
[    4.325387] RTL871X: Hal_EfuseParseBTCoexistInfo8192E: Disable BT-coex, wifi ant_num=2
[    4.325392] RTL871X: ReadAdapterInfo8192EU <====
[    4.329401] usbcore: registered new interface driver rtl8192eu
[    4.331699] rtl8192eu 1-10:1.0 enx542aa2977b0b: renamed from wlan0

---

### Post by ebbxss on 2017-02-07
Yesterday while i posted here wifi connection suddenly appeared, but today it is down again after reboot

Figured out now that it works after after i unplug and reconnect wifi adapter

---

### Post by chili555 on 2017-02-07
> **ebbxss said:**
> Yesterday while i posted here wifi connection suddenly appeared, but today it is down again after reboot

Figured out now that it works after after i unplug and reconnect wifi adapterSo, you are all set?

---

### Post by ebbxss on 2017-02-10
Now I have to replug it after every reboot to make it work.

---

### Post by chili555 on 2017-02-10
> **ebbxss said:**
> Now I have to replug it after every reboot to make it work.Is the driver not loaded on reboot? Can you start it with:```
sudo modprobe rtl8192eu
```

---

### Post by ebbxss on 2017-02-10
> **chili555 said:**
> Is the driver not loaded on reboot? Can you start it with:```
sudo modprobe rtl8192eu
```
no

---

### Post by chili555 on 2017-02-10
How about:```
sudo service network-manager restart
```

---

### Post by ebbxss on 2017-02-14
This works! But until reboot.

---

### Post by chili555 on 2017-02-14
Let's try an old trick:```
sudo gedit /etc/rc.local
```Use nano or kate or leafpad if you don't have the text editor gedit.

Right above the last line, exit 0, please add:```
sleep 1
service network-manager restart
```Proofread carefully, save and close the text editor. Reboot.

Any improvement?

---

### Post by ebbxss on 2017-02-14
Works like a charm, Thanks!

---

### Post by chili555 on 2017-02-14
> **ebbxss said:**
> Works like a charm, Thanks!Awesome! Glad it's working.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---


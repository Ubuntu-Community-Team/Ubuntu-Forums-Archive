---
title: "Installation of wifi adapter from a cd"
date: 2019-07-06
forum: Networking &amp; Wireless
---

### Post by AnupamMitra on 2019-07-06
I tried to install iball wifi adapter in my PC from a installation CD, but I couldn't. My OS is Ubuntu 19.04 64 bit. I solicit help from expert.

---

### Post by jeremy31 on 2019-07-06
Post results from terminal for ```
lspci -nnk | grep -iA3 net; lsusb; rfkill list
```

Moved to Networking & Wireless

---

### Post by AnupamMitra on 2019-07-06
> **jeremy31 said:**
> Post results from terminal for ```
lspci -nnk | grep -iA3 net; lsusb; rfkill list
```

Moved to Networking & Wireless

Thanks. Sorry for the delay. However, I put below the output.
```

anupam@anupam-ubuntu:~$ lspci -nnk | grep -iA3 net; lsusb; rfkill list
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8168
    Kernel modules: r8168
02:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. IT8892E PCIe to PCI Bridge [1283:8892] (rev 41)
03:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
    Subsystem: D-Link System Inc DGE-528T PCI Gigabit Ethernet Adapter [1186:4300]
    Kernel modules: r8169
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04d9:1203 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
anupam@anupam-ubuntu:~$ ^C
anupam@anupam-ubuntu:~$ 

```

---

### Post by jeremy31 on 2019-07-06
Was the adapter installed when the command was run

---

### Post by AnupamMitra on 2019-07-06
> **jeremy31 said:**
> Was the adapter installed when the command was run

No, adapter couldn't be installed from the CD provided by the Company. That is why I sought help as to how it would be installed. Simply putting the CD in the CD/DVD Rom, it couldn't be installed. However, only the folder which are in the CD could be seen.

---

### Post by jeremy31 on 2019-07-06
Plug the wifi in and run the command and post results

---

### Post by AnupamMitra on 2019-07-06
> **jeremy31 said:**
> Plug the wifi in and run the command and post results

```

anupam@anupam-ubuntu:~$ lspci -nnk | grep -iA3 net; lsusb; rfkill list
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8168
    Kernel modules: r8168
02:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. IT8892E PCIe to PCI Bridge [1283:8892] (rev 41)
03:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
    Subsystem: D-Link System Inc DGE-528T PCI Gigabit Ethernet Adapter [1186:4300]
    Kernel modules: r8169
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 001 Device 003: ID 04d9:1203 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
3: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no
anupam@anupam-ubuntu:~$ 

```

---

### Post by jeremy31 on 2019-07-06
See the wireless script link in my signature and post results.  You must have a kernel driver loading for that USB wifi

---

### Post by AnupamMitra on 2019-07-06
> **jeremy31 said:**
> See the wireless script link in my signature and post results.  You must have a kernel driver loading for that USB wifi

```

anupam@anupam-ubuntu:~$ sudo apt update
[sudo] password for anupam: 
Ign:1 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu disco InRelease
Hit:2 http://archive.ubuntu.com/ubuntu disco InRelease
Err:3 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu disco Release
  404  Not Found [IP: 91.189.95.83 80]
Get:4 http://archive.ubuntu.com/ubuntu disco-updates InRelease [97.5 kB]
Get:5 http://archive.ubuntu.com/ubuntu disco-backports InRelease [88.8 kB]
Get:6 http://archive.ubuntu.com/ubuntu disco-security InRelease [97.5 kB]
Get:7 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 Packages [201 kB]
Get:8 http://archive.ubuntu.com/ubuntu disco-updates/main i386 Packages [174 kB]
Get:9 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 DEP-11 Metadata [126 kB]
Get:10 http://archive.ubuntu.com/ubuntu disco-updates/main DEP-11 48x48 Icons [13.7 kB]
Get:11 http://archive.ubuntu.com/ubuntu disco-updates/main DEP-11 64x64 Icons [30.8 kB]
Get:12 http://archive.ubuntu.com/ubuntu disco-updates/universe i386 Packages [233 kB]
Get:13 http://archive.ubuntu.com/ubuntu disco-updates/universe amd64 Packages [235 kB]
Get:14 http://archive.ubuntu.com/ubuntu disco-updates/universe amd64 DEP-11 Metadata [56.1 kB]
Get:15 http://archive.ubuntu.com/ubuntu disco-updates/universe DEP-11 48x48 Icons [24.8 kB]
Get:16 http://archive.ubuntu.com/ubuntu disco-updates/universe DEP-11 64x64 Icons [60.9 kB]
Get:17 http://archive.ubuntu.com/ubuntu disco-backports/universe amd64 DEP-11 Metadata [7,232 B]
Get:18 http://archive.ubuntu.com/ubuntu disco-security/main amd64 DEP-11 Metadata [27.2 kB]
Get:19 http://archive.ubuntu.com/ubuntu disco-security/main DEP-11 64x64 Icons [11.0 kB]
Get:20 http://archive.ubuntu.com/ubuntu disco-security/universe amd64 DEP-11 Metadata [11.5 kB]
Get:21 http://archive.ubuntu.com/ubuntu disco-security/universe DEP-11 64x64 Icons [23.2 kB]
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/gezakovacs/ppa/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
anupam@anupam-ubuntu:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  docbook-xml fonts-noto-hinted gcc-8-base:i386 libgdbm-compat4:i386
  libgdbm6:i386 libgmime-3.0-0 libieee1284-3:i386 libipt2 libllvm7
  libllvm7:i386 libmysqlclient20:i386 libncurses5:i386 libopencv-core3.2
  libopencv-imgproc3.2 libpci3:i386 libperl5.28:i386 libsane:i386 libsane1
  libsane1:i386 libsnmp30:i386 libtbb2 libtinfo5:i386 python-crypto
  python-dnspython python-tdb sgml-data
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  gnome-shell gnome-shell-common
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 879 kB of archives.
After this operation, 20.5 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 gnome-shell amd64 3.32.1-1ubuntu1~19.04.1 [674 kB]
Get:2 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 gnome-shell-common all 3.32.1-1ubuntu1~19.04.1 [204 kB]
Fetched 879 kB in 1s (1,227 kB/s)           
(Reading database ... 255062 files and directories currently installed.)
Preparing to unpack .../gnome-shell_3.32.1-1ubuntu1~19.04.1_amd64.deb ...
Unpacking gnome-shell (3.32.1-1ubuntu1~19.04.1) over (3.32.0+git20190410-1ubuntu1) ...
Preparing to unpack .../gnome-shell-common_3.32.1-1ubuntu1~19.04.1_all.deb ...
Unpacking gnome-shell-common (3.32.1-1ubuntu1~19.04.1) over (3.32.0+git20190410-1ubuntu1) ...
Setting up gnome-shell-common (3.32.1-1ubuntu1~19.04.1) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.23-4ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.60.4-0ubuntu0.19.04.1) ...
Processing triggers for libglib2.0-0:i386 (2.60.4-0ubuntu0.19.04.1) ...
Processing triggers for gconf2 (3.2.6-5ubuntu1) ...
Processing triggers for man-db (2.8.5-2) ...
Setting up gnome-shell (3.32.1-1ubuntu1~19.04.1) ...
anupam@anupam-ubuntu:~$ sudo apt install pastebinit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pastebinit is already the newest version (1.5-2).
pastebinit set to manually installed.
The following packages were automatically installed and are no longer required:
  docbook-xml fonts-noto-hinted gcc-8-base:i386 libgdbm-compat4:i386
  libgdbm6:i386 libgmime-3.0-0 libieee1284-3:i386 libipt2 libllvm7
  libllvm7:i386 libmysqlclient20:i386 libncurses5:i386 libopencv-core3.2
  libopencv-imgproc3.2 libpci3:i386 libperl5.28:i386 libsane:i386 libsane1
  libsane1:i386 libsnmp30:i386 libtbb2 libtinfo5:i386 python-crypto
  python-dnspython python-tdb sgml-data
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anupam@anupam-ubuntu:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
> chmod +x wireless-info && \
> ./wireless-info
--2019-07-07 00:43:10--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 13.234.210.38
Connecting to github.com (github.com)|13.234.210.38|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2019-07-07 00:43:11--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.152.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.152.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17452 (17K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  17.04K  --.-KB/s    in 0.04s   

Last-modified header missing -- time-stamps turned off.
2019-07-07 00:43:11 (479 KB/s) - ‘wireless-info’ saved [17452/17452]


Results saved in "/home/anupam/wireless-info.txt".

Results also archived in "/home/anupam/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

Do you also want to post them to your default 'pastebinit' provider? [Y/n]: y

Pastebin successful:

/usr/bin/pastebinit:42: DeprecationWarning: dist() and linux_distribution() functions are deprecated in Python 3.5
  release = platform.linux_distribution()[0].lower()
/usr/bin/pastebinit:413: DeprecationWarning: pasteURLopener style of invoking requests is deprecated. Use newer urlopen functions/methods
  url_opener = pasteURLopener()
http://paste.ubuntu.com/p/ffhdQkgWkz/

anupam@anupam-ubuntu:~$ 

```

---

### Post by jeremy31 on 2019-07-06
I would do
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot with the ethernet unplugged

---

### Post by AnupamMitra on 2019-07-07
> **jeremy31 said:**
> I would do
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot with the ethernet unplugged

Thanks jeremy31, with your continuous support now the stalemate is over. The WIFI Adapter is working. I'm marking it as SOLVED. 

However, I would like to know from you as to how it can be installed in a PC (UBUNTU 16.04 32 bit) where no internet connection is available. Actually I purchased the product (WIFI Adapter) only to get internet connection in the said PC through Mobile Hotspot.

---


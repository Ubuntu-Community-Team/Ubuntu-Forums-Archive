---
title: "Driver Installation Help Needed (D-Link DWA-182 Wireless USB Adapter)"
date: 2019-03-05
forum: Networking &amp; Wireless
---

### Post by joshualu on 2019-03-05
[COLOR=#000000]Good morning,[/COLOR]

[COLOR=#000000]I searched this same thread (title) posted on December 19, 2016 and it's closed on December 20, 2016. I have the same problem and tried the same method to no avail. So I just want to reopen this thread again and hope someone can help me to solve this D-Link Wi-Fi driver installation problem. 

[/COLOR][COLOR=#000000]I have a Lenovo ThinkPad T540p running Ubuntu 18.04 and Windows 7 pro on two different hard drives. Its internal Intel wi-fi chip works fine on both Ubuntu and Windows 7. My D-Link Wi-Fi USB dongle works in Windows 7, but not in ubuntu. 

[/COLOR][COLOR=#000000]I bought this D-Link DWA-182 Wireless USB Dongle and tried to install the driver manually on my ThinkPad T540p with command mentioned in the previous thread: 

[/COLOR][COLOR=#000000]Code:[/COLOR]
sudo apt-get update 
sudo apt-get install rtl8812au-dkms[COLOR=#000000][FONT=&amp] 

The output shows Error as follows:

t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ sudo apt-get install rtl8812au-dkms
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

[/FONT][/COLOR][COLOR=#000000]I just don't how know to go about this error. Hopefully somebody can guide me on this. Thanks.

P.S. This is my first post on this forum. I just don't know how to use "Code:" yet. So I just copied it from the previous post from [/COLOR][COLOR=#C61919][FONT=Ubuntubeta]wildmanne39[/FONT][/COLOR][COLOR=#000000].  [/COLOR][COLOR=#C61919]wildmanne39[/COLOR]

---

### Post by praseodym on 2019-03-05
Try

```
sudo dpkg --configure -a
```

---

### Post by joshualu on 2019-03-05
Errors were encountered while processing:
 libgl1:amd64
 libmutter-2-0:amd64
 gnome-shell
 xserver-xorg-core
 gir1.2-mutter-2:amd64
 gdm3

The detail of dpkg dependency problem as below:

```

t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ sudo dpkg --configure -a
[sudo] password for t540p2hdd: 
Setting up libgomp1:amd64 (8.2.0-1ubuntu2~18.04) ...
Setting up gnome-settings-daemon-schemas (3.28.1-0ubuntu1.1) ...
Setting up libnss-systemd:amd64 (237-3ubuntu10.12) ...
Setting up libcc1-0:amd64 (8.2.0-1ubuntu2~18.04) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for ureadahead (0.100.0-20) ...
ureadahead will be reprofiled on next reboot
Setting up libnss-myhostname:amd64 (237-3ubuntu10.12) ...
Setting up gir1.2-gnomebluetooth-1.0:amd64 (3.28.0-2ubuntu0.1) ...
Processing triggers for install-info (6.5.0.dfsg.1-2) ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.3-1ubuntu7) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for cracklib-runtime (2.9.2-5build1) ...
Setting up systemd-sysv (237-3ubuntu10.12) ...
Setting up mutter-common (3.28.3-2~ubuntu18.04.2) ...
Setting up libglib2.0-0:amd64 (2.56.3-0ubuntu0.18.04.1) ...
Setting up libgdm1 (3.28.3-0ubuntu18.04.3) ...
Setting up libglapi-mesa:amd64 (18.2.2-0ubuntu1~18.04.2) ...
Setting up libdrm-common (2.4.95-1~18.04.1) ...
Setting up gnome-shell-common (3.28.3-0ubuntu0.18.04.4) ...
Setting up libx11-xcb1:amd64 (2:1.6.4-3ubuntu0.1) ...
Setting up bubblewrap (0.2.1-1ubuntu0.1) ...
Setting up libglib2.0-data (2.56.3-0ubuntu0.18.04.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up udev (237-3ubuntu10.12) ...
update-initramfs: deferring update (trigger activated)
Setting up gnome-bluetooth (3.28.0-2ubuntu0.1) ...
Setting up libpango-1.0-0:amd64 (1.40.14-1ubuntu0.1) ...
Processing triggers for systemd (237-3ubuntu10.12) ...
dpkg: dependency problems prevent configuration of libgl1:amd64:
 libgl1:amd64 depends on libglvnd0 (= 1.0.0-2ubuntu2.2); however:
  Version of libglvnd0:amd64 on system is 1.0.0-2ubuntu2.1.
 libgl1:amd64 depends on libglx0 (= 1.0.0-2ubuntu2.2); however:
  Version of libglx0:amd64 on system is 1.0.0-2ubuntu2.1.

dpkg: error processing package libgl1:amd64 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.8.3-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1) ...
Setting up initramfs-tools-bin (0.130ubuntu3.6) ...
Setting up friendly-recovery (0.2.38ubuntu1) ...
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-45-generic
Found initrd image: /boot/initrd.img-4.15.0-45-generic
Found linux image: /boot/vmlinuz-4.15.0-29-generic
Found initrd image: /boot/initrd.img-4.15.0-29-generic
Adding boot menu entry for EFI firmware configuration
done
Processing triggers for dbus (1.12.2-1ubuntu1) ...
Setting up x11-common (1:7.7+19ubuntu7.1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Processing triggers for hicolor-icon-theme (0.17-2) ...
Setting up libglib2.0-bin (2.56.3-0ubuntu0.18.04.1) ...
Setting up gnome-desktop3-data (3.28.2-0ubuntu1.2) ...
Setting up libx11-data (2:1.6.4-3ubuntu0.1) ...
Setting up libpolkit-gobject-1-0:amd64 (0.105-20ubuntu0.18.04.4) ...
Setting up xserver-common (2:1.19.6-1ubuntu4.2) ...
Setting up gir1.2-gdm-1.0 (3.28.3-0ubuntu18.04.3) ...
Setting up libpam-systemd:amd64 (237-3ubuntu10.12) ...
dpkg: dependency problems prevent configuration of libmutter-2-0:amd64:
 libmutter-2-0:amd64 depends on libgl1; however:
  Package libgl1:amd64 is not configured yet.

dpkg: error processing package libmutter-2-0:amd64 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.1) ...
Setting up initramfs-tools-core (0.130ubuntu3.6) ...
Setting up libpolkit-agent-1-0:amd64 (0.105-20ubuntu0.18.04.4) ...
Setting up gir1.2-polkit-1.0 (0.105-20ubuntu0.18.04.4) ...
Setting up libx11-6:amd64 (2:1.6.4-3ubuntu0.1) ...
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on libmutter-2-0 (>= 3.28.3); however:
  Package libmutter-2-0:amd64 is not configured yet.

dpkg: error processing package gnome-shell (--configure):
 dependency problems - leaving unconfigured
Setting up initramfs-tools (0.130ubuntu3.6) ...
update-initramfs: deferring update (trigger activated)
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on libgl1; however:
  Package libgl1:amd64 is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
Setting up libdrm2:amd64 (2.4.95-1~18.04.1) ...
Setting up libpangoft2-1.0-0:amd64 (1.40.14-1ubuntu0.1) ...
Setting up libdrm-intel1:amd64 (2.4.95-1~18.04.1) ...
Setting up libpolkit-backend-1-0:amd64 (0.105-20ubuntu0.18.04.4) ...
dpkg: dependency problems prevent configuration of gir1.2-mutter-2:amd64:
 gir1.2-mutter-2:amd64 depends on libmutter-2-0 (= 3.28.3-2~ubuntu18.04.2); however:
  Package libmutter-2-0:amd64 is not configured yet.

dpkg: error processing package gir1.2-mutter-2:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up libdrm-radeon1:amd64 (2.4.95-1~18.04.1) ...
Setting up libdrm-nouveau2:amd64 (2.4.95-1~18.04.1) ...
Setting up xserver-xorg-legacy (2:1.19.6-1ubuntu4.2) ...
setting xserver-xorg-legacy/xwrapper/allowed_users from configuration file
Setting up libglx-mesa0:amd64 (18.2.2-0ubuntu1~18.04.2) ...
Setting up libcairo2:amd64 (1.15.10-2ubuntu0.1) ...
Setting up libdrm-amdgpu1:amd64 (2.4.95-1~18.04.1) ...
Setting up policykit-1 (0.105-20ubuntu0.18.04.4) ...
Setting up libcairo-gobject2:amd64 (1.15.10-2ubuntu0.1) ...
dpkg: dependency problems prevent configuration of gdm3:
 gdm3 depends on gnome-shell (>= 3.19.92); however:
  Package gnome-shell is not configured yet.

dpkg: error processing package gdm3 (--configure):
 dependency problems - leaving unconfigured
Setting up libpangoxft-1.0-0:amd64 (1.40.14-1ubuntu0.1) ...
Setting up libpangocairo-1.0-0:amd64 (1.40.14-1ubuntu0.1) ...
Setting up gir1.2-pango-1.0:amd64 (1.40.14-1ubuntu0.1) ...
Setting up libgnome-desktop-3-17:amd64 (3.28.2-0ubuntu1.2) ...
Setting up gnome-settings-daemon (3.28.1-0ubuntu1.1) ...
Setting up gir1.2-gnomedesktop-3.0:amd64 (3.28.2-0ubuntu1.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for initramfs-tools (0.130ubuntu3.6) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-45-generic
Errors were encountered while processing:
 libgl1:amd64
 libmutter-2-0:amd64
 gnome-shell
 xserver-xorg-core
 gir1.2-mutter-2:amd64
 gdm3
t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ iwconfig
wlp4s0    IEEE 802.11  ESSID:"bluffshouse"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: 98:FC:11:FF:C7:47   
          Bit Rate=650 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:530   Missed beacon:0

lo        no wireless extensions.

enp0s25   no wireless extensions.

t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ 

```

---

### Post by joshualu on 2019-03-06
I went back and read the posts from December 20, 2016 more carefully. The posts stated it used an Ethernet connection, not another Wi-Fi connection to install the driver successfully. I thought of the possibility of the interference from the existing Intel wireless-ac 7260 chip on the laptop. I went ahead opening the bottom cover and pulling the Intel Wi-Fi 7260 card off the laptop. I then plugged an Ethernet cable into this laptop. (I wish I know how to disable it in the device manager like in Windows though instead of pulling it out). 

I reboot laptop and issue the command "sudo apt-get install rtl8812au-dkms" suggested by wildmanne39 again. This time it installed the driver rtl8812au-dkms successfully without any problem. Here is the printout:

```

  	 	 	 	   t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ sudo apt-get install rtl8812au-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.15.0-29 linux-headers-4.15.0-29-generic linux-image-4.15.0-29-generic linux-modules-4.15.0-29-generic
  linux-modules-extra-4.15.0-29-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  build-essential dkms dpkg-dev fakeroot g++ g++-7 gcc gcc-7 libalgorithm-diff-perl libalgorithm-diff-xs-perl
....
Setting up rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu8) ...
Loading new rtl8812au-4.3.8.12175.20140902+dfsg DKMS files...
Building for 4.15.0-46-generic
Building initial module for 4.15.0-46-generic
Generating a 2048 bit RSA private key
.............+++
.............................................................................................+++
writing new private key to '/var/lib/shim-signed/mok/MOK.priv'
-----
Secure Boot not enabled on this system.
Done.

8812au:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-46-generic/updates/dkms/

depmod........

DKMS: install completed.
Setting up build-essential (12.4ubuntu1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ 

```

Up to this point, driver is finally installed successfully and everything looks promising. I unplugged the Ethernet cable and reboot the laptop. But not until I checked if the handshake happened between the driver and the D-Link DWA-182 Wi-Fi USB dongle.

```

t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ iwconfig
enp0s25   no wireless extensions.

lo        no wireless extensions.

t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ sudo lshw -C network
[sudo] password for t540p2hdd: 
  *-network                 
       description: Ethernet interface
       product: Ethernet Connection I217-LM
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 04
       serial: 54:ee:75:89:5b:f7
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f2900000-f291ffff memory:f293f000-f293ffff ioport:5080(size=32)
t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 138a:0017 Validity Sensors, Inc. Fingerprint Reader
Bus 003 Device 002: ID 2001:3101 D-Link Corp. 
Bus 003 Device 004: ID 04f2:b39a Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ 

```

Obviously, the laptop still doesn't see the D-link USB dongle in the network. It just sees it as an USB device (D-Link Corp from lsusb).

This D-Link Wi-Fi driver is built on the Linux kernel 4.15 and my Ubuntu 18.04.2 LTS is also on the Linux kernel 4.15, "bionic". See below:

```

t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.2 LTS"
Linux t540p2hdd-ThinkPad-T540p 4.15.0-46-generic #49-Ubuntu SMP Wed Feb 6 09:33:07 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ 

```

I am out of idea. Please help.

---

### Post by chili555 on 2019-03-06
First, it would shock me (shock me, I tell you!!) to learn that any USB dongle outperforms an Intel 7260. I would much rather troubleshoot the Intel than install a driver for the USB.

Nonetheless, let's see if the driver you installed actually covers your device: ID 2001:3101 D-Link Corp. We'll do so by checking the listed aliases in the driver for your exact device:```

modinfo rtl8812au | grep 3101

```It comes back empty, I suspect. That means that this exact driver, or, at least, this driver version, doesn't cover your exact device.

The following usually reliable resources suggest that it is actually a Broadcom device, not Realtek, and that there is currently no support in Ubuntu or any other Linux distribution for it.

[https://translate.google.com/translate?hl=en&sl=de&u=https://wiki.ubuntuusers.de/WLAN/Karten/D-Link/&prev=search](https://translate.google.com/translate?hl=en&sl=de&u=https://wiki.ubuntuusers.de/WLAN/Karten/D-Link/&prev=search)

[https://wikidevi.com/wiki/D-Link_DWA-182_rev_A1](https://wikidevi.com/wiki/D-Link_DWA-182_rev_A1)

[https://ubuntuforums.org/showthread.php?t=2290133](https://ubuntuforums.org/showthread.php?t=2290133)

Now, how about that Intel?

---

### Post by joshualu on 2019-03-06
1. Why this USB Wi-Fi dongle - 

My Intel wireless-ac 7260 chip will  freeze from time to time in both Windows 7 or Ubuntu 18.04. I later  found out my Lenovo ThinkPad T540p won't boot with just an AC adapter  plugged in without a battery (it would still charge battery though and  It works on battery too). I sent it to Lenovo for repair under the  warranty three weeks ago. Lenovo replaced the motherboard and keyboard,  but not the Intel Wi-Fi card, battery, and charger. Lenovo claimed it  passed all the tests before it was sent back to me. So my Intel Wi-Fi  freeze issue is still there of course. I communicated this issue back to  Lenovo and they told me that it could be due to some interference from  other devices around my laptop. They sent a technician out and tested my  Intel wi-fi card to be fine. He tried three different Intel cards and  they all had this same issue. He then used an USB wifi dongle and it had  no freeze any more. He suggested me to get a USB wifi dongle because it  had better electromagnetic shield capability built-in. The one he tried  it on was a D-Link DWA-182. Of course he tried on Windows 7 only. Hence  I bought this same USB wifi dongle.

2. printout from the command:

```

t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ sudo modinfo rtl8812au | grep 3101
modinfo: ERROR: Module rtl8812au not found.
t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ 

```

mmm the module rtl8812au is not there? it reported successfully installed last night. very confusion!!!

---

### Post by chili555 on 2019-03-06
> 
mmm the module rtl8812au is not there? it reported successfully installed last night. very confusion!!!
Don't worry about it or waste time trying to fix it. I have already installed rtl8812au-dkms on my machine and I already know that it doesn't cover your Broadcom device. I already knew the answer before I asked the question!

Let's see if we can find some reasons that your Intel freezes. Even though it has been removed, the logs may help us. Please run and post:```
sudo iwlist scan
```Please show me your network only and redact the MAC address like this:```

wlp3s0    Scan completed :
          Cell 01 - Address: [COLOR="#FF0000"]xxxxxxx[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000032918c55595
                    Extra: Last beacon: 500ms ago
                    IE: Unknown: 000447425235
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


```Also run and post:```
grep iwl /var/log/kern.log
grep iwl /var/log/kern.log.1


```Depending on what these show, I will probably have more requests.

---

### Post by joshualu on 2019-03-06
```

t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ lspci -knn | grep Net -A2
04:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c270]
    Kernel driver in use: iwlwifi
t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ sudo iwlist scan
[sudo] password for t540p2hdd: 
wlp4s0    Scan completed :
          Cell 01 - Address: 98:FC:11:FF:C7:48
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"bluffshouse2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a18563d75d
                    Extra: Last beacon: 1072ms ago
                    IE: Unknown: 000C626C75666673686F75736532
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860

```

```

t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ grep iwl /var/log/kern.log
Mar  4 23:41:05 t540p2hdd-ThinkPad-T540p kernel: [   22.097094] iwlwifi 0000:04:00.0: loaded firmware version 17.948900127.0 op_mode iwlmvm
Mar  4 23:41:05 t540p2hdd-ThinkPad-T540p kernel: [   22.198338] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
Mar  4 23:41:05 t540p2hdd-ThinkPad-T540p kernel: [   22.215996] iwlwifi 0000:04:00.0: base HW address: 28:b2:bd:00:b7:48
Mar  4 23:41:05 t540p2hdd-ThinkPad-T540p kernel: [   22.510939] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
Mar  4 23:41:05 t540p2hdd-ThinkPad-T540p kernel: [   25.343139] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
Mar  4 23:52:04 t540p2hdd-ThinkPad-T540p kernel: [   22.886731] iwlwifi 0000:04:00.0: loaded firmware version 17.948900127.0 op_mode iwlmvm
Mar  4 23:52:04 t540p2hdd-ThinkPad-T540p kernel: [   24.077229] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
Mar  4 23:52:04 t540p2hdd-ThinkPad-T540p kernel: [   24.095276] iwlwifi 0000:04:00.0: base HW address: 28:b2:bd:00:b7:48
Mar  4 23:52:04 t540p2hdd-ThinkPad-T540p kernel: [   25.500633] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
Mar  4 23:52:04 t540p2hdd-ThinkPad-T540p kernel: [   25.866609] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
Mar  5 17:14:37 t540p2hdd-ThinkPad-T540p kernel: [   15.524960] iwlwifi 0000:04:00.0: loaded firmware version 17.948900127.0 op_mode iwlmvm
Mar  5 17:14:37 t540p2hdd-ThinkPad-T540p kernel: [   15.648533] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
Mar  5 17:14:37 t540p2hdd-ThinkPad-T540p kernel: [   15.666549] iwlwifi 0000:04:00.0: base HW address: 28:b2:bd:00:b7:48
Mar  5 17:14:37 t540p2hdd-ThinkPad-T540p kernel: [   16.950009] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
Mar  5 17:14:37 t540p2hdd-ThinkPad-T540p kernel: [   18.921396] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
Mar  5 20:28:05 t540p2hdd-ThinkPad-T540p kernel: [   27.265948] iwlwifi 0000:04:00.0: loaded firmware version 17.948900127.0 op_mode iwlmvm
Mar  5 20:28:05 t540p2hdd-ThinkPad-T540p kernel: [   27.389768] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
Mar  5 20:28:05 t540p2hdd-ThinkPad-T540p kernel: [   27.525088] iwlwifi 0000:04:00.0: base HW address: 28:b2:bd:00:b7:48
Mar  5 20:28:05 t540p2hdd-ThinkPad-T540p kernel: [   27.788909] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
Mar  5 20:28:05 t540p2hdd-ThinkPad-T540p kernel: [   28.334242] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
Mar  6 14:20:56 t540p2hdd-ThinkPad-T540p kernel: [   23.630780] iwlwifi 0000:04:00.0: loaded firmware version 17.948900127.0 op_mode iwlmvm
Mar  6 14:20:56 t540p2hdd-ThinkPad-T540p kernel: [   23.854002] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
Mar  6 14:20:56 t540p2hdd-ThinkPad-T540p kernel: [   23.872506] iwlwifi 0000:04:00.0: base HW address: 28:b2:bd:00:b7:48
Mar  6 14:20:56 t540p2hdd-ThinkPad-T540p kernel: [   24.164725] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
Mar  6 14:20:56 t540p2hdd-ThinkPad-T540p kernel: [   24.310171] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ grep iwl /var/log/kern.log.1
Mar  2 02:34:51 t540p2hdd-ThinkPad-T540p kernel: [   22.752518] iwlwifi 0000:04:00.0: loaded firmware version 17.948900127.0 op_mode iwlmvm
Mar  2 02:34:51 t540p2hdd-ThinkPad-T540p kernel: [   23.298479] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
Mar  2 02:34:51 t540p2hdd-ThinkPad-T540p kernel: [   23.315960] iwlwifi 0000:04:00.0: base HW address: 28:b2:bd:00:b7:48
Mar  2 02:34:51 t540p2hdd-ThinkPad-T540p kernel: [   24.488722] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
Mar  2 02:34:51 t540p2hdd-ThinkPad-T540p kernel: [   24.946739] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
Binary file /var/log/kern.log.1 matches
t540p2hdd@t540p2hdd-ThinkPad-T540p:~$ 


```

---

### Post by chili555 on 2019-03-07
We don't see anything alarming going on with the driver, iwlwifi. Let's also check the interface:

```
grep wlp /var/log/kern.log
grep wlp /var/log/kern.log.1
```We do see a couple of things to tweak in your router.

WPA2-AES is preferred; not any WPA and WPA2 mixed mode and *certainly not* TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Once we see the further results above, we may have other suggestions.

---

### Post by mj41 on 2019-04-29
Hello. i have the same prblem with this wifi adapter.
i followed the steps as well. when i put:
```
sudo iwlist scan
```
 i get:
```
wlp3s0    Interface doesn't support scanning : Network is down

enp2s0    Interface doesn't support scanning.

enp0s20u3  Interface doesn't support scanning.

lo        Interface doesn't support scanning.
```

also if u have any idea how to fix my internal chip, would be great. for some reason it stopped working a few days ago. i've tried everything i found on google. still nothing. so annoying. i have to tether my phone to use the house wifi.
```
*-network DISABLED
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 93
       serial: e4:f8:9c:40:5e:c5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.18.0-18-generic firmware=17.948900127.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:54 memory:d1100000-d1101fff


```

---

### Post by chili555 on 2019-04-29
> *-network DISABLED

This usually tells us that the hardware switch is set to disable the wireless radio. What does this tell us?```
rfkill list all
```Please find the switch and enable the wireless.

---

### Post by samwwjd on 2019-07-13
Hey guys! :) after much digging, it turns out our revision D usb dongles have a newer chipset! See comment below that I posted on superuser and askubuntu as well! :) Hope this helps someone as much as it helped me!

Special note! :D I have D-Link AC1200 USB adapter. It's a Revision D tho!!! So I kept digging and digging... turns out, revision C had a different chip, than mine!
So for those of you digging that can't get yours working,

OR if you know you have a Realtek RTL8812BU or RTL8822BU chipset, then try the following 1 line at a time in your command prompt. Worked for me and I'm so stoked right now! :D :) I had to dig and dig tho, so I thought I would drop this gem here since all my searches for DWA 182 d1 led me here at one point or another. Hope this helps someone. :)
```

    sudo apt update
    sudo apt install -y git
    git clone https://github.com/EntropicEffect/rtl8822bu.git
    cd rtl8822bu
    make
    sudo make install
    sudo modprobe 88x2bu

```

---

### Post by kurt18947 on 2019-07-21
> I have D-Link AC1200 USB adapter. It's a Revision D tho!!! So I kept  digging and digging... turns out, revision C had a different chip, than  mine!
So for those of you digging that can't get yours working,


D-Link is still doing that, huh? I haven't really messed with wifi much the last few years but I bought a D-link adapter one time and it worked great right out of the box. Bought a second one a few days later and it didn't work. That's when i learned that D-link ( and I doubt they're alone in this) changes chipsets but doesn't change model numbers. They may append a letter or different version number to the model number to indicate something has changed but that's not reflected on the package, only on the device itself - or not at all.

---

### Post by enahssmith on 2019-11-15
Will this work for revision C?

---

### Post by chili555 on 2019-11-16
> **enahssmith said:**
> Will this work for revision C?Please start your own new question and include the result of the terminal command:```
lsusb
```

---


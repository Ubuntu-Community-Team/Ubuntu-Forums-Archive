---
title: "WiFi driver for Samsung Galaxy Book"
date: 2018-02-09
forum: Networking &amp; Wireless
---

### Post by makem2 on 2018-02-09
I have installed and updated xubuntu 17.01 alongside Windows 10, using a wifi dongle.

I need a driver for the internal WiFi card. I believe there is one in the repositories and ask for assistance to obtain and install it.

I tried to obtain the information required before posting but failed as shown below:

```
makem@galaxy-book:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
> 

```

```
makem@galaxy-book:~$ chmod +x wireless-info && \
> 

```

```

makem@galaxy-book:~$ ./wireless-info
bash: ./wireless-info: No such file or directory

```

I also found this:

```

makem@galaxy-book:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 04e8:a00a Samsung Electronics Co., Ltd 
Bus 001 Device 006: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 002: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

makem@galaxy-book:~$ sudo lshw -C network
[sudo] password for makem: 
  *-network                 
       description: Network controller
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 32
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ath10k_pci latency=0
       resources: irq:280 memory:df400000-df5fffff
  *-network
       description: Wireless interface
       physical id: 6
       bus info: usb@1:1.1
       logical name: wlx7cdd90d84115
       serial: 7c:dd:90:d8:41:15
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.13.0-32-generic firmware=0.36 ip=192.168.2.27 link=yes multicast=yes wireless=IEEE 802.11
makem@galaxy-book:~$

```

```

makem@galaxy-book:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)
00:05.0 Multimedia controller: Intel Corporation Skylake Imaging Unit (rev 01)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:14.3 Multimedia controller: Intel Corporation Device 9d32 (rev 01)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:15.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #2 (rev 21)
00:15.3 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #3 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:19.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #2 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1e.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #0 (rev 21)
00:1e.6 SD Host controller: Intel Corporation Sunrise Point-LP Secure Digital IO Controller (rev 21)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Multimedia audio controller: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
makem@galaxy-book:~$ 

```

Tried this after I read the above output:

[https://ubuntuforums.org/showthread.php?t=2323812](https://ubuntuforums.org/showthread.php?t=2323812)

```

makem@galaxy-book:~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk gitweb git-cvs git-mediawiki git-svn
The following NEW packages will be installed
  git git-man liberror-perl
0 to upgrade, 3 to newly install, 0 to remove and 0 not to upgrade.
Need to get 3,943 kB of archives.
After this operation, 30.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 liberror-perl all 0.17024-1 [23.0 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 git-man all 1:2.14.1-1ubuntu4 [790 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 git amd64 1:2.14.1-1ubuntu4 [3,130 kB]
Fetched 3,943 kB in 1s (3,911 kB/s)
Selecting previously unselected package liberror-perl.
(Reading database ... 174677 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17024-1_all.deb ...
Unpacking liberror-perl (0.17024-1) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a2.14.1-1ubuntu4_all.deb ...
Unpacking git-man (1:2.14.1-1ubuntu4) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a2.14.1-1ubuntu4_amd64.deb ...
Unpacking git (1:2.14.1-1ubuntu4) ...
Setting up git-man (1:2.14.1-1ubuntu4) ...
Setting up liberror-perl (0.17024-1) ...
Processing triggers for man-db (2.7.6.1-2) ...
Setting up git (1:2.14.1-1ubuntu4) 
makem@galaxy-book:~$ git clone https://github.com/jeremyb31/ath10k-firmware.git
Cloning into 'ath10k-firmware'...
Username for 'https://github.com': 
Password for 'https://github.com': 
remote: Repository not found.
fatal: Authentication failed for 'https://github.com/jeremyb31/ath10k-firmware.git/'

```

---

### Post by chili555 on 2018-02-09
Your internal wireless device already has a driver:> *-network                 
       description: Network controller
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 32
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: [COLOR="#FF0000"]driver=ath10k_pci [/COLOR]latency=0
       resources: irq:280 memory:df400000-df5fffffWe wonder if it needs firmware. Please open a terminal and run and post:```
dmesg | grep ath
rfkill list all
```

---

### Post by makem2 on 2018-02-09
Thank you for such a quick response.

```

makem@galaxy-book:~$ dmesg | grep ath
[    4.533658] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[    4.536393] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    4.822184] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[    4.822186] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.822608] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00051-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 c3fd4411
[    4.888061] ath10k_pci 0000:01:00.0: failed to fetch board data for bus=pci,vendor=168c,device=003e,subsystem-vendor=144d,subsystem-device=c14f from ath10k/QCA6174/hw3.0/board-2.bin
[    4.888347] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 ed5f849a
[    5.466090] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[    5.469101] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[    8.668267] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[    8.668282] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[    8.749908] ath10k_pci 0000:01:00.0: could not init core (-110)
[    8.750007] ath10k_pci 0000:01:00.0: could not probe fw (-110)
makem@galaxy-book:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
makem@galaxy-book:~$ 

```

---

### Post by chili555 on 2018-02-09
Oooh! A hard problem! Let's see if we can figure it out.

I am studying this similar problem: [http://lists.infradead.org/pipermail/ath10k/2017-October/010384.html](http://lists.infradead.org/pipermail/ath10k/2017-October/010384.html)> > [   30.882452] ath10k_pci 0000:01:00.0: failed to fetch board data for
> bus=pci,vendor=168c,device=003e,subsystem-vendor=144d,subsystem-
> device=c150 from ath10k/QCA6174/hw3.0/board-2.bin

Ok, so this means the board-2.bin file you're using is not having the 144d:c150.In your dmesg, we see: > failed to fetch board data for bus=pci,vendor=168c,device=003e,subsystem-vendor=144d,subsystem-device=c14f from ath10k/QCA6174/hw3.0/board-2.binFirst, do you actually have board-2.bin?```
ls -al /lib/firmware/ath10k/QCA6174/hw3.0
```Next, there is reference in the link above to the firmware file in Windows. Can you check on the Windows partition to see if you can find something like eeprom_ar6320_3p0_SS_620.bin and or eeprom_ar6320_3p0_SS_720_K.bin? If so, please copy them to a USB drive or similar and then to the desktop of the Ubuntu partition and let's see if we can figure out how to use it.

---

### Post by makem2 on 2018-02-09
makem@galaxy-book:~$ ls -al /lib/firmware/ath10k/QCA6174/hw3.0
total 2076
drwxr-xr-x 2 root root   4096 Feb  9 20:26 .
drwxr-xr-x 4 root root   4096 Oct 17 21:36 ..
-rw-r--r-- 1 root root 477060 Jan 25 20:23 board-2.bin
-rw-r--r-- 1 root root   8124 Mar 30  2017 board.bin
-rw-r--r-- 1 root root 733784 Mar 30  2017 firmware-4.bin
-rw-r--r-- 1 root root 727776 Jan 17 15:49 firmware-6.bin
-rw-r--r-- 1 root root  79689 Mar 30  2017 notice_ath10k_firmware-4.txt
-rw-r--r-- 1 root root  78564 Jan 17 15:49 notice_ath10k_firmware-6.txt
makem@galaxy-book:~$

---

### Post by makem2 on 2018-02-09
Both bin files are present in windows driver and are both now copied to xubuntu desktop.

EDIT: For clarity the file names are:

eeprom_ar6320_3p0_SS_620.bin

eeprom_ar6320_3p0_SS_720_K.bin

---

### Post by chili555 on 2018-02-09
I am referencing this: [http://lists.infradead.org/pipermail/ath10k/2017-September/010106.html](http://lists.infradead.org/pipermail/ath10k/2017-September/010106.html) It is, by no means, clear cut. We may need to experiment a bit.

From the terminal; first we back up the current board.bin:```
sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/board.bin /lib/firmware/ath10k/QCA6174/hw3.0/board.bak
```Next, we try the K version:```
cd ~/Desktop
sudo cp eeprom_ar6320_3p0_SS_720_K.bin board.bin
```And copy it to the firmware library:```
sudo cp board.bin  /lib/firmware/ath10k/QCA6174/hw3.0/
```Check:```
ls -al /lib/firmware/ath10k/QCA6174/hw3.0/

```You should have, among others, a board.bak and a new board.bin.

Reboot and cross your fingers and toes.

Please let us see a new:```
dmesg | grep ath
```

---

### Post by makem2 on 2018-02-09
```

makem@galaxy-book:~$ sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/board.bin /lib/firmware/ath10k/QCA6174/hw3.0/board.bak
[sudo] password for makem: 
makem@galaxy-book:~$ cd ~/Desktop
makem@galaxy-book:~/Desktop$ sudo cp eeprom_ar6320_3p0_SS_720_K.bin board.bin
makem@galaxy-book:~/Desktop$ sudo cp board.bin  /lib/firmware/ath10k/QCA6174/hw3.0/
makem@galaxy-book:~/Desktop$ ls -al /lib/firmware/ath10k/QCA6174/hw3.0/
total 2084
drwxr-xr-x 2 root root   4096 Feb  9 23:25 .
drwxr-xr-x 4 root root   4096 Oct 17 21:36 ..
-rw-r--r-- 1 root root 477060 Jan 25 20:23 board-2.bin
-rw-r--r-- 1 root root   8124 Mar 30  2017 board.bak
-rwxr-xr-x 1 root root   8124 Feb  9 23:25 board.bin
-rw-r--r-- 1 root root 733784 Mar 30  2017 firmware-4.bin
-rw-r--r-- 1 root root 727776 Jan 17 15:49 firmware-6.bin
-rw-r--r-- 1 root root  79689 Mar 30  2017 notice_ath10k_firmware-4.txt
-rw-r--r-- 1 root root  78564 Jan 17 15:49 notice_ath10k_firmware-6.txt
makem@galaxy-book:

```

---

### Post by makem2 on 2018-02-09
```

makem@galaxy-book:~$ dmesg | grep ath
[    4.542031] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[    4.543967] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    4.838413] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[    4.838415] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.838853] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00051-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 c3fd4411
[    4.904366] ath10k_pci 0000:01:00.0: failed to fetch board data for bus=pci,vendor=168c,device=003e,subsystem-vendor=144d,subsystem-device=c14f from ath10k/QCA6174/hw3.0/board-2.bin
[    4.904627] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 ad2a5746
[    5.482848] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[    5.485843] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[    5.486442] ath10k_pci 0000:01:00.0: htt-ver 3.44 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    5.573818] ath: EEPROM regdomain: 0x5f
[    5.573820] ath: EEPROM indicates we should expect a direct regpair map
[    5.573821] ath: invalid regulatory domain/country code 0x5f
[    5.573821] ath: Invalid EEPROM contents
[    5.573827] ath10k_pci 0000:01:00.0: failed to initialise regulatory: -22
[    5.573829] ath10k_pci 0000:01:00.0: could not register to mac80211 (-22)
makem@galaxy-book:~$ 


```

---

### Post by chili555 on 2018-02-10
> 5.573818] ath: EEPROM regdomain: 0x5f
[    5.573820] ath: EEPROM indicates we should expect a direct regpair map
[    5.573821] ath: invalid regulatory domain/country code 0x5f
[    5.573821] ath: Invalid EEPROM contents
[    5.573827] ath10k_pci 0000:01:00.0: failed to initialise regulatory: -22
[    5.573829] ath10k_pci 0000:01:00.0: could not register to mac80211 (-22)It appears that some errors were fixed and new errors emerged. 

The regulatory issue is discussed here: [https://patchwork.kernel.org/patch/9951857/](https://patchwork.kernel.org/patch/9951857/) The fix was to modify the code (!!) and recompile the driver (!!!), a daunting task, even for me. Let's see if we can use more reasonable methods to set the regulatory domain.
 Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Set it permanently:```
sudo nano /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Of course, substitute your country code if not Iceland. Proofread carefully, save and close the text editor.

Let's also set it in cfg80211, one of the dependencies of ath10k_pci.```
sudo -i
echo "options cfg80211 ieee80211_regdom=IS"  >  /etc/modprobe.d/cfg80211.conf
exit 
```Again, substitute your country code if not Iceland.

Reboot and cross your fingers and toes.

Please let us see a new:

```
dmesg | grep ath
```

---

### Post by makem2 on 2018-02-10
```

makem@galaxy-book:~$ sudo nano /etc/default/crda
[sudo] password for makem: 
makem@galaxy-book:~$ sudo -i
root@galaxy-book:~# echo "options cfg80211 ieee80211_regdom=GB"  >  /etc/modprobe.d/cfg80211.conf
root@galaxy-book:~# exit
logout
makem@galaxy-book:~$ dmesg | grep ath
[    4.537760] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[    4.539669] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    4.822363] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[    4.822365] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.822793] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00051-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 c3fd4411
[    4.888217] ath10k_pci 0000:01:00.0: failed to fetch board data for bus=pci,vendor=168c,device=003e,subsystem-vendor=144d,subsystem-device=c14f from ath10k/QCA6174/hw3.0/board-2.bin
[    4.888445] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 ad2a5746
[    5.467020] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[    5.470074] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[    5.470651] ath10k_pci 0000:01:00.0: htt-ver 3.44 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    5.557731] ath: EEPROM regdomain: 0x5f
[    5.557733] ath: EEPROM indicates we should expect a direct regpair map
[    5.557733] ath: invalid regulatory domain/country code 0x5f
[    5.557734] ath: Invalid EEPROM contents
[    5.557738] ath10k_pci 0000:01:00.0: failed to initialise regulatory: -22
[    5.557740] ath10k_pci 0000:01:00.0: could not register to mac80211 (-22)
makem@galaxy-book:~$

```

EDIT: Also tried  "UK"

```

makem@galaxy-book:~$ dmesg | grep ath
[    4.537760] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[    4.539669] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    4.822363] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[    4.822365] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.822793] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00051-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 c3fd4411
[    4.888217] ath10k_pci 0000:01:00.0: failed to fetch board data for bus=pci,vendor=168c,device=003e,subsystem-vendor=144d,subsystem-device=c14f from ath10k/QCA6174/hw3.0/board-2.bin
[    4.888445] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 ad2a5746
[    5.467020] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[    5.470074] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[    5.470651] ath10k_pci 0000:01:00.0: htt-ver 3.44 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    5.557731] ath: EEPROM regdomain: 0x5f
[    5.557733] ath: EEPROM indicates we should expect a direct regpair map
[    5.557733] ath: invalid regulatory domain/country code 0x5f
[    5.557734] ath: Invalid EEPROM contents
[    5.557738] ath10k_pci 0000:01:00.0: failed to initialise regulatory: -22
[    5.557740] ath10k_pci 0000:01:00.0: could not register to mac80211 (-22)
makem@galaxy-book:~$

```

Also tried "GB-United Kingdom"

---

### Post by chili555 on 2018-02-10
Do you have eeprom_ar6320_3p0_SS_720.bin on your Windows partition; in other words, not the K variant? If so, please transfer it, too and let's experiment.

On the assumption that you do, please back up the current board.bin:
```
sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/board.bin /lib/firmware/ath10k/QCA6174/hw3.0/board.Kbak
```
Next, we try the non-K version:
```
cd ~/Desktop
sudo cp eeprom_ar6320_3p0_SS_720.bin board.bin
```
And copy it to the firmware library:
```
sudo cp board.bin  /lib/firmware/ath10k/QCA6174/hw3.0/
```
Check:

```
ls -al /lib/firmware/ath10k/QCA6174/hw3.0/
```
You should have, among others, a board.bak, boardK.bak and a new board.bin.

I am interested in the differences, if any:```
cd /lib/firmware/ath10k/QCA6174/hw3.0
md5sum *
```

You know the rest.

---

### Post by makem2 on 2018-02-10
Note that the bin files I obtained from windows are both 620, not 720 as your instructions gave. I have used the 620 non K bin file:

```

makem@galaxy-book:~$ sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/board.bin /lib/firmware/ath10k/QCA6174/hw3.0/board.Kbak
[sudo] password for makem: 
makem@galaxy-book:~$ cd ~/Desktop
makem@galaxy-book:~/Desktop$ sudo cp eeprom_ar6320_3p0_SS_720.bin board.bin
cp: cannot stat 'eeprom_ar6320_3p0_SS_720.bin': No such file or directory
makem@galaxy-book:~/Desktop$ sudo cp eeprom_ar6320_3p0_SS_620.bin board.bin
makem@galaxy-book:~/Desktop$ sudo cp board.bin  /lib/firmware/ath10k/QCA6174/hw3.0/
makem@galaxy-book:~/Desktop$ ls -al /lib/firmware/ath10k/QCA6174/hw3.0/
total 2092
drwxr-xr-x 2 root root   4096 Feb 10 16:03 .
drwxr-xr-x 4 root root   4096 Oct 17 21:36 ..
-rw-r--r-- 1 root root 477060 Jan 25 20:23 board-2.bin
-rw-r--r-- 1 root root   8124 Mar 30  2017 board.bak
-rwxr-xr-x 1 root root   8124 Feb 10 16:03 board.bin
-rwxr-xr-x 1 root root   8124 Feb  9 23:25 board.Kbak
-rw-r--r-- 1 root root 733784 Mar 30  2017 firmware-4.bin
-rw-r--r-- 1 root root 727776 Jan 17 15:49 firmware-6.bin
-rw-r--r-- 1 root root  79689 Mar 30  2017 notice_ath10k_firmware-4.txt
-rw-r--r-- 1 root root  78564 Jan 17 15:49 notice_ath10k_firmware-6.txt
makem@galaxy-book:~/Desktop$ cd /lib/firmware/ath10k/QCA6174/hw3.0
makem@galaxy-book:/lib/firmware/ath10k/QCA6174/hw3.0$ md5sum *
46fc22f0fe0e1b10fa85318da203d149  board-2.bin
cb37c63d9ca28f53fea1ff09ad7c7a82  board.bak
687f24c87a77923b9fb6865bc378732e  board.bin
e97f510901331683fa8711677428d668  board.Kbak
a5dfbc03c9a7a73f7aa8d0a94a6d9426  firmware-4.bin
fcdc7ffe6226f0c94268933ff1d7a4bb  firmware-6.bin
8f22a7c04aa733762c0ad03e52d5de9b  notice_ath10k_firmware-4.txt
1996ef26689766a457043339661141c2  notice_ath10k_firmware-6.txt
makem@galaxy-book:/lib/firmware/ath10k/QCA6174/hw3.0$

```

---

### Post by makem2 on 2018-02-10
```

makem@galaxy-book:/$ dmesg | grep ath
[    3.447853] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[    3.450078] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    3.738463] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[    3.738465] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    3.738898] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00051-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 c3fd4411
[    3.804330] ath10k_pci 0000:01:00.0: failed to fetch board data for bus=pci,vendor=168c,device=003e,subsystem-vendor=144d,subsystem-device=c14f from ath10k/QCA6174/hw3.0/board-2.bin
[    3.804547] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 ad2a5746
[    4.389023] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[    4.392040] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[    4.397731] ath10k_pci 0000:01:00.0: htt-ver 3.44 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    4.490210] ath: EEPROM regdomain: 0x5f
[    4.490212] ath: EEPROM indicates we should expect a direct regpair map
[    4.490213] ath: invalid regulatory domain/country code 0x5f
[    4.490213] ath: Invalid EEPROM contents
[    4.490235] ath10k_pci 0000:01:00.0: failed to initialise regulatory: -22
[    4.490256] ath10k_pci 0000:01:00.0: could not register to mac80211 (-22)
makem@galaxy-book:/$ 

```

---

### Post by chili555 on 2018-02-10
> Note that the bin files I obtained from windows are both 620, not 720 as your instructions gave. I have used the 620 non K bin file:Your post #6 suggests 720. Are there both 620 and 620_K and 720 and 720_K files available?

I am quickly running out of ideas, mojo, ammo.

---

### Post by makem2 on 2018-02-10
I have searched for the eeprom_ar6320_3p0_SS_720.bin file in widows to be sure and it does not exist.

Reading the thread you mentioned:

[https://patchwork.kernel.org/patch/9951857/](https://patchwork.kernel.org/patch/9951857/)

I see that his machine is identical to mine except for the RAM amount and maybe SSD size. I would think the 'internals' would be otherwise identical.

---

### Post by makem2 on 2018-02-10
> **chili555 said:**
> Your post #6 suggests 720. Are there both 620 and 620_K and 720 and 720_K files available?

I am quickly running out of ideas, mojo, ammo.

Extract from my post #6:

[COLOR=#000000]EDIT: For clarity the file names are:[/COLOR]

[COLOR=#000000]eeprom_ar6320_3p0_SS_620.bin[/COLOR]

[COLOR=#000000]eeprom_ar6320_3p0_SS_720_K.bin

[/COLOR]You asked that I tried the K file and I did so. You then asked that I try the non K file which as shown above is 620.

I tried [COLOR=#000000]eeprom_ar6320_3p0_SS_620.bin[/COLOR]

Sorry if I am wrong somewhere.

Edit: I found that above I wrongly referred to BOTH files being 620, sorry. I hope the explanation above resolves the confusion.

---

### Post by chili555 on 2018-02-10
Please note that his dmesg said:> failed to fetch board data for bus=pci,vendor=168c,device=003e,subsystem-vendor=144d,subsystem-device=c14f,[COLOR="#FF0000"]variant=K[/COLOR] from ath10k/QCA6174/hw3.0/board-2.binBut yours says:> failed to fetch board data for bus=pci,vendor=168c,device=003e,subsystem-vendor=144d,subsystem-device=c14f from ath10k/QCA6174/hw3.0/board-2.binIn other words, no Variant K. 

The referenced link suggests editing the code for drivers/net/wireless/ath/regd_common.h to add the missing regulatory domain/country code 0x5f. I have no suggestions as to how to accomplish this.

I do note that the latest kernel versions, 4.15.2 does not contain the patch: [https://elixir.free-electrons.com/linux/latest/source/drivers/net/wireless/ath/regd_common.h](https://elixir.free-electrons.com/linux/latest/source/drivers/net/wireless/ath/regd_common.h) Therefore, I assume that installing a newer mainline kernel version would be ineffective.

I am now wondering if we can edit the board.bin file. Studying...

---

### Post by jeremy31 on 2018-02-10
I added the patch to backports so we can try
```
sudo apt install git build-essential
git clone https://github.com/jeremyb31/backports-4.14.git
cd backports-4.14
make defconfig-wifi
make
sudo make install
```
Reboot

After kernel updates you will have issues until you
```
cd backports-4.14
make clean
make defconfig-wifi
make
sudo make install
```
Reboot

---

### Post by makem2 on 2018-02-10
All completed without apparent error except I did notice:

cc -Wall -Wmissing prototypes etc.

I do have the full output if needed.

However, crossing fingers and toes had no effect I am afraid. I am typing this on another linux machine because the tablet no longer has WiFi access with or without the dongle.

I can do a [COLOR=#000000][FONT=&quot]dmesg | grep ath and transfer it here?[/FONT][/COLOR]

---

### Post by jeremy31 on 2018-02-10
Post the full output, you can remove the changes by
```
cd backports-4.14
sudo make uninstall
```
Reboot

---

### Post by makem2 on 2018-02-10
This is where I saw apparent errors :

```

makem@galaxy-book:~$ cd backports-4.14
makem@galaxy-book:~/backports-4.14$ make clean
  CLEAN   /home/makem/backports-4.14/.tmp_versions
  CLEAN   /home/makem/backports-4.14/Module.symvers
makem@galaxy-book:~/backports-4.14$ make defconfig-wifi
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
warning: (USB_ALI_M5632 && USB_AN2720 && USB_BELKIN && USB_ARMLINUX && USB_EPSON2888 && USB_KC2190) selects USB_NET_CDC_SUBSET_ENABLE which has unmet direct dependencies (USB_NET_DRIVERS && n && m && BP_MODULES && USB_NET_CDC_SUBSET)
warning: (USB_ALI_M5632 && USB_AN2720 && USB_BELKIN && USB_ARMLINUX && USB_EPSON2888 && USB_KC2190) selects USB_NET_CDC_SUBSET_ENABLE which has unmet direct dependencies (USB_NET_DRIVERS && n && m && BP_MODULES && USB_NET_CDC_SUBSET)
#
# configuration written to .config
#
makem@galaxy-book:~/backports-4.14$

```

---

### Post by makem2 on 2018-02-10
> **jeremy31 said:**
> Post the full output, you can remove the changes by
```
cd backports-4.14
sudo make uninstall
```
Reboot

Do you want the output ([COLOR=#000000]dmesg | grep ath[/COLOR]) before or after removing the changes?

---

### Post by jeremy31 on 2018-02-10
Actually did you run all the commands even sudo make install?  Some of those errors might be normal in the newer backports

---

### Post by makem2 on 2018-02-10
> **jeremy31 said:**
> Actually did you run all the commands even sudo make install?  Some of those errors might be normal in the newer backports

I copy/pasted every command.

I just did a dmesg | grep ath and it retuned empty.

EDIT: Yes, I carried out the initial sudo make install, rebooted and then followed with the second make install and reboot.

---

### Post by jeremy31 on 2018-02-10
Do you have dmesg | grep ath output from when the backports were used?  I am using the backports now with my ath9k Atheros wifi in 17.10 with the 4.13.0-32 kernel
Is there a way to access BIOS/UEFI to see if Secure Boot is disabled?

---

### Post by makem2 on 2018-02-10
No, but i will get a [COLOR=#000000]dmesg | grep ath

Fast boot is disabled. Secure boot? If there is such a thing I will find it.[/COLOR]

---

### Post by makem2 on 2018-02-10
Secure boot was on and is now off. Fast BIOS was also on and is now off.

I have WiFi via the dongle now.

I will try removing and reboot.

---

### Post by makem2 on 2018-02-10
WiFi is working correctly and I am now able to use 5GHz.

Thank you for your assistance and patience.

Do you still require the dmesg?

---

### Post by jeremy31 on 2018-02-10
If the internal Atheros card is working, I do not require the dmesg

---

### Post by chili555 on 2018-02-10
> **makem2 said:**
> WiFi is working correctly and I am now able to use 5GHz.

Thank you for your assistance and patience.

Do you still require the dmesg?Woo hoo! Glad it's working and very, very grateful for Jeremy's very skillful assistance. Thank you!

Please use thread tools at the top to mark Solved. The searchers will appreciate it. As you saw, we used Google extensively to find clues and a solved thread will help others.

Thanks again, Jeremy.

---

### Post by jeremy31 on 2018-02-10
Trying to get some answers on IRC from the ath10k devs on why the patch isn't committed yet...nothing but silence so far and the infradead mailing list seems down

Not a problem chili555, glad makem2 has working wifi

---

### Post by office-liquid-light on 2018-04-04
Hi Chilli555, hi Jeremy31,

I run into the same problem makem2 and several other had with the QCA6174. I got a fail with a slightly different version because I use the Samsung book 10,6:

[   19.746598] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c150
but in the end got the same problem with
EEPROM regdomain: 0x5f

Anyways, the Backport-4.14 from Jeremy31 worked for me with the Ubuntu version 16.04, but I switched to the beta 18.04 because of missing energy saving and standby mode with 16.04. I tried the Backport-4.14 but that didn't work. Now I sit here, reading lots of threads and mailing lists but I'm not able to solve the problem. Cloud you guys help me?
Thanks in advance.
Yu Kei

---

### Post by jeremy31 on 2018-04-07
You could try this
```
sudo apt-get install git build-essential
git clone https://github.com/jeremyb31/ath-4.15.git
cd ath-4.15
cp /usr/src/$(uname -r)/.config ./
cp /usr/src/$(uname -r)/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp ath.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath
```
Reboot

After other kernel updates you will need to do 
```

cd ath-4.15
make -C /lib/modules/$(uname -r)/build M=$(pwd) clean
cp /usr/src/$(uname -r)/.config ./
cp /usr/src/$(uname -r)/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp ath.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath
```

---

### Post by office-liquid-light on 2018-04-10
**Yes, yes, yes**, don't ask me what you did, but at least it worked. 

To make it work, I change this two lines from:   

```
cp /usr/lib/modules/$(uname -r)/build/.config ./ 
cp /usr/lib/modules/$(uname -r)/build/Module.symvers ./  
```
to  

```
cp /lib/modules/$(uname -r)/build/.config ./ 
cp /lib/modules/$(uname -r)/build/Module.symvers ./  
```
and I cloud swear that in this instruction **"sudo cp ath.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath"** - the directory after kernel -> **drivers/net/wireless/ath** didn't exist. So I copied the ath.ko file manually to "/lib/modules/$(uname -r)/**build**/drivers/net/wireless/ath". 
After a reboot that didn't work, but executing "sudo cp ath.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath" worked and after a second reboot I had a working wifi. 

 I wright this just in case someone else might run into the same problems.  Again, thank a lot. Someone on the other end of the line is happy.

---

### Post by devrikx on 2018-04-24
> **jeremy31 said:**
> You could try this
```
sudo apt-get install git build-essential
git clone https://github.com/jeremyb31/ath-4.15.git
cd ath-4.15
cp /usr/lib/modules/$(uname -r)/build/.config ./
cp /usr/lib/modules/$(uname -r)/build/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp ath.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath
```
Reboot

After other kernel updates you will need to do 
```

cd ath-4.15
make -C /lib/modules/$(uname -r)/build M=$(pwd) clean
cp /usr/lib/modules/$(uname -r)/build/.config ./
cp /usr/lib/modules/$(uname -r)/build/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp ath.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath
```

I'm a dedicated **Debian** user running the **Buster** branch, utilizing the **4.15**.2 Kernel.  

I've tried for over 2 months now to get the **Atheros QCA6174 WiFi **working on my **Samsung Galaxy Book 12**.  *This solution worked for me*.

I've followed many a guide, building dkms from source, trying several different git user's repositories and several different drivers, yet none of them worked. 

 I did have to drop `*/usr*` for the `*cp*` steps, as another user stated, but otherwise it was flawless - not a single error.
```

cp /lib/modules/$(uname -r)/build/.config ./
cp /lib/modules/$(uname -r)/build/Module.symvers ./

```
---

I about cried when I spent 3 minutes following these instructions.....and rebooted to the WiFi actually being enabled and waiting on *me* to select a network - I'm currently posting this on my Galaxy Book's built-in wifi.

---

I have everything except for the built-in 4glte (which doesnt even so much as show up as a piece of hardware in any command I run, lspci, lsusb, etc), and speakers (though bluetooth sound works in HDP and a2dp mode).  The pen, touch, pressure, and multi-gesture (screen and touchpad) and now the wifi...all working. 

I've been plugging my phone in everywhere I go to get internet on this thing and now I can finally use it with its built-in wifi.  Thank you so much.  I made an account on this forum to pay my respect. Hands down, you rock Jeremy31!


Would you mind explaining what the actual problem was, or what you changed in the source that was the problem with the firmware?  No worries if not. If there is someplace specifically I can bump to get your changes included upstream(?), where would that be?  

Thanks again, its amazing how simple you made this fix.  I will link to this post and tattoo the instructions on my arm (i kid).  


Lastly, if you could get the 4glte working, I'd definitely buy you a beer at the least!

---

### Post by office-liquid-light on 2018-05-30
Hi devrix,

as far as I understood, this is a forgotten countrycode !!! Forgotten for the last two year and future version. Don't laugh, there are patches for the whole 4.16 kernel and may be more. At least I wrote a bug report for launchpad but as far as I could see it's a kernel.org thing. Sound is not country related but also a kernel.org thing. I didn't open a bug report till now.

Well, with the file 'regd_common.h' that contains wrong country codes (regdomain: 0x5f - island?). There are some report hanging around. So Carsten Haitzler a.k. Rasterman (entlightenment desktop) run into the same problem. But he needed seconds to solve the problem where we need additional help. See:
 [https://patchwork.kernel.org/patch/9951857/](https://patchwork.kernel.org/patch/9951857/)

---

### Post by aytony19 on 2018-07-07
> **devrikx said:**
> I'm a dedicated **Debian** user running the **Buster** branch, utilizing the **4.15**.2 Kernel.  

I've tried for over 2 months now to get the **Atheros QCA6174 WiFi **working on my **Samsung Galaxy Book 12**.  *This solution worked for me*.

I've followed many a guide, building dkms from source, trying several different git user's repositories and several different drivers, yet none of them worked. 

 I did have to drop `*/usr*` for the `*cp*` steps, as another user stated, but otherwise it was flawless - not a single error.
```

cp /lib/modules/$(uname -r)/build/.config ./
cp /lib/modules/$(uname -r)/build/Module.symvers ./

```
---

I about cried when I spent 3 minutes following these instructions.....and rebooted to the WiFi actually being enabled and waiting on *me* to select a network - I'm currently posting this on my Galaxy Book's built-in wifi.

---

I have everything except for the built-in 4glte (which doesnt even so much as show up as a piece of hardware in any command I run, lspci, lsusb, etc), and speakers (though bluetooth sound works in HDP and a2dp mode).  The pen, touch, pressure, and multi-gesture (screen and touchpad) and now the wifi...all working. 

I've been plugging my phone in everywhere I go to get internet on this thing and now I can finally use it with its built-in wifi.  Thank you so much.  I made an account on this forum to pay my respect. Hands down, you rock Jeremy31!


Would you mind explaining what the actual problem was, or what you changed in the source that was the problem with the firmware?  No worries if not. If there is someplace specifically I can bump to get your changes included upstream(?), where would that be?  

Thanks again, its amazing how simple you made this fix.  I will link to this post and tattoo the instructions on my arm (i kid).  


Lastly, if you could get the 4glte working, I'd definitely buy you a beer at the least!

I have a Galaxy Book and this worked for me! At least until I did an update. Ever-since, I have been unable to get my wifi working again. Long story short, I am now using a different Ubuntu flavor (I am still very very new to all of this) with a fresh install. When I try to follow the above steps, I get errors about implicit declarations of functions in the "ar5523.c" file. Any advice? Thanks!

---

### Post by aytony19 on 2018-07-14
I know this isn't helpful, so I am sorry. However, my issue has been resolved. I went through the entire thread, re-did everything that I had previously tried, got all the same error messages, but this time, my wifi drivers seem happy to do their job. The only guess I have is running this current batch of updates (I didn't note which where installed sadly; the price of multitasking) seemed to help. Regardless, thanks for all of this information and help.

---

### Post by devrikx on 2018-09-01
I've been following **[jeremyb31]("https://ubuntuforums.org/member.php?u=1924242")**'s directions - successfully - for quite some time now. His solution has worked flawlessly for my Samsung Galaxy Book 12, which is running Debian Buster. I've even posted tweaks to the instructions for Debian users just to ease the process for newcomers to the issue.

Unfortunately, as of kernel version 4.17 the solution (as-is) stops working - due to an error which occurs during the build process. 

The error occurs because of the following function call made in *cfg80211.c*, found at *line 1599* within the *wil6210* directory of the source for the Atheros kernel driver - which is picked from the pre-4.17 linux kernel source tree:

```

cfg80211_probe_status(ndev, sta->addr, req->cookie, alive, GFP_KERNEL);

```

The API for the method has since been updated to accept 2 additional arguments:

```


cfg80211_probe_status(ndev, sta->addr, req->cookie, alive,
                  0, false, GFP_KERNEL);

```


For my own use-case, I merged the updated **wil6210** directory from the **[latest 4.17 linux kernel source tree]("https://www.kernel.org/pub/linux/kernel/v4.x/linux-4.17.tar.xz")** with the modified source provided by jeremyb31 - and it seems to be working perfectly. Whatever changes he made were not within that directory.

Additionally, **[I created a repository on Github]("https://github.com/devrikx/atheros")** where I'm hosting the updated source code for kernel version 4.17 - as well as the older source for kernel versions 4.15 and 4.16 (on named branches, respectively). The repository's README is also loaded with instructions for walking users through the process of getting their wifi working.
Before long I'll have figured out the changes made to the older source, and will transpile (my, how terms change :popcorn: ) them into the newer Atheros source from the latest kernel source tree.


For an expedited set of [debian] instructions without leaving ubuntuforums - if you are using kernel version 4.17:

```

sudo apt-get install git build-essential
git clone https://github.com/devrikx/atheros
cd atheros
cp /lib/modules/$(uname -r)/build/.config ./
cp /lib/modules/$(uname -r)/build/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp ath.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath

```

Reboot

When a kernel update happens, the wifi will break - at which point you'll need to perform the following:

```

cd atheros
make -C /lib/modules/$(uname -r)/build M=$(pwd) clean
cp /lib/modules/$(uname -r)/build/.config ./
cp /lib/modules/$(uname -r)/build/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp ath.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath

```


**NOTE **- On Ubuntu, just prepend */usr* to */lib/modules/$(uname -r)/build/.config* and */lib/modules/$(uname -r)/build/Module.symvers *copy commands.

**MANY THANKS** - To jeremyb31 for having provided the source and instructions to get wifi working on my Samsung Galaxy Book 12 :)

---

### Post by testing990 on 2018-11-04
Hello,

I haven now installed Ubuntu 18.10 and Kernal 4.18 is in use.
on a general note, sound is only working via bluetooth and the cameras not at all.

The path of the folders for the CP commands do not need prepending of /usr it seems, as the the directory will not be found.

Anyhow, I do get this error, both on the git for the 4.16 and 4.17 kernel. how can i fix this?

(the incompatible pointer type points to the = symbol)

~/atheros$ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
make: Entering directory '/usr/src/linux-headers-4.18.0-10-generic'
  CC [M]  /home/computer/atheros/ath9k/main.o
/home/computer/atheros/ath9k/main.c: In function &#8216;ath9k_fill_chanctx_ops&#8217;:
/home/computer/atheros/ath9k/main.c:2635:37: error: assignment to &#8216;void (*)(struct ieee80211_hw *, struct ieee80211_vif *, u16)&#8217; {aka &#8216;void (*)(struct ieee80211_hw *, struct ieee80211_vif *, short unsigned int)&#8217;} from incompatible pointer type &#8216;void (*)(struct ieee80211_hw *, struct ieee80211_vif *)&#8217; [-Werror=incompatible-pointer-types]
  ath9k_ops.mgd_prepare_tx           = ath9k_mgd_prepare_tx;
                                     ^
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:327: /home/computer/atheros/ath9k/main.o] Error 1
make[1]: *** [scripts/Makefile.build:581: /home/computer/atheros/ath9k] Error 2
make: *** [Makefile:1546: _module_/home/computer/atheros] Error 2
make: Leaving directory '/usr/src/linux-headers-4.18.0-10-generic'
computer@computer:~/atheros$

---

### Post by chili555 on 2018-11-04
> **testing990 said:**
> Hello,

I haven now installed Ubuntu 18.10 and Kernal 4.18 is in use.
on a general note, sound is only working via bluetooth and the cameras not at all.

<snip>
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:327: /home/computer/atheros/ath9k/main.o] Error 1
make[1]: *** [scripts/Makefile.build:581: /home/computer/atheros/ath9k] Error 2
make: *** [Makefile:1546: _module_/home/computer/atheros] Error 2
make: Leaving directory '/usr/src/linux-headers-4.18.0-10-generic'
computer@computer:~/atheros$
The original post was concerning an ath10k_pci device. You have, or suspect you have, an ath9k device. They are entirely different.

The driver ath9k is present in Ubuntu 18.10. If it is not working as expected, then installing an older, less developed driver isn't going to help.

Please start a new question and include the diagnostics from here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by testing990 on 2018-11-05
Hello, thank you for the swift reply!

This is for the Samsung Galaxy Book 10.6. In the Ubuntu 18.10 installation, it says "no wifi adapter found"

I am sad to now understand they gave it an older wifi device, i could not afford the larger galaxy book.

---

### Post by chili555 on 2018-11-05
> **testing990 said:**
> Hello, thank you for the swift reply!

This is for the Samsung Galaxy Book 10.6. In the Ubuntu 18.10 installation, it says "no wifi adapter found"

I am sad to now understand they gave it an older wifi device, i could not afford the larger galaxy book.As I said, please start a new question and we’ll be very happy to help.

---

### Post by testing990 on 2018-11-12
ok thanks i posted it here:

[https://ubuntuforums.org/showthread.php?t=2405871](https://ubuntuforums.org/showthread.php?t=2405871)

and the pastebin here

[https://paste.ubuntu.com/p/P8CDXbb3Rr/](https://paste.ubuntu.com/p/P8CDXbb3Rr/)

---

### Post by testing990 on 2018-11-19
Hi @office-liquid-light , How were you able to execute the make command?
I also have the samsung galaxy book 10.6 like you do, and it seems i never get to the stage that ath.ko was actually created:

My build always aborts when doing make, and exits with the error below.
I read the error as such that there is an error in main.o but could be wrong.

 CC [M]  /home/computer/atheros/ath9k/main.o
/home/computer/atheros/ath9k/main.c: In function &#8216;ath9k_fill_chanctx_ops&#8217;:
/home/computer/atheros/ath9k/main.c:2635:37: error: assignment to &#8216;void (*)(struct ieee80211_hw *, struct ieee80211_vif *, u16)&#8217; {aka &#8216;void (*)(struct ieee80211_hw *, struct ieee80211_vif *, short unsigned int)&#8217;} from incompatible pointer type &#8216;void (*)(struct ieee80211_hw *, struct ieee80211_vif *)&#8217; [-Werror=incompatible-pointer-types]
  ath9k_ops.mgd_prepare_tx           = ath9k_mgd_prepare_tx;
                                     ^
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:327: /home/computer/atheros/ath9k/main.o] Error 1
make[1]: *** [scripts/Makefile.build:581: /home/computer/atheros/ath9k] Error 2
make: *** [Makefile:1546: _module_/home/computer/atheros] Error 2
make: Leaving directory '/usr/src/linux-headers-4.18.0-11-generic'

---

### Post by chili555 on 2018-11-19
> **testing990 said:**
> Hi @office-liquid-light , How were you able to execute the make command?
I also have the samsung galaxy book 10.6 like you do, and it seems i never get to the stage that ath.ko was actually created:

My build always aborts when doing make, and exits with the error below.
I read the error as such that there is an error in main.o but could be wrong.

 CC [M]  /home/computer/atheros/ath9k/main.o
/home/computer/atheros/ath9k/main.c: In function ‘ath9k_fill_chanctx_ops’:
/home/computer/atheros/ath9k/main.c:2635:37: error: assignment to ‘void (*)(struct ieee80211_hw *, struct ieee80211_vif *, u16)’ {aka ‘void (*)(struct ieee80211_hw *, struct ieee80211_vif *, short unsigned int)’} from incompatible pointer type ‘void (*)(struct ieee80211_hw *, struct ieee80211_vif *)’ [-Werror=incompatible-pointer-types]
  ath9k_ops.mgd_prepare_tx           = ath9k_mgd_prepare_tx;
                                     ^
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:327: /home/computer/atheros/ath9k/main.o] Error 1
make[1]: *** [scripts/Makefile.build:581: /home/computer/atheros/ath9k] Error 2
make: *** [Makefile:1546: _module_/home/computer/atheros] Error 2
make: Leaving directory '/usr/src/linux-headers-4.18.0-11-generic'The driver ath9k is not correct for your device. I suspect the driver you are trying to compile is old and incompatible with your 4.18 kernel in any event.

---

### Post by testing990 on 2018-11-19
When executing the make command, several files are generated, including ath10k, ath6 and ath5k files, before it comes to ath9k files - thats when in the terminal the make process aborts and shows the said error.  I never get a ath.ko file that i could copy.

I had used the github repository backport by Jeremy31 as well as the atheros repository described by devrikx.

Devrikx suggests to use the command

git checkout 4-XX-stable

where xx would be replaced by any other prior version, and I tried it both with 15, 16, 17 and origin. but the very same error comes, so i was only guessing in main.c would be a conflict of a boolean or int data type.

---

### Post by chili555 on 2018-11-19
> **testing990 said:**
> When executing the make command, several files are generated, including ath10k, ath6 and ath5k files, before it comes to ath9k files - thats when in the terminal the make process aborts and shows the said error.  I never get a ath.ko file that i could copy.

I had used the github repository backport by Jeremy31 as well as the atheros repository described by devrikx.

Devrikx suggests to use the command

git checkout 4-XX-stable

where xx would be replaced by any other prior version, and I tried it both with 15, 16, 17 and origin. but the very same error comes, so i was only guessing in main.c would be a conflict of a boolean or int data type.I've sent Jeremy a PM to ask for his help.

---

### Post by testing990 on 2018-11-29
I have found that his is also an ath10_k device. therefore I assume the errors originate from using the current 4.18 kernel.

What can we do?


computer@computer:~$ sudo lshw -C network
[sudo] password for computer: 
  *-network                 
       description: Network controller
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 32
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ath10k_pci latency=0
       resources: irq:128 memory:df400000-df5fffff



Can't i just use any compiled ath.ko file and copy it? The make process is awlays aborted with the error message previously posted.

---

### Post by testing990 on 2018-11-29
So after copying the board.bin file from killernetworking.com, as described here:

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1804028](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1804028)

i got it to work after a reboot, but not with the here presented solutions.

---

### Post by space-shell on 2018-12-17
> **testing990 said:**
> So after copying the board.bin file from killernetworking.com, as described here:

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1804028](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1804028)

i got it to work after a reboot, but not with the here presented solutions.

I can confirm that this solution has worked for me.

I had deleted the original `board-2.bin` and copied the `eeprom_ar6320_3p0_TX8_clpc.bin` file to `lib/firmware/ath10k/QCA6174/hw3.0/board.bin`

OS: Arch linux
Kernel: 4.19
Device: Samsung Galaxy Book 12

[ATTACH]281952[/ATTACH]

---

### Post by cainelliott on 2019-09-12
Thank you so much. May I also provide Jeremy with a beer for this fix.

---


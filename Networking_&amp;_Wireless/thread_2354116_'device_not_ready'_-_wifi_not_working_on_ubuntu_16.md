---
title: "'device not ready' - wifi not working on ubuntu 16.10"
date: 2017-02-28
forum: Networking &amp; Wireless
---

### Post by kurrent93 on 2017-02-28
After installing Ubuntu 16.10 on my Lenovo Thinkpad 510, the wireless is not working. In the network manager it says 'device not ready'

```
$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

```

```
$ lspci -nn | grep -e 0200 -e 0280
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]
```

I have tried:

```
$ lspci -knn | grep Net -A2
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
    Subsystem: Lenovo 82577LM Gigabit Network Connection [17aa:2153]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
```
--
```
SUSPEND_MODULES="rtl8723be" to /etc/pm/config.d/config
sudo service network-manager restart
```

```
$ sudo lshw -class network
  *-network                 
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 06
       serial: 00:26:2d:fd:f3:a8
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.12-1 ip=192.168.1.9 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:25 memory:f2400000-f241ffff memory:f2425000-f2425fff ioport:1820(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Wireless-N 1000 [Condor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: 00:26:c7:3d:a3:f6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.8.0-39-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:29 memory:f2000000-f2001fff
```


```
$ sudo rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Output from dmesg | grep iwl is on [http://pastebin.com/S2c9C3E4](http://pastebin.com/S2c9C3E4)
Running sudo modprobe -r iwlwifi && sleep 20 && sudo modprobe iwlwifi produces no output.
```
$ echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
outputs options rtl8723be fwlps=N
```

Have also tried sudo service network-manager restart but this also did not help.
```
$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```

Also tried [http://askubuntu.com/a/770714/17643](http://askubuntu.com/a/770714/17643) but this also did not work.
Also tried sudo apt-get install --reinstall linux-firmware but this also did not help.
Also, based on [https://ubuntuforums.org/showthread.php?t=2188827&p=12855191#post12855191](https://ubuntuforums.org/showthread.php?t=2188827&p=12855191#post12855191), /etc/rc.local - Im not sure if this is supposed to be empty.

---

### Post by kurrent93 on 2017-03-02
Is there any further information that I can add to help understand the problem?

---

### Post by deadflowr on 2017-03-02
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2017-03-02
> [   55.231619] iwlwifi 0000:03:00.0: Failed to run INIT ucode: -5
[   55.231630] iwlwifi 0000:03:00.0: Unable to initialize device.
[   65.191661] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.199436] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   65.199532] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[   65.208062] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.That's not at all good.

There is only one firmware file available: [http://linuxwireless.org/en/users/Drivers/iwlwifi/](http://linuxwireless.org/en/users/Drivers/iwlwifi/) The version -5 firmware is the one that you have and is loaded. I think there are two possibilities; first, that the firmware file you have is corrupted, or, second, that the hardware itself, the chip, is defective.

Let's check the firmware:```
ls -al /lib/firmware/iwlwifi-1000-5.ucode
```On my machine, I get:```
-rw-r--r-- 1 root root [COLOR="#FF0000"]337520 [/COLOR]Apr 25  2016 /lib/firmware/iwlwifi-1000-5.ucode
```Let's also check its integrity:```
md5sum /lib/firmware/iwlwifi-1000-5.ucode 
```I get:```
[COLOR="#FF0000"]9f81a060ed274f76cd605295da77f7a6 [/COLOR] /lib/firmware/iwlwifi-1000-5.ucode

```If you get a different result for either or both the size or the md5sum, we'll update your firmware.

Next, as to whether the hardware itself is at fault, please try a live session of Ubuntu 14.04 LTS or Mint or any other recent Linux version. Does your wireless work there?

---

### Post by kurrent93 on 2017-03-03
```
$ ls -al /lib/firmware/iwlwifi-1000-5.ucode
-rw-r--r-- 1 root root 337520 Feb 26 21:27 /lib/firmware/iwlwifi-1000-5.ucode

```

```
$ md5sum /lib/firmware/iwlwifi-1000-5.ucode
9f81a060ed274f76cd605295da77f7a6  /lib/firmware/iwlwifi-1000-5.ucode

```

Additional info - [http://paste.ubuntu.com/24101344/](http://paste.ubuntu.com/24101344/)

Will check live CD....

---

### Post by kurrent93 on 2017-03-03
Ok I tried with Mint live CD but it also would not work.
I then swapped the harddrive for a windows harddrive and the wireless does work on Windows.
So its not faulty hardware.

---

### Post by chili555 on 2017-03-03
In researching your issue, I came upon this interesting thread: [https://ubuntuforums.org/showthread.php?t=1941350](https://ubuntuforums.org/showthread.php?t=1941350) The crazy lunatic suggested downgrading your firmware! Crazy, eh? However, the issue was solved. Let's try it. With a working internet connection by ethernet, tethered or whatever means possible:```
wget https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-1000-ucode-128.50.3.1.tgz
tar zxvf iwlwifi-1000-ucode-128.50.3.1.tgz
cd iwlwifi-1000-ucode-128.50.3.1
sudo cp iwlwifi-1000-3.ucode  /lib/firmware
```Now, let's rename your existing firmware so it doesn't load; we can easily change it back, if needed:```
cd /lib/firmware
sudo mv iwlwifi-1000-5.ucode  iwlwifi-1000-5.bak
```Reboot and let us see:```
dmesg | grep iwl
```

---

### Post by shreshth on 2017-10-28
I recently installed 12.04 on an old laptop. My wireless network shows device no ready too.

```
sudo lshw -class network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:87:6a:32
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945  driverversion=3.13.0-117-generic firmware=15.32.2.9 latency=0 link=no  multicast=yes wireless=IEEE 802.11abg
       resources: irq:42 memory:b0200000-b0200fff

```

```
dmesg | grep iwl3945
[   13.603062] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   13.603063] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   13.603130] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   13.648008] Modules linked in: snd_hda_codec iwl3945(+) iwlegacy  snd_hwdep snd_pcm mac80211 i915(+) r852 snd_seq_midi sm_common nand  snd_rawmidi mtd btusb snd_seq_midi_event nand_ids cfg80211 nand_bch  snd_seq bluetooth pcmcia snd_seq_device bch joydev drm_kms_helper drm  snd_timer r592 nand_ecc yenta_socket memstick snd soundcore pcmcia_rsrc  snd_page_alloc pcmcia_core i2c_algo_bit lpc_ich psmouse shpchp serio_raw  video mac_hid coretemp lp parport pata_acpi sdhci_pci 8139too sdhci  8139cp firewire_ohci mii firewire_core crc_itu_t
[   13.648008]  [<f8889e6c>] il3945_apm_init+0x2c/0x130 [iwl3945]
[   13.648008]  [<f8887d0d>] il3945_pci_probe+0x18d/0x4a0 [iwl3945]
[   13.648008]  [<f8853050>] il3945_init+0x50/0x1000 [iwl3945]
[   13.781168] iwl3945 0000:03:00.0: Master Disable Timed Out, 100 usec
[   13.781355] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.781358] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   13.781436] iwl3945 0000:03:00.0: irq 42 for MSI/MSI-X
[   13.781643] iwl3945 0000:03:00.0: Hardware error detected.  Restarting.
[   13.781646] iwl3945 0000:03:00.0: Loaded firmware version: 
[   13.781649] iwl3945 0000:03:00.0: Not valid error log pointer 0x00000000
[   25.033375] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   25.938109] iwl3945 0000:03:00.0: Hardware error detected.  Restarting.
[   25.938120] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[   25.938125] iwl3945 0000:03:00.0: Not valid error log pointer 0x00000000
[   26.083032] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   26.083037] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   26.228033] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   26.228037] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   26.373000] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   26.373005] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   26.517979] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   26.517983] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   26.662950] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   26.662954] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   26.666943] iwl3945 0000:03:00.0: Master Disable Timed Out, 100 usec
[   26.668202] iwl3945 0000:03:00.0: Unable to initialize device after 5 attempts.
[   28.002482] iwl3945 0000:03:00.0: Hardware error detected.  Restarting.
[   28.002491] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[   28.002496] iwl3945 0000:03:00.0: Not valid error log pointer 0x00000000
[   28.147460] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   28.147467] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   28.292473] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   28.292479] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   28.437494] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   28.437500] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   28.582505] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   28.582512] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   28.727496] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   28.727502] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   28.731487] iwl3945 0000:03:00.0: Master Disable Timed Out, 100 usec
[   28.732825] iwl3945 0000:03:00.0: Unable to initialize device after 5 attempts.
[   29.639741] iwl3945 0000:03:00.0: Hardware error detected.  Restarting.
[   29.639753] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[   29.639757] iwl3945 0000:03:00.0: Not valid error log pointer 0x00000000
[   29.784718] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   29.784726] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   29.929735] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   29.929742] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   30.074715] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   30.074722] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   30.219688] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   30.219694] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   30.364658] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[   30.364663] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[   30.368650] iwl3945 0000:03:00.0: Master Disable Timed Out, 100 usec
[   30.369985] iwl3945 0000:03:00.0: Unable to initialize device after 5 attempts.
[ 1133.748735] iwl3945 0000:03:00.0: Hardware error detected.  Restarting.
[ 1133.748745] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[ 1133.748750] iwl3945 0000:03:00.0: Not valid error log pointer 0x00000000
[ 1133.893915] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1133.893924] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1134.039043] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1134.039050] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1134.184085] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1134.184092] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1134.329134] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1134.329141] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1134.474156] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1134.474163] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1134.478142] iwl3945 0000:03:00.0: Master Disable Timed Out, 100 usec
[ 1134.479489] iwl3945 0000:03:00.0: Unable to initialize device after 5 attempts.
[ 1135.389125] iwl3945 0000:03:00.0: Hardware error detected.  Restarting.
[ 1135.389143] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[ 1135.389148] iwl3945 0000:03:00.0: Not valid error log pointer 0x00000000
[ 1135.534121] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1135.534130] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1135.679159] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1135.679167] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1135.824181] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1135.824188] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1135.969204] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1135.969211] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1136.114258] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1136.114265] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1136.118237] iwl3945 0000:03:00.0: Master Disable Timed Out, 100 usec
[ 1136.119605] iwl3945 0000:03:00.0: Unable to initialize device after 5 attempts.
[ 1137.026767] iwl3945 0000:03:00.0: Hardware error detected.  Restarting.
[ 1137.026778] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[ 1137.026783] iwl3945 0000:03:00.0: Not valid error log pointer 0x00000000
[ 1137.171396] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1137.171405] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1137.316093] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1137.316101] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1137.460787] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1137.460794] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1137.605486] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1137.605493] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1137.750162] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1137.750169] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1137.754149] iwl3945 0000:03:00.0: Master Disable Timed Out, 100 usec
[ 1137.755486] iwl3945 0000:03:00.0: Unable to initialize device after 5 attempts.
[ 1406.545345] iwl3945 0000:03:00.0: Hardware error detected.  Restarting.
[ 1406.545364] iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[ 1406.545370] iwl3945 0000:03:00.0: Not valid error log pointer 0x00000000
[ 1406.690322] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1406.690328] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1406.835417] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1406.835422] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1406.980475] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1406.980481] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1407.125521] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1407.125527] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1407.270575] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a0, s/b 0xf802020
[ 1407.270580] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[ 1407.274567] iwl3945 0000:03:00.0: Master Disable Timed Out, 100 usec
[ 1407.275931] iwl3945 0000:03:00.0: Unable to initialize device after 5 attempts.

```

Kindly help?

---

### Post by chili555 on 2017-10-28
> **shreshth said:**
> I recently installed 12.04 on an old laptop. My wireless network shows device no ready too.

```
sudo lshw -class network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:87:6a:32
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945  driverversion=3.13.0-117-generic firmware=15.32.2.9 latency=0 link=no  multicast=yes wireless=IEEE 802.11abg
       resources: irq:42 memory:b0200000-b0200fff

```

```
dmesg | grep iwl3945
[   13.603062] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   13.603063] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   13.603130] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   13.648008] Modules linked in: snd_hda_codec iwl3945(+) iwlegacy  snd_hwdep snd_pcm mac80211 i915(+) r852 snd_seq_midi sm_common nand  snd_rawmidi mtd btusb snd_seq_midi_event nand_ids cfg80211 nand_bch  snd_seq bluetooth pcmcia snd_seq_device bch joydev drm_kms_helper drm  snd_timer r592 nand_ecc yenta_socket memstick snd soundcore pcmcia_rsrc  snd_page_alloc pcmcia_core i2c_algo_bit lpc_ich psmouse shpchp serio_raw  video mac_hid coretemp lp parport pata_acpi sdhci_pci 8139too sdhci  8139cp firewire_ohci mii firewire_core crc_itu_t
[   13.648008]  [<f8889e6c>] il3945_apm_init+0x2c/0x130 [iwl3945]
[   13.648008]  [<f8887d0d>] il3945_pci_probe+0x18d/0x4a0 [iwl3945]
[   13.648008]  [<f8853050>] il3945_init+0x50/0x1000 [iwl3945]
[   13.781168] iwl3945 0000:03:00.0: Master Disable Timed Out, 100 usec
[   13.781355] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.781358] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   13.781436] iwl3945 0000:03:00.0: irq 42 for MSI/MSI-X
<snip>
[ 1407.275931] iwl3945 0000:03:00.0: Unable to initialize device after 5 attempts.

```

Kindly help?Ubuntu 12.04 is not only beyond its end-of-life, but it is 5 1/2 years old. We've made a lot of progress in drivers in that time.

None of us here have a 12.04 installation with which we can guide you.

Finally, please don't hijack an old thread when you have a merely similar but not identical problem.

Please install 14.04LTS or 16.04LTS or newer and start your own new question.

---


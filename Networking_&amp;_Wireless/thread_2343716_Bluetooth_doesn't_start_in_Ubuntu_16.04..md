---
title: "Bluetooth doesn't start in Ubuntu 16.04."
date: 2016-11-18
forum: Networking &amp; Wireless
---

### Post by exodd on 2016-11-18
Hello, everyone.

I recently installed Ubuntu 16.04 in my Sony Vaio laptop, but I can't turn on my Bluetooth, and there's no icon in the bar.
I tried switching it to "on" in the settings, and checking the option for showing the icon, but they don't have any effect.

I tried following some solutions on the web, but none succeded.
I have already tried "rfkill unblock bluetooth" and shut down (not rebooting), but it didn't work.

The command "[COLOR=#111111][FONT=Consolas]sudo hciconfig hci0 reset" gave me the error "[/FONT][/COLOR]Can't init device hci0: Connection timed out (110)" and
```

exodd@exodd-SVF1521R6EW:~$ hciconfig -a
    hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    DOWN 
    RX bytes:88352 acl:0 sco:0 events:362 errors:0
    TX bytes:71 acl:0 sco:0 commands:11 errors:2
    Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
    Packet type: DM1 DH1 HV1 
    Link policy: 
    Link mode: SLAVE ACCEPT 

```

other infos:

```
exodd@exodd-SVF1521R6EW:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:5729 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0489:e062 Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


```
exodd@exodd-SVF1521R6EW:~$ uname -a
Linux exodd-SVF1521R6EW 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

```
exodd@exodd-SVF1521R6EW:~$ rfkill list
0: sony-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: nfc0: NFC
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

```
exodd@exodd-SVF1521R6EW:~$ dmesg | grep -i blue
[   13.511456] Bluetooth: Core ver 2.21
[   13.511474] Bluetooth: HCI device and connection manager initialized
[   13.511476] Bluetooth: HCI socket layer initialized
[   13.511478] Bluetooth: L2CAP socket layer initialized
[   13.511482] Bluetooth: SCO socket layer initialized
[   15.973197] Bluetooth: hci0 command 0x1001 tx timeout
[   23.969029] Bluetooth: hci0: BCM: Reading local version info failed (-110)
[   23.976909] Bluetooth: hci0: BCM: chip id 70
[   23.992884] Bluetooth: hci0: BCM43142A
[   23.992887] Bluetooth: hci0: BCM (001.001.011) build 0000
[   27.444946] Bluetooth: hci0 command 0xfc4c tx timeout
[   35.440816] Bluetooth: hci0: BCM: Patch command fc4c failed (-110)
[   37.444894] Bluetooth: hci0 command 0x0c03 tx timeout
[   45.440758] Bluetooth: hci0: BCM: Reset failed (-110)
[   46.725244] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   46.725247] Bluetooth: BNEP filters: protocol multicast
[   46.725250] Bluetooth: BNEP socket layer initialized
[  446.434460] Bluetooth: hci0 command 0x0c03 tx timeout
[  454.428671] Bluetooth: hci0: BCM: Reset failed (-110)
[ 3144.410152] Bluetooth: hci0 command 0x0c03 tx timeout
[ 3152.405954] Bluetooth: hci0: BCM: Reset failed (-110)

```


```
exodd@exodd-SVF1521R6EW:~$ lspci -knn | grep Net -A
    207:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Foxconn International, Inc. BCM43142 802.11b/g/n [105b:e071]
    Kernel driver in use: wl

```

```
exodd@exodd-SVF1521R6EW:~$ bluetoothd -d -n
bluetoothd[7605]: Bluetooth daemon 5.37
bluetoothd[7605]: src/main.c:parse_config() parsing main.conf
bluetoothd[7605]: src/main.c:parse_config() Key file does not have key 'DiscoverableTimeout' in group 'General'
bluetoothd[7605]: src/main.c:parse_config() Key file does not have key 'PairableTimeout' in group 'General'
bluetoothd[7605]: src/main.c:parse_config() Key file does not have key 'AutoConnectTimeout' in group 'General'
bluetoothd[7605]: src/main.c:parse_config() Key file does not have key 'Name' in group 'General'
bluetoothd[7605]: src/main.c:parse_config() Key file does not have key 'Class' in group 'General'
bluetoothd[7605]: src/main.c:parse_config() Key file does not have key 'DeviceID' in group 'General'
bluetoothd[7605]: src/main.c:parse_config() Key file does not have key 'ReverseServiceDiscovery' in group 'General'
D-Bus setup failed: Connection ":1.129" is not allowed to own the service "org.bluez" due to security policies in the configuration file
bluetoothd[7605]: Unable to get on D-Bus

```

```
exodd@exodd-SVF1521R6EW:~$ hcitool dev
Devices:

```

---

### Post by jeremy31 on 2016-11-18
Did you install the needed firmware?

---

### Post by exodd on 2016-11-19
Followed [http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu](http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu) letter by letter, but still not working

---

### Post by jeremy31 on 2016-11-19
What was the name of the .hex file used?

---

### Post by exodd on 2016-11-19
BCM20702A1_001.002.014.1483.1651.hex

---

### Post by jeremy31 on 2016-11-19
Let's try a different file that has worked before with that ID
```
wget https://www.dropbox.com/s/prxmhz1zvt0chdc/fw-0489_e062.hcd
sudo cp fw-0489_e062.hcd /lib/firmware/brcm/BCM.hcd
```

Reboot

---

### Post by exodd on 2016-11-21
I've shut down and restarted (not rebooted) the computer, but it's still the same as before..

---

### Post by jeremy31 on 2016-11-21
It is time to file a bug report against package linux, see [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)
There must be a regression somewhere in the kernel source code as I think we could make them work in 14.04

You may want to see if ```
sudo modprobe -r btusb && sleep 20 && sudo modprobe btusb
```
Will get it to work

---

### Post by federico24 on 2017-07-01
> **jeremy31 said:**
> It is time to file a bug report against package linux, see [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)
There must be a regression somewhere in the kernel source code as I think we could make them work in 14.04

You may want to see if ```
sudo modprobe -r btusb && sleep 20 && sudo modprobe btusb
```
Will get it to work


Hi, thanks a lot, many hours of research for finally get here before post my problem and it's work for my in UBUNTU 17.04 with XFCE4, KDE-PLASMA and UNITY installed, the laptop is a SAMSUNG NP-470 Latin American version with a ATHEROS AR9485 that comes with bluetooth 4.0.

The problem is that with KDE plasma it's work well sometimes and anothers simply doesn't, but KDE plasma is really slow.

Well, again thanks, I wrote all my laptop info and model for anothers users that has a same problem with a similar hardware that me.
Greetings!

---


---
title: "WiFi device vanished?"
date: 2016-12-09
forum: Networking &amp; Wireless
---

### Post by vinay_wagh on 2016-12-09
Dear forum,
I am running Ubuntu 16.04 on my HP Probook 450 G3 (with all latest updates installed). Day before yesterday after finishing the work I suspended the system. After waking up (after almost 3 hours), the Wireless was not working. 
(Symptoms:
1. None of the access points were mentioned.
2. The Physical WiFi On/Off switch was glowing orange
3. No change in pressing this switch.)

Noticed the same symptoms even after the restart. Further noticed the following entries in the syslog (after pressing the hardware switch):
```

Dec 10 08:34:28 my-laptop kernel: [ 2032.229930] atkbd serio0: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 10 08:34:28 my-laptop kernel: [ 2032.229948] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.

```

As suggested in the system message if I do
```
setkeycodes e078 141
```
I get
```
Dec 10 07:20:13 my-laptop systemd[1]: Starting Load/Save RF Kill Switch Status...
Dec 10 07:20:13 my-laptop systemd[1]: Started Load/Save RF Kill Switch Status.

```

The command 
```
root@my-laptop:~# rfkill list all
```
behaves erratically. Sometimes it shows bluetooth device is not (hard + soft) blocked. Most of the times no output to the command.

After searching a bit on google I found various posts. I have tried the following things so far:

Reinstall b43-fwcutter firmware-b43-installer bcmwl-kernel-source

lsusb and lspci give the following:
```

root@my-laptop:~# lsusb 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 138a:003f Validity Sensors, Inc. VFS495 Fingerprint Reader
Bus 001 Device 004: ID 05c8:0383 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 003: ID 0781:5590 SanDisk Corp. 
Bus 001 Device 002: ID 22b8:2e24 Motorola PCS 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@my-laptop:~# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Sky Lake Host Bridge/DRAM Registers [8086:1904] (rev 08)
00:02.0 VGA compatible controller [0300]: Intel Corporation Sky Lake Integrated Graphics [8086:1916] (rev 07)
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI [8086:9d3a] (rev 21)
00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] [8086:9d03] (rev 21)
00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port [8086:9d14] (rev f1)
00:1d.0 PCI bridge [0604]: Intel Corporation Device [8086:9d18] (rev f1)
00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-LP LPC Controller [8086:9d48] (rev 21)
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
00:1f.3 Multimedia audio controller [0401]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d70] (rev 21)
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader [10ec:522a] (rev 01)

```

modproble b43 does not give amything, whereas lsmod gives:
```

root@my-laptop:~# lsmod | grep b43
b43                   417792  0
bcma                   53248  1 b43
mac80211              737280  1 b43
cfg80211              565248  2 b43,mac80211
ssb                    65536  1 b43

```

Some of the posts have also suggested to remove the file: /etc/modprobe.d/blacklist-bcm43.conf. But this hasnt helped either.

Any pointers?

Here is the System Info:
```

Make and model: HP Probook 450 G3
OS: Ubuntu 16.04 64bit
WiFi hardware: Broadcom

```

Thanks and Regards 
VInay

---

### Post by wildmanne39 on 2016-12-09
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by vinay_wagh on 2016-12-10
Thanks wildmanne39, I had already seen this script (as a reply to some other post), but had not executed it! 

Anyway, attaching the .txt output. Note that I am currently using the network using USB tethering (enp0s20f0u2 in the dmesg).

Regards
VInay

---

### Post by vinay_wagh on 2016-12-12
Any updates / analysis of the wireless-info.txt?

Regards
VInay

---

### Post by wildmanne39 on 2016-12-12
I do not see a wifi card present, it is an internal card correct? If so there is only a few possibilities.

1. The card went bad.

2. The card is loose or has a dirty connection.

3. It may be turned off in the bios you can go into the bios and see if there is a setting that needs to be changed.

4. If you have windows go into windows and make sure it is on in windows then shut down windows and boot ubuntu, if this where the case I am sure we could see the card in the information you posted but it does not show up at all.

---

### Post by vinay_wagh on 2016-12-13
Thanks [**[COLOR=#C61919][B]wildmanne39**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=508533"),

Your suspicions are absolutely correct. The card is loose or probably gone bad. 

The BIOS settings are completely untouched and wireless has not been disabled in the BIOS. I have contacted the hardware support team. (In case of hardware failure, it will be taken care of!) I dont have windows installed on the system, but I checked with the bootable Ubuntu, there is no information about Broadcomm card.

I will keep you updated.

Thanks once again.
VInay

---

### Post by wildmanne39 on 2016-12-13
Your welcome!

---


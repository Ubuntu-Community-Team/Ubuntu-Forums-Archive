---
title: "Atheros AR3011 bluetooth doesn't work on Ubuntu 18.04"
date: 2019-01-05
forum: Networking &amp; Wireless
---

### Post by aneganov on 2019-01-05
I have a desktop PC with "IMC Networks Asus Integrated Bluetooth module [AR3011]" device which doesn't seem to work.
I found a report dated by 2011 saying this thing worked before (2.6.x kernels) [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641749](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641749) - which is pretty close to my own... feeling that yeah, it did work before (the same PC).
I'm too lazy to fix problems as soon as they appear, so I've been postponing the resolution of this problem for several years.
Today I told myself that it really needs my attention. 
So folks, any ideas where to look at?


```
[FONT=monospace][COLOR=#000000]
$ lsusb | grep -i bluetooth[/COLOR]
Bus 002 Device 004: ID 13d3:3304 IMC Networks Asus Integrated [COLOR=#FF5454]**Bluetooth**[/COLOR][COLOR=#000000] module [AR3011][/COLOR]
[/FONT]
```

UPD 1:
```

$ dmesg | egrep -i 'blue|firm'
[    0.031874] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    5.348311] Bluetooth: Core ver 2.22
[    5.348323] Bluetooth: HCI device and connection manager initialized
[    5.348325] Bluetooth: HCI socket layer initialized
[    5.348327] Bluetooth: L2CAP socket layer initialized
[    5.348331] Bluetooth: SCO socket layer initialized
[   10.463408] Bluetooth: Can't change to loading configuration err
[   20.606784] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.606785] Bluetooth: BNEP filters: protocol multicast
[   20.606788] Bluetooth: BNEP socket layer initialized
[ 3877.171073] audit: type=1107 audit(1546720379.542:45): pid=1032 uid=105 auid=4294967295 ses=4294967295\
  msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/"\
  interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name
="org.bluez" pid=13909 label="snap.wire.wire" peer_pid=2733 peer_label="unconfined"

```

---

### Post by jeremy31 on 2019-01-05
Please post results for ```
dmesg | egrep -i 'blue|firm'
```

---

### Post by aneganov on 2019-01-05
Hi Jeremy,

thanks for quick reply.
Here it is:

```

$ dmesg | egrep -i 'blue|firm'
[    0.031874] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    5.348311] Bluetooth: Core ver 2.22
[    5.348323] Bluetooth: HCI device and connection manager initialized
[    5.348325] Bluetooth: HCI socket layer initialized
[    5.348327] Bluetooth: L2CAP socket layer initialized
[    5.348331] Bluetooth: SCO socket layer initialized
[   10.463408] Bluetooth: Can't change to loading configuration err
[   20.606784] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.606785] Bluetooth: BNEP filters: protocol multicast
[   20.606788] Bluetooth: BNEP socket layer initialized
[ 3877.171073] audit: type=1107 audit(1546720379.542:45): pid=1032 uid=105 auid=4294967295 ses=4294967295\
  msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/"\
  interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name
="org.bluez" pid=13909 label="snap.wire.wire" peer_pid=2733 peer_label="unconfined"

```[FONT=monospace][COLOR=#000000]
[/COLOR]
[/FONT]

---

### Post by jeremy31 on 2019-01-05
One thing you can try is
```
echo "blacklist ath3k" | sudo tee /etc/modprobe.d/ath3k.conf
echo "blacklist btusb" | sudo tee -a /etc/modprobe.d/ath3k.conf
```
Power down, then boot and after it boots, open terminal
```
sudo modprobe ath3k
sudo modprobe btusb
```

---

### Post by aneganov on 2019-01-05
I blacklisted those drivers, rebooted and executed those commands.
This is from dmesg:
```

[FONT=monospace][COLOR=#18B218][  164.399880] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: Core ver 2.22[/COLOR]
[COLOR=#18B218][  164.399902] [/COLOR][COLOR=#B26818]NET[/COLOR][COLOR=#000000]: Registered protocol family 31[/COLOR]
[COLOR=#18B218][  164.399902] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: HCI device and connection manager initialized[/COLOR]
[COLOR=#18B218][  164.399905] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: HCI socket layer initialized[/COLOR]
[COLOR=#18B218][  164.399907] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: L2CAP socket layer initialized[/COLOR]
[COLOR=#18B218][  164.399917] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: SCO socket layer initialized[/COLOR]
[COLOR=#18B218][  169.439983] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#B21818]: Can't change to loading configuration err[/COLOR]
[COLOR=#18B218][  169.440021] [/COLOR][COLOR=#B26818]ath3k[/COLOR][COLOR=#000000]**: probe of 2-1.5:1.0 failed with error -110**[/COLOR]
[COLOR=#18B218][  169.440114] [/COLOR][COLOR=#B26818]usbcore[/COLOR][COLOR=#000000]: registered new interface driver ath3k[/COLOR]
[COLOR=#18B218][  194.564966] [/COLOR][COLOR=#B26818]usbcore[/COLOR][COLOR=#000000]: registered new interface driver btusb[/COLOR]
[/FONT]
```

[strike]It seems some other driver should be used here...[/strike]

---

### Post by aneganov on 2019-01-06
Any more suggestions?

I've read this thread [https://forums.linuxmint.com/viewtopic.php?f=49&t=188272&sid=e2ba4d748c1e3b6934dab5e60468d322&start=20](https://forums.linuxmint.com/viewtopic.php?f=49&t=188272&sid=e2ba4d748c1e3b6934dab5e60468d322&start=20) and understood nothing. Seems to be my case.
I'm crusios will I get this crap working at all...

---

### Post by jeremy31 on 2019-01-06
What wifi? ```
lspci -nnk | grep -iA3 net
```
I suspect an old AR9200.  You might want to try removing the card and reinstall it to make sure it has a good connection in the motherboard

---

### Post by aneganov on 2019-01-06
> I suspect an old AR9200. You might want to try removing the card and reinstall it to make sure it has a good connection in the motherboard

Yeah, maybe - see below. I cannot remove/insert anything, since it's built into my ASUS P9X79_DELUXE motherboard - [https://www.asus.com/us/Motherboards/P9X79_DELUXE/](https://www.asus.com/us/Motherboards/P9X79_DELUXE/)
And it perfectly works on Windows (dual boot system) so no hw issues.

```

[FONT=monospace][COLOR=#000000]$ lspci -nnk | grep -iA3 net[/COLOR]
00:19.0 Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] controller [0200]: Intel Corporation 82579V Gigabit [/COLOR][COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work Connection [8086:1503] (rev 06)[/COLOR]
        Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
        Kernel driver in use: e1000e
        Kernel modules: e1000e
[COLOR=#18B2B2]--[/COLOR][COLOR=#000000][/COLOR]
08:00.0 [COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work controller [0280]: Qualcomm Atheros AR9285 Wireless [/COLOR][COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work Adapter (PCI-Express) [168c:002b] (rev 01)[/COLOR]
        Subsystem: AzureWave AW-NB037H 802.11bgn Wireless Half-size Mini PCIe Card [AR9002WB-1NGCD] [1a3b:2c37]
        Kernel driver in use: ath9k
        Kernel modules: ath9k
[COLOR=#18B2B2]--[/COLOR][COLOR=#000000][/COLOR]
0a:00.0 Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ether[/COLOR][COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] Controller [10ec:8168] (rev 06)[/COLOR]
        Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
        Kernel driver in use: r8169
        Kernel modules: r8169

```[/FONT]

---

### Post by jeremy31 on 2019-01-06
I am not sure as I just put my old card back in a Toshiba laptop and it works fine, blacklisting ath3k and rebooting results in it showing up in lsusb as ID 13d3:3304 IMC Networks Asus Integrated Bluetooth module [AR3011] and after modprobe ath3k it then shows as 0cf3:3005 and functions as a Bluetooth device
```
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NB037H 802.11bgn Wireless Half-size Mini PCIe Card [AR9002WB-1NGCD] [1a3b:2c37]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:3304 IMC Networks Asus Integrated Bluetooth module [AR3011]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

After sudo modprobe ath3k
```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by aneganov on 2019-01-06
Seems like we have similar set of hardware.
I retried everything from scratch in this sequence: restarted, checked devices, modprobe'd ath3k, checked devices again, and it basically doesn't work like at your side.
When I issue **modprobe ath3k** this appears in dmesg:
```
 
[FONT=monospace][COLOR=#18B218][  147.176952] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: Core ver 2.22[/COLOR]
[COLOR=#18B218][  147.176972] [/COLOR][COLOR=#B26818]NET[/COLOR][COLOR=#000000]: Registered protocol family 31[/COLOR]
[COLOR=#18B218][  147.176973] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: HCI device and connection manager initialized[/COLOR]
[COLOR=#18B218][  147.176976] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: HCI socket layer initialized[/COLOR]
[COLOR=#18B218][  147.176978] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: L2CAP socket layer initialized[/COLOR]
[COLOR=#18B218][  147.176984] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: SCO socket layer initialized[/COLOR]
[COLOR=#18B218][  152.418571] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#B21818]: Can't change to loading configuration err[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][  152.418618] [/COLOR][COLOR=#B26818]ath3k[/COLOR][COLOR=#000000]**: probe of 2-1.5:1.0 failed with error -110**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][  152.418711] [/COLOR][COLOR=#B26818]usbcore[/COLOR][COLOR=#000000]: registered new interface driver ath3k[/COLOR]
[/FONT]
```
note the times: there is 5.5 seconds delay when it's loading **ath3k**. This is because it cannot configure/reach the device.

---

### Post by praseodym on 2019-01-06
The weird thing:
```

modprobe -c | grep -i "13d3.*3304"
alias usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in* ath3k
modprobe -c | grep -i "0cf3.*3005"
```
gives nothing. Check this firmware update:

[https://forum.mxlinux.org/viewtopic.php?t=46010](https://forum.mxlinux.org/viewtopic.php?t=46010)

```
cd /lib/firmware
sudo mv ath3-1.fw ath3-1.bak
sudo wget https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/714862/+attachment/2832934/+files/ath3k-1.fw
```
Reboot and check
```

dmesg | egrep 'ath3|firm|fail|blue'
```

---

### Post by jeremy31 on 2019-01-06
Actually, try reversing the order of loading the modules
```
sudo modprobe btusb
sudo modprobe ath3k
```

---


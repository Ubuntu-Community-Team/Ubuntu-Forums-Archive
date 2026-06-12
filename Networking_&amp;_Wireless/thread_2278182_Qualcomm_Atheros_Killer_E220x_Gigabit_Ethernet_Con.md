---
title: "Qualcomm Atheros Killer E220x Gigabit Ethernet Controller"
date: 2015-05-14
forum: Networking &amp; Wireless
---

### Post by el-rayado-verde on 2015-05-14
Hi!

I have just installed Ubuntu 15.04 on my laptop but i have problems with my Ethernet. I have been told to open a new thread including the following:

```
lspci -nn | grep 0200
```

Result:
```
04:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 13)
```

I've been told also to write ```
nm-tool
```, but the command is not found.

---

### Post by chili555 on 2015-05-14
Your device is covered by the driver *alx *in Ubuntu 15.04. I doubt that installing a different driver is helpful since virtually all of them are older than what you now have. What is not working as expected? May we see the log?```
dmesg | grep -e alx -e eth
```

---

### Post by el-rayado-verde on 2015-05-14
The thing is that the status bar shows the WiFi logo, and pressing on  it, it shows a list of connections, but I have never managed to connect  neither via WiFi nor via wired LAN.

Result:
```
[    0.824346] alx 0000:04:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [44:8a:5b:f2:35:15]
[    1.159097] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff88041e8e33e8), AE_NOT_FOUND (20141107/psparse-536)
[    1.160510] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff88041e8e33e8), AE_NOT_FOUND (20141107/psparse-536)
[    1.819286] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG0.PEGP handle
[   12.369047] ipheth 1-6:4.2: ipheth_get_macaddr: usb_control_msg: -110
[   12.369063] ipheth: probe of 1-6:4.2 failed with error -110
[   12.369095] usbcore: registered new interface driver ipheth
[  101.474688] ipheth 1-1:4.2: Apple iPhone USB Ethernet device attached

```

As you can see, I'm online sharing my mobile connection via USB, and that is an expensive connection.

---

### Post by chili555 on 2015-05-14
Please detach the tether, turn off the wireless with the switch or key combination and reboot. Then run:```
dmesg | grep -e alx -e 04:00  >  ethernet.txt
cat  /etc/network/interfaces  >>  ethernet.txt
```Hook up the tether, find the file ethernet.txt in your user directory and post it here.

---

### Post by el-rayado-verde on 2015-05-14
Result:

```
[    0.289237] pci 0000:04:00.0: [1969:e091] type 00 class 0x020000[    0.289273] pci 0000:04:00.0: reg 0x10: [mem 0xf7800000-0xf783ffff 64bit]
[    0.289313] pci 0000:04:00.0: reg 0x18: [io  0xd000-0xd07f]
[    0.289533] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.289579] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.364764] pci 0000:04:00.0: set MSI_INTX_DISABLE_BUG flag
[    0.576345] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.816229] alx 0000:04:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [44:8a:5b:f2:35:15]
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by chili555 on 2015-05-14
That is some fast booting there! May I assume the drive is a solid-state device (SSD)? 

Is the module loaded now?```
lsmod | grep -e alx -e mdio
```Does it help at all to unload and reload the driver, perhaps just to provoke an error or warning?```
sudo modprobe -r alx
sudo modprobe alx
dmesg | grep alx
```Any clues here?```
sudo ethtool eth0
```So far, I see nothing wrong; that is fixable, except it doesn't work!

---

### Post by el-rayado-verde on 2015-05-14
Yes, I am using a SDD :-)

According to the first command the result is:

```
alx              36864  0
mdio                16384  1  alx
```

Should I understand alx is off? But does it mean that I couldn't check for available Wireless Networks when I do see them?

I have no idea, sorry about my ignorance. I promise I'll learn more, that is the point.

```
manucy@manucy-GE62-2QF:~$ lsmod | grep -e alx -e mdioalx                    36864  0 
mdio                   16384  1 alx
manucy@manucy-GE62-2QF:~$ sudo modprobe -r alx
[sudo] password for manucy: 
manucy@manucy-GE62-2QF:~$ sudo modprobe alx
manucy@manucy-GE62-2QF:~$ dmesg | grep alx
[    0.816229] alx 0000:04:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [44:8a:5b:f2:35:15]
[  849.705355]  soundcore wmi dw_dmac i2c_designware_platform spi_pxa2xx_platform dw_dmac_core video i2c_designware_core snd_soc_sst_acpi 8250_dw acpi_pad parport_pc ppdev lp parport autofs4 psmouse ahci alx libahci mdio sdhci_acpi sdhci
[ 1674.641978]  drm mei_me ie31200_edac mei edac_core shpchp i2c_algo_bit lpc_ich snd_rawmidi snd_seq snd_seq_device snd_timer snd i2c_hid hid mac_hid soundcore wmi dw_dmac i2c_designware_platform spi_pxa2xx_platform dw_dmac_core video i2c_designware_core snd_soc_sst_acpi 8250_dw acpi_pad parport_pc ppdev lp parport autofs4 psmouse ahci alx libahci mdio sdhci_acpi sdhci
[ 1674.654012]  drm mei_me ie31200_edac mei edac_core shpchp i2c_algo_bit lpc_ich snd_rawmidi snd_seq snd_seq_device snd_timer snd i2c_hid hid mac_hid soundcore wmi dw_dmac i2c_designware_platform spi_pxa2xx_platform dw_dmac_core video i2c_designware_core snd_soc_sst_acpi 8250_dw acpi_pad parport_pc ppdev lp parport autofs4 psmouse ahci alx libahci mdio sdhci_acpi sdhci
[ 1674.654136]  drm mei_me ie31200_edac mei edac_core shpchp i2c_algo_bit lpc_ich snd_rawmidi snd_seq snd_seq_device snd_timer snd i2c_hid hid mac_hid soundcore wmi dw_dmac i2c_designware_platform spi_pxa2xx_platform dw_dmac_core video i2c_designware_core snd_soc_sst_acpi 8250_dw acpi_pad parport_pc ppdev lp parport autofs4 psmouse ahci alx libahci mdio sdhci_acpi sdhci
[ 1674.654221]  drm mei_me ie31200_edac mei edac_core shpchp i2c_algo_bit lpc_ich snd_rawmidi snd_seq snd_seq_device snd_timer snd i2c_hid hid mac_hid soundcore wmi dw_dmac i2c_designware_platform spi_pxa2xx_platform dw_dmac_core video i2c_designware_core snd_soc_sst_acpi 8250_dw acpi_pad parport_pc ppdev lp parport autofs4 psmouse ahci alx libahci mdio sdhci_acpi sdhci
[ 1674.654337]  drm mei_me ie31200_edac mei edac_core shpchp i2c_algo_bit lpc_ich snd_rawmidi snd_seq snd_seq_device snd_timer snd i2c_hid hid mac_hid soundcore wmi dw_dmac i2c_designware_platform spi_pxa2xx_platform dw_dmac_core video i2c_designware_core snd_soc_sst_acpi 8250_dw acpi_pad parport_pc ppdev lp parport autofs4 psmouse ahci alx libahci mdio sdhci_acpi sdhci
[ 2015.479189] alx 0000:04:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [44:8a:5b:f2:35:15]
manucy@manucy-GE62-2QF:~$ 
manucy@manucy-GE62-2QF:~$ lsmod | grep -e alx -e mdio
alx                    36864  0 
mdio                   16384  1 alx
manucy@manucy-GE62-2QF:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: Symmetric Receive-only
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Current message level: 0x000060e4 (24804)
			       link ifup rx_err tx_err hw wol
	Link detected: no



```

We've made some progress, there's an internet connection when wired to the router, but couldn't connect to any WiFi, neither from the router nor from tethered iOS or Android.

---

### Post by el-rayado-verde on 2015-05-14
Issue solved!

Thanks!

---

### Post by chili555 on 2015-05-14
> **el-rayado-verde said:**
> Issue solved!

Thanks!Would you mind telling us how? I am glad it's working, but if there is some magic fix, I'm sure the searchers would be glad to know it.

---

### Post by maym86 on 2015-06-18
What was the fix?

---

### Post by el-rayado-verde on 2015-09-04
I don't know, it just worked...

---

### Post by el-rayado-verde on 2015-09-04
The thing is that I had to reinstall Ubuntu, and it is not working anymore...

---

### Post by Tristan_Cormier on 2015-10-09
I too have the same problem and have opened a thread at [SIZE=2]http://ubuntuforums.org/showthread.php?t=2297839 if anyone's interested.[/SIZE]

---


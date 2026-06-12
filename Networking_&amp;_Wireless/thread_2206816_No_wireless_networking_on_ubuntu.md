---
title: "No wireless networking on ubuntu"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by Mikael_Gafi on 2014-02-20
Hello everyone, I am new to Ubuntu. Recently, I received a laptop from a friend of mine(HP pavilion dv2000). I believe it had 13.04 and just yesterday i updated it to 13.10 hoping that the wireless networking issue would be resolved, but that wasn't the case. I am able to use a wired connection but not wireless. If anyone can help, I would be content. I am willing to add more info to those who request it. Thank You!

---

### Post by papibe on 2014-02-20
Hi Mikael_Gafi. Welcome to the forum ):P

Could you open a terminal, run these commands, and post back its results? (you can copy paste the output):
```
sudo lshw -C network

lspci -nnk | grep -iA2 net

ifconfig

route -n

nm-tool 

cat /etc/network/interfaces
```
Regards.

---

### Post by Mikael_Gafi on 2014-02-22
Alright, after entering the commands you gave me above these were my results:
```
gacy@apex:~$ sudo lshw -c network
[sudo] password for negacy: 
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:5c:fb:8d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.111 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f4200000-f4203fff ioport:3000(size=256)

negacy@apex:~$ lspci -nnk | grep -ia2 net
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: sky2

negacy@apex:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:5c:fb:8d  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe5c:fb8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1402435 (1.4 MB)  TX bytes:209210 (209.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20588 (20.5 KB)  TX bytes:20588 (20.5 KB)

negacy@apex:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

negacy@apex:~$ nm-tool
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:1D:72:5C:FB:8D

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.111
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


negacy@apex:~$ cat /etc/network/interfaces
    auto lo
    auto mlan0
    iface lo inet loopback
    iface mlan0 inet manual
            wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
    iface default inet dhcp

negacy@apex:~$
```

---

### Post by papibe on 2014-02-22
Thanks.

There no mention of another interface, other than ethernet, on the results. Which is very strange.

Are you sure you have a wireless card inside?

There may be a hint. There's a reference to in interface called **mlan0** on the interfaces files. It is set to handle manually and configured using a file. Let's try to let the system to handle it.

Please open a terminal and run these commands:
```
sudo apt-get install gksu
```
It may ask you for your password, and then a confirmation (enter yes).

Then:
```
gksudo gedit /etc/network/interfaces
```
That will open an editor. Modify the file so it looks like this:
```
auto lo
iface lo inet loopback
```
Save the file, and restart your computer.

Once back, try to use your wireless connection. If it doesn't work, please open a terminal and run this commands, and post back its results:
```
sudo lshw -C network

lspci -nnk | grep -iA2 net

ifconfig

rfkill list

sudo cat /etc/wpa_supplicant/wpa_supplicant.conf
```
Regards.

---

### Post by Mikael_Gafi on 2014-02-22
Hi, I tried the first 2 commands but they both failed to do anything, so I did the last command and this is what I recieved (P.S. I messed up quite a few times on this one):

```
negacy@apex:~$  sudo lshw -c network
[sudo] password for negacy: 
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:5c:fb:8d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.111 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f4200000-f4203fff ioport:3000(size=256)
negacy@apex:~$ lspci -nnk | grep -ia2 net
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: sky2

negacy@apex:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:5c:fb:8d  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe5c:fb8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11523 (11.5 KB)  TX bytes:14432 (14.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4625 (4.6 KB)  TX bytes:4625 (4.6 KB)

negacy@apex:~$ rfkill list sud cat /etc/wpa_supplicant/wpa_supplicant.conf
Bogus list argument 'sud'.

negacy@apex:~$ rfkill list
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
negacy@apex:~$ sudo cat /etc/wpa
cat: /etc/wpa: No such file or directory
negacy@apex:~$ 
negacy@apex:~$ 
negacy@apex:~$ 

negacy@apex:~$ sudo cat /etc/wpa_supplicant/wpa_supplicant.conf
 update_config=1
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
negacy@apex:~$
```

---

### Post by papibe on 2014-02-22
Try this to edit the file:
```
sudo nano /etc/network/interfaces
```
Edit it to look like this:
```
auto lo
iface lo inet loopback
```
Then restart.

Regards.

---

### Post by Mikael_Gafi on 2014-02-23
I did that previously and it did nothing :(

---

### Post by papibe on 2014-02-23
As far I can tell, from the output of the commands, that laptop has no wireless cards.

In this page [HP Pavilion dv2000]("http://en.wikipedia.org/wiki/HP_Pavilion_dv2000"), I found this:
> HP has identified hardware issues with certain HP Pavilion dv2000/dv6000/dv9000 and Compaq Presario V3000/V6000 series notebook PCs, equipped with nvidia chipsets and mostly of them with AMD microprocessors. For the dv2000 series, it includes many models from the dv20xx, dv21xx, dv22xx, dv23xx, and the dv24xx series (where xx is any other 2 digits). The Intel-based dv2000 Core Solo, Core Duo, Core 2 Duo or Pentium Dual Core with the Intel 945 chipset, do not suffer from this problem, except those with dedicated video chip nVidia.

Some symptoms include:

    **[COLOR="#FF0000"]The notebook does not detect wireless networks and the wireless adapter is not detected in the Device Manager.[/COLOR]**
    There is no video on the computer LCD panel or external monitor (video card failure).[2]
    Problems with the sound system, DVD or Hard Drive.

At this moment, I don't have any other idea other than it could be a BIOS update on HP's website that maybe fix those problems.

I hope you can fix it.
Regards.

---

### Post by praseodym on 2014-02-23
The card is not shown. Please show
```

lsmod
pccardctl info
lsusb
```
Checked the BIOS-settings if wireless can be activated there?

---

### Post by Mikael_Gafi on 2014-02-23
Sorry im new to Ubuntu so I don't know how to check the BIOS-settings and here is the output for the above commands that you gave me: 



negacy@apex:~$ lsmod
Module                  Size  Used by
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  12 
btusb                  23443  0 
bluetooth             323656  22 bnep,btusb,rfcomm
binfmt_misc            13140  1 
snd_hda_codec_conexant    47785  1 
joydev                 17097  0 
coretemp               13195  0 
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
microcode              18894  0 
r852                   17925  0 
sm_common              16772  1 r852
nand                   58878  2 r852,sm_common
nand_ecc               13136  1 nand
nand_bch               13067  1 nand
r592                   17711  0 
nand_ids                8547  1 nand
psmouse                90642  0 
serio_raw              13189  0 
memstick               16008  1 r592
bch                    17197  1 nand_bch
snd_hda_intel          42658  3 
snd_hda_codec         164003  2 snd_hda_codec_conexant,snd_hda_intel
mtd                    52735  2 nand,sm_common
snd_hwdep              13272  1 snd_hda_codec
lpc_ich                16864  0 
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  16 snd_hwdep,snd_timer,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  594442  3 
drm_kms_helper         46867  1 i915
soundcore              12600  1 snd
drm                   242400  4 i915,drm_kms_helper
wmi                    18590  1 hp_wmi
i2c_algo_bit           13197  1 i915
video                  18777  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
firewire_ohci          35463  0 
firewire_core          57656  1 firewire_ohci
ahci                   25579  2 
libahci                26619  1 ahci
sdhci_pci              18481  0 
crc_itu_t              12627  1 firewire_core
sdhci                  37644  1 sdhci_pci
sky2                   52946  0 
negacy@apex:~$ pccardctl info
negacy@apex:~$ lsusb
Bus 002 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
negacy@apex:~$

---

### Post by praseodym on 2014-02-23
Lets check

```
lspci -nnk
```

completely.

If you reboot there should be a key shown during the black boot screen which brings you into your BIOS (here it is DEL, sometimes its F12, etc.). Normally, F9 resets the BIOS and F10 save&exit)

---

### Post by Mikael_Gafi on 2014-06-20
sorry im etremely late but here is the output for the command above


negacy@apex:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: ata_piix
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: sky2
08:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: firewire_ohci
08:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: sdhci-pci
08:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: r592
08:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: r852

---

### Post by praseodym on 2014-06-20
Obviously, no PCI device. Lets check
```

lsusb
pccardctl info
```
Checked the BIOS settings for turning it on? BIOS-reset to default settings?

---

### Post by Mikael_Gafi on 2014-06-20
Here is the code to the commands you just gave me:

negacy@apex:~$ lsusb
Bus 002 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
negacy@apex:~$ pccardctl info



the pccardctl info command did not seem to do anything

---

### Post by Mikael_Gafi on 2014-06-20
I checked the BIOS settings by pressing f10 on the boot, and set it to default configuration.. it did nothing.  By the way thanks for your support

---

### Post by Mikael_Gafi on 2014-06-20
:confused:

---

### Post by papibe on 2014-06-20
Is there any BIOS update available for your machine at the HP site?

Regards.

---

### Post by Mikael_Gafi on 2014-06-20
yes but it is only for those that run on vista

---

### Post by papibe on 2014-06-20
There's a couple of 'unofficial' options. Read [here]("http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and-Software/BIOS-upgrade-with-Linux/td-p/296487").

One requires someone loan you a Windows PC to create a bootable media. The other one is pure Linux. It could also be valuable to take a look at [this]("https://help.ubuntu.com/community/BIOSUpdate") too.

Regards.

P.S.: Please note there's always risks when you update your BIOS.

---

### Post by Mikael_Gafi on 2014-06-20
Is that the only option left I have to fix this issue. I have seen many other issues like mine concerning the wireless card intel wm3945abg not showing up.

---

### Post by praseodym on 2014-06-21
The outputs show no wireless device. Is it a dualboot system? Does Windows show a device or does Windows shut down the card automatically?

---

### Post by Mikael_Gafi on 2014-06-21
it is a dual boot and vista is currently not working on it, only ubuntu. I have no idea on what to do next.

---

### Post by praseodym on 2014-06-22
Lets check:

```
cat /etc/udev/rules.d/70-persistent-net.rules
dmesg >> dmesg.txt
```
Please upload the file dmesg.txt

---

### Post by Mikael_Gafi on 2014-06-22
so i did the command but dmesg >> dmesg.txt returned nothing  


negacy@apex:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x11ab:0x4353 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:72:5c:fb:8d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
negacy@apex:~$ dmesg >> dmesg.txt

---

### Post by Mikael_Gafi on 2014-06-22
I feel so dumb.. Here are the two .txt files since it was too large to fit on one file

---

### Post by Mikael_Gafi on 2014-06-22
Here

---

### Post by Mikael_Gafi on 2014-06-22
:

---


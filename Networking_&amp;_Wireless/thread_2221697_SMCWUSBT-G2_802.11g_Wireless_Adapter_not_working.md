---
title: "SMCWUSBT-G2 802.11g Wireless Adapter not working"
date: 2014-05-03
forum: Networking &amp; Wireless
---

### Post by brunolabs on 2014-05-03
Hi!

I can't get the wireless adapter to work in 14.04. 
It is detected by 'lsusb': 
```
Bus 001 Device 003: ID 083a:4507 Accton Technology Corp. SMCWUSBT-G2 802.11g Wireless Adapter [Atheros AR5523]
```
However, the blinking led is off and I can't create a new wireless connection with it.

I tried most of the solutions posted online without success.
Can anyone help me with this issue?


Thank you in advance! :)

---

### Post by varunendra on 2014-05-04
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by brunolabs on 2014-05-25
Wireless script result:
```

########## wireless info START ##########

##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

##### kernel #####

Linux P5SD1-FM2 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191]
	Subsystem: ASUSTeK Computer Inc. Device [1043:8139]
	Kernel driver in use: sis190

##### lsusb #####

Bus 001 Device 008: ID 083a:4507 Accton Technology Corp. SMCWUSBT-G2 802.11g Wireless Adapter [Atheros AR5523]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0734 Microsoft Corp. Wireless Optical Desktop 700
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### iw reg get #####

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search lan

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sis190
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.71
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

##### lsmod #####

##### modinfo #####

##### modules #####

lp

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x1039:0x0191 (sis190)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #####

########## wireless info END ############
```


Thank you for your help.

---

### Post by praseodym on 2014-05-25
Try installing this driver package:
```

sudo apt-get install build-essential linux-headers-$(uname -r) linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.14/backports-3.14-1.tar.gz
tar -xvf backports-3.14-1.tar.gz
cd backports-3.14-1
make defconfig-ar5523
make
sudo make install
```

---

### Post by brunolabs on 2014-05-25
Hello.

Thank you for helping with this issue.

I followed your instructions and every step was sucessful. Also did the required system reboot after the install.

However, I still can't make any wifi connection. I don't see the list of available networks.
I also tried to create one in the "Network Connections" menu but without success.

Could you could give me some additional help?


Thanks again for your help! :)

---

### Post by praseodym on 2014-05-25
Lets check if it works at all:
```

lsmod
iwconfig
rfkill list
ifconfig -a
cat /etc/resolv.conf
route -n
dmesg | grep ar5
```
Is it 32 or 64 bit?

---

### Post by brunolabs on 2014-05-25
Here are the results I got.

- lsmod
```
Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               299807  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342263  10 bnep,rfcomm
binfmt_misc            13140  1 
radeon               1416373  3 
snd_intel8x0           33110  2 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
ttm                    72698  1 radeon
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper         46907  1 radeon
drm                   243792  5 ttm,drm_kms_helper,radeon
snd_timer              28584  2 snd_pcm,snd_seq
i2c_algo_bit           13197  1 radeon
snd                    60871  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
shpchp                 32128  0 
serio_raw              13230  0 
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
hid_generic            12492  0 
usbhid                 47035  0 
hid                    87604  2 hid_generic,usbhid
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
sis190                 22210  0 
psmouse                91033  0 
crc_itu_t              12627  1 firewire_core
mii                    13654  1 sis190
sata_sis               12711  2 
floppy                 55378  0
```

- iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

- rfkill list
     did not show any output

- ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:15:f2:61:bd:ad  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe61:bdad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4853488 (4.8 MB)  TX bytes:883218 (883.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:220002 (220.0 KB)  TX bytes:220002 (220.0 KB)

```

- cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search lan
```

- route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

- dmesg | grep ar5
     did not show any output

And it is a 32 bit system.


Thank you very much for your time.

---

### Post by praseodym on 2014-05-25
Unplug the cable, load the driver by hand and replug the stick:
```

sudo modprobe -v ar5523
```Check
```
dmesg | grep ar5
modinfo ar5523
iwconfig
```

---

### Post by brunolabs on 2014-05-25
New results after those instructions.


- dmesg | grep ar5
```
[ 9181.873672] usbcore: registered new interface driver ar5523
```

- modinfo ar5523
```
filename:       /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ar5523/ar5523.ko
firmware:       ar5523.bin
license:        Dual BSD/GPL
version:        backported from Linux (v3.14-0-g455c6fd) using backports v3.14-1-0-g369d49a
srcversion:     737FECEC1B1574C35426909
alias:          usb:v1385p5F03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1385p5F02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1385p5F01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1385p5F00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1385p4251d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1385p4250d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0829d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0828d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0827d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0826d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3206d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3205d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p5F01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p5F00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p4251d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p4250d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p4301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p4300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7803d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7802d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v16ABp7812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v16ABp7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v16ABp7802d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v16ABp7801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v129Bp160Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v129Bp160Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0710d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0713d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3A08d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3A07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A05d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A04d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3A00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7802d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D8Ep7801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v168Cp0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v168Cp0001d*dc*dsc*dp*ic*isc*ip*in*
depends:        compat,mac80211,cfg80211
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
```

- iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by praseodym on 2014-05-25
Ok, add the device ID to the driver:

```
echo 'install ar5523 modprobe --ignore-install ar5523 ; /bin/echo "083a 4507" > [COLOR="#FF0000"]/sys/bus/usb/drivers/rt2800usb/[/COLOR]new_id' | sudo tee /etc/modprobe.d/ar5523.conf
```
Check and correct the red entry, this is from an earlier example of a Ralink driver.

Load the driver
```

sudo modprobe -rfv ar5523
sudo modprobe -v ar5523
```
Replug the stick and check again.

---

### Post by brunolabs on 2014-05-25
Corrected the command to the right folder (ar5523)

```
install ar5523 modprobe --ignore-install ar5523 ; /bin/echo "083a 4507" > /sys/bus/usb/drivers/ar5523/new_id
```

And the next commands return
```

insmod /lib/modules/3.13.0-24-generic/updates/compat/compat.ko 
insmod /lib/modules/3.13.0-24-generic/updates/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-24-generic/updates/net/mac80211/mac80211.ko 
install modprobe --ignore-install ar5523 ; /bin/echo "083a 4507" > /sys/bus/usb/drivers/ar5523/new_id 
insmod /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ar5523/ar5523.ko 

```


Still the same. But now 'dmesg' returns an error!!
```
[  372.534875] usbcore: registered new interface driver ar5523
[  416.616405]** ar5523: probe of 1-6:1.0 failed with error -110**
```

The other commands return the same data.


I also have issues with another wifi adapter.
[http://ubuntuforums.org/showthread.php?t=2226109]("http://ubuntuforums.org/showthread.php?t=2226109")

Could this be a configuration problem of some sort shared by the two adapters?
I find it odd that an old and a new adapter fail to work properly. :\


Again, thanks for your help! :)

---

### Post by praseodym on 2014-05-26
That other device is a very new Ralink device, this is an old Atheros ;-)

Uninstall that driver via
```

cd backports-3.14-1
make clean
make defconfig-ar5523
make
sudo make uninstall
```
And try Ndiswrapper with the Windows driver, you're lucky: There's only a 32bit driver available:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms ndisgtk ndiswrapper-dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/49/42/2899382-Atheros_AR5523usb_XPw9x_32bit.tar.gz
```
Try both of that windows drivers (*.INF file) via
```

gksudo ndisgtk
```

---

### Post by brunolabs on 2014-05-26
After installing both drivers (separately) both say "Hardware not present".

I guess this adapter is a lost cause. :(

Could you please help me with the other Ralink chipset then?
Maybe it could be easier to configure. Should I replicate all the steps you've mentioned in this thread?


I really thank you for your help. :)

---

### Post by praseodym on 2014-05-26
Unplug this stick and run:
```

sudo ndiswrapper -i [COLOR="#FF0000"]/path/to/the/respective/*.INF[/COLOR]
sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
```
Replug the stick and:
```

lsmod
iwconfig
dmesg | grep ndis
```

---

### Post by brunolabs on 2014-05-26
After "sudo ndiswrapper -ma" I get:
wrong bustype () for configuration file 07D1:3A0.F.conf - ignoring it
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf

The referred file contains:
```
alias usb:v07D1p3A08d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0CF3p0002d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0CF3p0002d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v129Bp160Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v129Bp160Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v129Bp160Dd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v129Bp160Dd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v148Fp7601d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3A01d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3A01d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3A02d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3A02d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3A03d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3A03d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3A05d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3A05d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:vA727p6893d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:vA727p6893d*dc*dsc*dp*ic*isc*ip* ndiswrapper
```

After replugging the stick I get:
- lsmod
```
Module                  Size  Used by
btrfs                 822702  0 
raid6_pq               97455  1 btrfs
xor                    26221  1 btrfs
ufs                    73656  0 
qnx4                   13101  0 
hfsplus                93447  0 
hfs                    49390  0 
minix                  31317  0 
ntfs                   95723  0 
msdos                  17093  0 
jfs                   170009  0 
xfs                   802883  0 
libcrc32c              12543  2 xfs,btrfs
ndiswrapper           192915  0 
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               299807  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342263  10 bnep,rfcomm
binfmt_misc            13140  1 
rt2800usb              26581  0 
rt2x00usb              20041  1 rt2800usb
ppdev                  17391  0 
rt2800lib              83150  1 rt2800usb
snd_intel8x0           33110  2 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
rt2x00lib              48886  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              545990  3 rt2x00lib,rt2x00usb,rt2800lib
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
cfg80211              409394  2 mac80211,rt2x00lib
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
serio_raw              13230  0 
snd                    60871  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
shpchp                 32128  0 
radeon               1416373  3 
crc_ccitt              12627  1 rt2800lib
soundcore              12600  1 snd
ttm                    72698  1 radeon
drm_kms_helper         46907  1 radeon
parport_pc             31981  1 
mac_hid                13037  0 
drm                   243792  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
hid_generic            12492  0 
usbhid                 47035  0 
hid                    87604  2 hid_generic,usbhid
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
sata_sis               12711  2 
sis190                 22210  0 
crc_itu_t              12627  1 firewire_core
psmouse                91033  0 
mii                    13654  1 sis190
floppy                 55378  0 

```

- iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

- dmesg | grep ndis
```
[   86.055315] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   86.489557] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[   86.489613] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[   86.489906] ndiswrapper (load_sys_files:200): couldn't prepare driver 'rt2870'
[   86.490940] ndiswrapper (load_wrap_driver:103): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[   86.491029] usbcore: registered new interface driver ndiswrapper
```

---

### Post by praseodym on 2014-05-26
Ok, try the 2nd driver and run the commands again

---

### Post by brunolabs on 2014-05-26
It returns exactly the same results. :(
I also restarted the system just to make sure there were no pending configurations.

---


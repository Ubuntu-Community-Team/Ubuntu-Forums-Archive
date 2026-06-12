---
title: "Ndiswrapper + RTL8187"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by Jexel on 2007-07-03
Okay, Ubuntu comes with native RTL8187 drivers (i think)...so my wireless connection works...however, the connection isn't stable, it tends to hang and dropout at times forcing me to restart my computer...

I tried giving ndiswrapper a go however I can't seem to get that working either...

Here is what lspci gives me:

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)

I'm using RTL8187 from my asus p5b-deluxe wifi mobo. I also installed ndisgtk to help me out, but when i add the driver downloaded from the official asus website it says that the hardware isn't present...

I have no clue as to what to do from this point on.

I'm fed up of restarting my computer everything my internet hangs. Is there a method to just restart the wireless connection?

---

### Post by kevdog on 2007-07-03
Im having problems interpreting your output above.  Is there anyway you could post:
lshw -C network

---

### Post by Jexel on 2007-07-03
*-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 12
       serial: 00:18:f3:ee:db:7c
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:fe8fc000-fe8fffff ioport:9800-98ff irq:17
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@05:04.0
       logical name: eth0
       version: 14
       serial: 00:18:f3:ee:db:00
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.9 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: iomemory:feaf4000-feaf7fff ioport:b800-b8ff irq:19
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:0c:c5:08
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.137 multicast=yes wireless=IEEE 802.11g

---

### Post by kevdog on 2007-07-03
How about lsmod??  Your hardware wasnt showing up in the lspci statement, and no driver is listed with the lshw statement.  Its really strange!!!  Check dmesg and see if you are getting error messages!  Also what is the contents of the following file: /etc/modprobe.d/blacklist.

---

### Post by Jexel on 2007-07-03
**Here is lsmod:**
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ipv6                  268960  14 
ppdev                  10116  0 
acpi_cpufreq           10056  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  2 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pcc_acpi               13184  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
video                  16388  0 
ac                      6020  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
battery                10756  0 
button                  8720  0 
dock                   10268  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
container               5248  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
nls_utf8                3072  2 
ntfs                  107764  2 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
rc80211_simple          6400  1 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                34944  0 
snd_timer              23684  2 snd_pcm,snd_seq
mac80211              175364  2 rc80211_simple,rtl8187
cfg80211               22920  1 mac80211
serio_raw               7940  0 
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              25244  1 
nvidia               4713780  32 
psmouse                38920  0 
af_packet              23816  14 
sk98lin               156896  0 
eeprom_93cx6            4352  1 rtl8187
pcspkr                  4224  0 
i2c_core               22656  2 i2c_ec,nvidia
agpgart                35400  2 intel_agp,nvidia
sky2                   43528  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  6 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
ata_generic             9092  0 
ata_piix               15492  5 
pata_jmicron            7808  0 
floppy                 59524  0 
ahci                   22020  0 
libata                125720  4 ata_generic,ata_piix,pata_jmicron,ahci
scsi_mod              142348  5 sbp2,sg,sd_mod,sr_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
generic                 5124  0 [permanent]
skge                   40848  0 
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  4 rtl8187,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

**Here is the blacklist:**
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

**and in dmesg i get:**

.
.
.
[ 1810.428544]     Additional sense: Medium not present
[ 1810.428549] end_request: I/O error, dev sr0, sector 4
[ 1810.435486] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1810.435491]     Additional sense: Medium not present
[ 1810.435496] end_request: I/O error, dev sr0, sector 0
[ 1810.446481] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1810.446488]     Additional sense: Medium not present
[ 1810.446493] end_request: I/O error, dev sr0, sector 4
[ 1810.453430] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1810.453435]     Additional sense: Medium not present
[ 1810.453441] end_request: I/O error, dev sr0, sector 0
[ 1810.458451] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1810.458458]     Additional sense: Medium not present
[ 1810.458464] end_request: I/O error, dev sr0, sector 4
[ 1810.459479] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1810.459483]     Additional sense: Medium not present
[ 1810.459488] end_request: I/O error, dev sr0, sector 0
[ 1810.465418] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1810.465423]     Additional sense: Medium not present
[ 1810.465428] end_request: I/O error, dev sr0, sector 4
[ 1854.170261] wlan0: starting scan
[ 1855.399649] wlan0: scan completed
[ 1975.230332] wlan0: starting scan
[ 1976.459702] wlan0: scan completed
[ 2096.287954] wlan0: starting scan
[ 2097.561143] wlan0: scan completed
[ 2217.384133] wlan0: starting scan
[ 2218.657385] wlan0: scan completed
[ 2338.490102] wlan0: starting scan
[ 2339.719474] wlan0: scan completed
[ 2459.497093] wlan0: starting scan
[ 2460.774365] wlan0: scan completed
[ 2580.595230] wlan0: starting scan
[ 2581.868546] wlan0: scan completed
[ 2701.693428] wlan0: starting scan
[ 2702.922814] wlan0: scan completed
[ 2822.700258] wlan0: starting scan
[ 2823.973552] wlan0: scan completed
[ 2943.742439] wlan0: starting scan
[ 2945.015722] wlan0: scan completed
[ 3064.832583] wlan0: starting scan
[ 3066.061963] wlan0: scan completed
[ 3185.838907] wlan0: starting scan
[ 3187.112178] wlan0: scan completed
[ 3306.936926] wlan0: starting scan
[ 3308.166322] wlan0: scan completed
[ 3427.936905] wlan0: starting scan
[ 3429.166239] wlan0: scan completed

I don't see why my hardware isn't showing up :| I mean...I'm connected to my wireless network :|

---

### Post by kevdog on 2007-07-03
Its strange the 8187 driver is loaded,

from lsmod:

> rtl8187 34944 0 

However at the same time you are blacklisting the module:
> blacklist r818x
blacklist r8187

Can you unblacklist the modules, gksu gedit /etc/modprobe.d/blacklist
and then just put a # sign in front of the two above blacklist statements?

Reboot.

I thought there was a bug in the above modules that you had to fake the essid by putting an extra character behind the essid name.  Something like if your essid was linksys, then when you manually configured the network the essid had to be linksysx.

---

### Post by Jexel on 2007-07-03
okay i did everything that you said, What info would you like me to output?

---

### Post by bollix47 on 2007-07-03
The reason you're not seeing 8187 using lspci is because it's tied to usb.

Try sudo lsusb -v | more and you will see it.

---

### Post by Jexel on 2007-07-03
when i type lsusb -v | more i get

.
.
.
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8187 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
.
.
.
So I guess it exists?

Sorry is this is such a bother...

---

### Post by bollix47 on 2007-07-03
No problem.  

I'm very interested in an answer to this problem as I have the same problem with the same equipment in Feisty with the dropped connections.  

As you can see your 8187 is at Bus 1 Device 2.

FYI.  I also have Gutsy on this computer and it does not drop the connections.

---

### Post by Jexel on 2007-07-03
when i right click the connection icon and select "connection information" i get an error saying "Could not find some required resources (the glade file)!" however, if i do this when it's connection or the near the exact moment it connects it works perfectly...

I've also tried to unload the rtl8187 driver during the installation of ndiswrapper using "rmmod" this was suggested on [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/)

*sigh*

---

### Post by kevdog on 2007-07-03
If you want to use ndiswrapper then you will need some help to set it up (hence the errors).  You will also require windows drivers for the wireless device (probably came on a CD -- I know my Asus motherboard came with a disk for the built in wireless).  Usually ndiswrapper works best with XP drivers, however Ive seen some people report the win98 drivers work best.  When we get to this step we might need to experiment.

---

### Post by panurge77 on 2007-07-05
You got to blacklist rtl8187 and not r8187. Then install ndiswrapper and windows 98 drivers. The tricky part is disabling network manager. I dont know why, but it wont work with ndiswrapper. You need to disable networkmanager and set the old /etc/network/interfaces file. You may also need to add ndiswrapper to /etc/modules so it wont slow down your boot.

edit: can't remember how i disabled networkmanager

---

### Post by kevdog on 2007-07-05
I think if you do not allowing roaming and set up the interfaces manually, then I think you effectively work-around network manager.

Cant believe I didnt spot the typo on the blacklist earlier -- I feel stupid!

---

### Post by panurge77 on 2007-07-05
> Stop network manager

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Create two files with only the word 'exit' in them. These files are:

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

From here: [https://help.ubuntu.com/community/Wi...NetworkManager](https://help.ubuntu.com/community/Wi...NetworkManager)

Then just edit /etc/network/interfaces as it was on previous ubuntu releases. I use the passkey before the essid on the interfaces file because it was needed on RTL8180. I dont know if it's needed for the 8187 too.

---

### Post by Jexel on 2007-07-06
Thanks for all the help

r8187 was already included in the list of blacklists so i think i'll leave it there. This is what I've done currently:

I typed in "ndiswrapper -l" into the terminal and I get this.
```

netrtuw : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)

```
I then blacklisted rtl8187, I disable network manager and then load ndiswrapper module however nothing appears to be happening. I'm guessing it's to do with my interface file. Can somebody provide me with a template as to what the interface file should look like?

Also, what should I be expecting when I run the ndiswrapper module?

---

### Post by kevdog on 2007-07-06
Ok,  lets just perform a few checks:
lshw -C network
ndiswrapper -v
ndiswrapper -l
sudo modprobe -l | grep ndiswrapper
dmesg | grep ndiswrapper

In the installation process did you issue command
sudo ndiswrapper -m

You can do it again -- it will not hurt

Please then include your 
/etc/network/interfaces
/etc/iftab

Thanks

---

### Post by fredj on 2007-07-06
The info you have posted seems to show that your wireless card is now using the skge driver. Is this the
driver you loaded with ndiswrapper. If so where did you get your version of ndiswrapper? If you got the
standard version from the repositories then the bad news is that it doesn't work. Open a terminal and
type sudo ndiswrapper -v. Then post the output from that here.

---

### Post by panurge77 on 2007-07-06
I use the repositories version and it works (though ndiswrapper gnome gui is a liar and tell me the driver is not installed). 

/etc/network/interfaces should look like this about wlan
```
auto wlan0
iface wlan0 inet dhcp
wireless-key ********
wireless-essid *******
```

---

### Post by Jexel on 2007-07-06
I'm still using the native rtl8187 drivers at the moment so here are the results as requested.

lshw -C network
```
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 12
       serial: 00:18:f3:ee:db:7c
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:fe8fc000-fe8fffff ioport:9800-98ff irq:17
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@05:04.0
       logical name: eth0
       version: 14
       serial: 00:18:f3:ee:db:00
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.9 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: iomemory:feaf4000-feaf7fff ioport:b800-b8ff irq:18
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:0c:c5:08
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.137 multicast=yes wireless=IEEE 802.11g

```

ndiswrapper -v
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 

```

ndiswrapper -l
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 
jexel@b166er:~$ sudo ndiswrapper -l
netrtuw : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)

```

sudo modprobe -l | grep ndiswrapper
```
/lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
```

dmesg | grep ndiswrapper gives me nothing

sudo ndiswrapper -m gives me "module configuration already contains alias directive"

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

/etc/iftab
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:18:f3:ee:db:00 arp 1
eth1 mac 00:18:f3:ee:db:7c arp 1
wlan0 mac 00:15:af:0c:c5:08 arp 1
```

---

### Post by bung33 on 2007-07-06
To answer an original question, use this command to restart networking without restarting the computer...

```
sudo /etc/init.d/networking restart
```

Hope that helps until you can get the card working properly...

---

### Post by panurge77 on 2007-07-06
I wrote a guide, hope it helps.

[http://ubuntuforums.org/showthread.php?p=2973537#post2973537](http://ubuntuforums.org/showthread.php?p=2973537#post2973537)

---

### Post by Jexel on 2007-07-06
I would like to thank kevdog, bollix47, bung33 and panurge77 for helping me. Greatly appreciated. My internet finally works :)

---


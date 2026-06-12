---
title: "[SOLVED] wifi problem Amilo 1520 - wifi switch not on?"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by pognonec on 2008-06-08
I have a home network with a router (ethernet and wireless), that works fine either by wifi or ethernet with XP as well as with a Ubuntu Hardy laptop (Dell Inspiron 8000). I also have an Amilo laptop, with Ubuntu Hardy. Ethernet works fine, and wifi appears fine as far as wifi radar is concerned: it sees the wifi network (static IP, WEP key). However, I cannot connect through wifi with this machine! And the little blue LED on the keyboard for the wifi switch is not on.
Any idea? Thanx in advance!

I paste below some related info:

aline@Aline:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"


aline@Aline:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 008: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
aline@Aline:~$ 


aline@Aline:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)



aline@Aline:~$ sudo lshw -C network
[sudo] password for aline: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:e2:51:db
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:82:c6:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.0.9 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s


aline@Aline:~$ lsmod
Module                  Size  Used by
hci_usb                16540  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
e100                   37388  0 
mii                     6400  1 e100
binfmt_misc            12808  1 
i915                   32512  2 
drm                    82580  3 i915
rfcomm                 41744  2 
l2cap                  25728  11 rfcomm
bluetooth              61156  3 hci_usb,rfcomm,l2cap
nls_iso8859_1           4992  0 
nls_cp437               6656  0 
vfat                   14464  0 
fat                    54556  1 vfat
ppdev                  10372  0 
acpi_cpufreq           10796  0 
cpufreq_ondemand        9740  2 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
ipv6                  267780  16 
snd_hda_intel         344728  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
usb_storage            73664  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
libusual               19108  1 usb_storage
psmouse                40336  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
serio_raw               7940  0 
snd_seq_dummy           4868  0 
sr_mod                 17956  0 
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
cdrom                  37408  1 sr_mod
cfg80211               15112  1 iwlwifi_mac80211
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
sdhci                  19076  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video                  19856  0 
output                  4736  1 video
ricoh_mmc               4352  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_core               51460  1 sdhci
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               13092  0 
ac                      6916  0 
button                  9232  0 
battery                14212  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pata_acpi               8320  0 
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
evdev                  13056  8 
pcspkr                  4224  0 
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
ata_piix               19588  0 
ohci1394               33584  0 
ahci                   28420  2 
ieee1394               93752  2 sbp2,ohci1394
ata_generic             8324  0 
libata                159344  4 pata_acpi,ata_piix,ahci,ata_generic
scsi_mod              151436  6 sbp2,usb_storage,sr_mod,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  6 hci_usb,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 



aline@Aline:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"colombo"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:07:CB:53:78:83   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


aline@Aline:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:82:c6:b8  
          inet adr:192.168.0.9  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::216:36ff:fe82:c6b8/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:13147 erreurs:0 :0 overruns:0 frame:0
          TX packets:12772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:12655334 (12.0 MB) Octets transmis:1854465 (1.7 MB)

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1743 erreurs:0 :0 overruns:0 frame:0
          TX packets:1743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:89938 (87.8 KB) Octets transmis:89938 (87.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:e2:51:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-E2-51-DB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)



aline@Aline:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

aline@Aline:~$ uname -r -m 
2.6.24-18-generic i686



aline@Aline:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.9
netmask 255.255.255.0
gateway 192.168.0.254

auto eth0

iface wlan0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.254
wireless-key 39EBC17316FF2C4D0B235FC252
wireless-essid colombo

auto wlan0

---

### Post by chili555 on 2008-06-08
The usual way to see if the switch is the problem is to do:```
sudo cat /var/log/messages | grep switch
```However, I notice your *interfaces *file asks for eth0 **and** wlan0 to be started automatically. I'm fairly certain that when it gets an IP address wired:> ip=192.168.0.9 latency=64 link=yes it gives up. Try detaching the wire and reboot. Then can you:```
ping -c3 www.google.com
```

---

### Post by pognonec on 2008-06-08
Thank you for your help, Chili555. Unfortunately, I am still stuck:

> **chili555 said:**
> The usual way to see if the switch is the problem is to do:```
sudo cat /var/log/messages | grep switch
```

Below is what I got, and it went on like that for many lines. I have no idea what to do with it...

aline@Aline:~$ sudo cat /var/log/messages | grep switch
[sudo] password for aline: 
Jun  8 10:20:47 Aline kernel: [  405.311496] SMP alternatives: switching to UP code
Jun  8 10:20:47 Aline kernel: [   58.220287] SMP alternatives: switching to SMP code
Jun  8 10:36:12 Aline kernel: [  984.073604] Kill switch must be turned off for wireless networking to work.
Jun  8 10:44:11 Aline kernel: [ 1463.028881] Kill switch must be turned off for wireless networking to work.


> **chili555 said:**
> However, I notice your *interfaces *file asks for eth0 **and** wlan0 to be started automatically. I'm fairly certain that when it gets an IP address wired:it gives up. Try detaching the wire and reboot. Then can you:```
ping -c3 www.google.com
```

I did what you suggested, but it does not work either: I get:

aline@Aline:~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

Any suggestion welcome!

---

### Post by chili555 on 2008-06-08
> Kill switch must be turned off for wireless networking to work.
It means your suspicion, in the title of this thread, is correct. There is a physical switch or key combination that turns the wireless radio off; Fn+F5 or some other combination. Your wireless is not going to activate until you toggle the switch or key combination.

---

### Post by pognonec on 2008-06-09
> **chili555 said:**
> It means your suspicion, in the title of this thread, is correct. There is a physical switch or key combination that turns the wireless radio off; Fn+F5 or some other combination. Your wireless is not going to activate until you toggle the switch or key combination.

Well well, there is a little button, looking a bit like this:
((i))
that I thought was the kill switch.

When pressed TWICE (yes, twice??!!), it starts flashing. But sudo cat /var/log/messages | grep switch still tells me that: 

Jun  8 10:20:47 Aline kernel: [  405.311496] SMP alternatives: switching to UP code
Jun  8 10:20:47 Aline kernel: [   58.220287] SMP alternatives: switching to SMP code
Jun  8 10:36:12 Aline kernel: [  984.073604] Kill switch must be turned off for wireless networking to work.
Jun  8 10:44:11 Aline kernel: [ 1463.028881] Kill switch must be turned off for wireless networking to work.
Jun  8 11:15:17 Aline kernel: [ 3326.205350] Kill switch must be turned off for wireless networking to work.
Jun  8 11:15:17 Aline kernel: [ 3326.752584] Kill switch must be turned off for wireless networking to work.
Jun  8 11:15:40 Aline kernel: [ 3349.380103] Kill switch must be turned off for wireless networking to work.
Jun  8 11:15:40 Aline kernel: [ 3349.851821] Kill switch must be turned off for wireless networking to work.
Jun  8 11:15:41 Aline kernel: [ 3350.283445] Kill switch must be turned off for wireless networking to work.
Jun  8 11:20:20 Aline kernel: [ 3629.733326] Kill switch must be turned off for wireless networking to work.
Jun  8 11:20:40 Aline kernel: [ 3649.188670] Kill switch must be turned off for wireless networking to work.
Jun  8 14:23:46 Aline kernel: [ 7046.240416] Kill switch must be turned off for wireless networking to work.
Jun  8 14:23:47 Aline kernel: [ 7047.054982] Kill switch must be turned off for wireless networking to work.
Jun  8 14:23:49 Aline kernel: [ 7047.623310] Kill switch must be turned off for wireless networking to work.
Jun  8 14:23:50 Aline kernel: [ 7048.135210] Kill switch must be turned off for wireless networking to work.
Jun  8 14:23:50 Aline kernel: [ 7048.448040] Kill switch must be turned off for wireless networking to work.
Jun  8 14:38:00 Aline kernel: [ 7310.419484] Kill switch must be turned off for wireless networking to work.
Jun  8 14:42:58 Aline kernel: [ 7408.090804] Kill switch must be turned off for wireless networking to work.
Jun  8 14:43:00 Aline kernel: [ 7408.532209] Kill switch must be turned off for wireless networking to work.
Jun  8 14:46:27 Aline kernel: [   16.380282] SMP alternatives: switching to UP code
Jun  8 14:46:27 Aline kernel: [   16.739761] SMP alternatives: switching to SMP code
Jun  8 14:46:27 Aline kernel: [   17.002804] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  8 14:46:27 Aline kernel: [   35.274577] Kill switch must be turned off for wireless networking to work.
Jun  8 14:46:27 Aline kernel: [   36.605414] Kill switch must be turned off for wireless networking to work.
.......and so on for pages.....

I have not been able to find a way for turning this ... kill switch off. Does anybody know the trick? Amilo 1520 users? Anyone?

---

### Post by chili555 on 2008-06-09
I saw this: [http://www.amilo-forum.com/topic,929,-linux-on-amilo-li-1718.html](http://www.amilo-forum.com/topic,929,-linux-on-amilo-li-1718.html) and especially:> If you press F2 on boot you can set the wireless card to turn on at boot up.
that might avoid the problem of programming the switch to do the same job.I realize the post concerns a 1718, but give it a try.

I'm still looking.

---

### Post by pognonec on 2008-06-10
Thanks for the F2 trick, chili555. So now my light flashes, I see my network in wifi radar, that tells me that I am connected to the wireless network through the dedicated fixed IP (that is different from the one for the ethernet connection), but... it still does not work!

---

### Post by chili555 on 2008-06-10
When it says it's connected, please open up a terminal and let us see:```
ifconfig
iwconfig
```Thanks.

---

### Post by pognonec on 2008-06-11
> **chili555 said:**
> When it says it's connected, please open up a terminal and let us see:```
ifconfig
iwconfig
```

Here it is:

aline@Aline:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:82:c6:b8  
          inet adr:192.168.0.9  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::216:36ff:fe82:c6b8/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:850 erreurs:0 :0 overruns:0 frame:0
          TX packets:917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:573618 (560.1 KB) Octets transmis:162560 (158.7 KB)

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1674 erreurs:0 :0 overruns:0 frame:0
          TX packets:1674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:83700 (81.7 KB) Octets transmis:83700 (81.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:e2:51:db  
          inet adr:192.168.0.10  Bcast:192.168.0.255  Masque:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:57 erreurs:0 :0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:7749 (7.5 KB) Octets transmis:3619 (3.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-E2-51-DB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)



aline@Aline:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"colombo"  Nickname:"colombo"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:07:CB:53:78:83   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=99/100  Signal level=-22 dBm  Noise level=-48 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2008-06-11
Once again, I think your wired connection has taken over. Please detach the wire, reboot and then let us see:```
ping -c3 192.168.0.254
sudo iwlist wlan0 scan
```Thanks.

---

### Post by pognonec on 2008-06-11
Thanks for still being there, chili555.
Here is what I got to the two code requests after booting without ethernet plugged in (but I had to replug it in to post this reply, unfortunately...) Curiously, the ping request was issued from the ethernet address (192.168.0.9), and not from the wifi address (192.168.0.10). Could that be the reason of my problem? How can I force the wifi address to be used?

aline@Aline:~$ ping -c3 192.168.0.254
PING 192.168.0.254 (192.168.0.254) 56(84) bytes of data.
From 192.168.0.9 icmp_seq=1 Destination Host Unreachable
From 192.168.0.9 icmp_seq=2 Destination Host Unreachable
From 192.168.0.9 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.254 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2008ms
, pipe 3

aline@Aline:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:07:CB:53:78:83
                    ESSID:"colombo"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=96/100  Signal level=-32 dBm  Noise level=-57 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000276dd172b5
          Cell 02 - Address: 00:16:CF:38:97:A4
                    ESSID:"N9UF_TEL9COM"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/100  Signal level=-85 dBm  Noise level=-57 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000024536249189

---

### Post by pognonec on 2008-06-11
I just tried something else: after rebooting with no wire in, I opened network manager, and inactivated the ethernet connection (192.168.0.9). Then I pinged my gateway. Here is what I got: this time the wifi connection was used, but still no ping!

aline@Aline:~$ ping -c3 192.168.0.254
PING 192.168.0.254 (192.168.0.254) 56(84) bytes of data.
From 192.168.0.10 icmp_seq=1 Destination Host Unreachable
From 192.168.0.10 icmp_seq=2 Destination Host Unreachable
From 192.168.0.10 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.254 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3

---

### Post by pognonec on 2008-06-17
Since I did not understand what the problem was, and could  not fix it despite several advice (thanks for your help, chili 555), I backed up my data, did a fresh reinstall of the same version (8.04), but sat up only the wifi (fixed IP and all, as described above), not the ethernet connection.
And guess what? wifi works great...

So it may be a little excessive way of fixing the problem, but if you are confronted to a "ghost" wifi connection, well, you have a solution here...

---


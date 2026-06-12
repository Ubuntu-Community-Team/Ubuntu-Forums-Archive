---
title: "Wireless is not working unless &lt;sudo iwlist scan&gt; is run"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by akamaras2 on 2013-09-26
Dear all,

I have recently reinstalled Ubuntu 12.04.3 LTS on my machine. Some effort allowed me to set up a Wireless connection by installing b43 (LP-PHY) driver. Unfortunatelly, it only starts working if I run <sudo iwlist scan> (running <iwlist scan> does not help) a couple of times.
I have placed b43 in my /etc/modules (although this is probably not relevant in my situation).

Now I see some difference in Kernell message buffer, which I can't quite understand:

dmesg | grep b43 #before initiating <sudo iwlist scan>

```
[    6.622358] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    6.664355] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   14.844276] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
```

dmesg | grep b43 #after <sudo iwlist scan>

```
[    6.441881] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    6.488247] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   14.616258] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   92.579067] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   92.620356] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   92.852386] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
```

Some of the other outputs I get (if that's of any relevance). I get them even when Wireless is not active:

sudo lshw -C network

```
  *-network              
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:eb:a8:23
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f69f0000-f69fffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:24:2b:a6:2c:36
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.8.0-30-generic firmware=478.104 ip=192.168.1.23 link=yes multicast=yes wireless=IEEE 802.11bg
```

rfkill list all

```
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

lspci -nn

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

sudo ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:21:9b:eb:a8:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:23941 (23.9 KB)  TX bytes:23941 (23.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:a6:2c:36  
          inet addr:192.168.1.23  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fea6:2c36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2813251 (2.8 MB)  TX bytes:852311 (852.3 KB)


```

I would be thankfull for any usefull suggestions for this rather esotheric problem.

---

### Post by theDaveTheRave on 2013-09-26
your ran an ifconfig,

is this the output before or after you have managed to get the card to work (after the sudo iwlist scan).

It would be interesting to see the ifconfig result before and after. If the result of your posting is before the scan, then you should try a ping, so see if you are able to ping a page.

David

---

### Post by akamaras2 on 2013-09-26
Dear theDaveTheRave,

I am sorry for stating the information in ambiguous manner. If I don't run <sudo iwlist scan> that's what I get from <sudo ifconfig wlan0>

```
wlan0     Link encap:Ethernet  HWaddr 00:24:2b:a6:2c:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

In the meantime I have discovered that if I run dmesg before running <sudo iwlist scan> I get something like this:

```
[  222.474703] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  222.516364] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[  222.541046] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  222.541787] Broadcom 43xx driver loaded [ Features: PNL ]
[  222.744486] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  228.270370] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  228.270775] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

And afterwards dmesg becomes like this:

```
[   41.082239] audit_printk_skb: 24 callbacks suppressed
[   41.082244] type=1400 audit(1380203352.840:31): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1678 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  241.193450] wlan0: authenticate with 24:95:04:75:f3:64
[  241.216559] wlan0: send auth to 24:95:04:75:f3:64 (try 1/3)
[  241.220513] wlan0: authenticated
[  241.224118] wlan0: associate with 24:95:04:75:f3:64 (try 1/3)
[  241.226870] wlan0: RX AssocResp from 24:95:04:75:f3:64 (capab=0x411 status=0 aid=1)
[  241.227641] wlan0: associated
[  241.227668] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

---

### Post by Hadaka on 2013-09-26
Hi, Lets rummage around in your files and see if
we can figure this out. Please post the output of..
```
lsmod
cat/etc/modules
cat /etc/NetworkManager/NetworkManager.conf
```
thanks.

---

### Post by akamaras2 on 2013-09-26
Dear Hadaka, this is the output given by the following commands:

lsmod

```
Module                  Size  Used by
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     36564  1 
snd_hda_codec_idt      64649  1 
snd_hda_intel          38819  3 
snd_hda_codec         118650  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
uvcvideo               72250  0 
joydev                 17329  0 
videobuf2_core         39385  1 uvcvideo
videodev               96131  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12920  1 uvcvideo
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  550344  3 
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         47749  1 i915
r852                   17873  0 
snd_timer              28931  2 snd_pcm,snd_seq
drm                   233935  4 i915,drm_kms_helper
sm_common              16772  1 r852
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
nand                   54027  2 r852,sm_common
gpio_ich               13278  0 
coretemp               13324  0 
snd                    57014  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
arc4                   12509  2 
mtd                    38990  2 sm_common,nand
soundcore              12600  1 snd
dell_laptop            17209  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
nand_ids                8547  1 nand
r592                   17808  0 
dcdbas                 14065  1 dell_laptop
nand_bch               13003  1 nand
psmouse                82769  0 
dell_wmi               12601  0 
bch                    21767  1 nand_bch
sparse_keymap          13658  1 dell_wmi
serio_raw              13031  0 
i2c_algo_bit           13316  1 i915
nand_ecc               13105  1 nand
microcode              18433  0 
memstick               15885  1 r592
wmi                    18744  1 dell_wmi
lpc_ich                17048  0 
mac_hid                13077  0 
video                  19116  1 i915
b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453853  2 b43,mac80211
bcma                   39810  1 b43
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35914  0 
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ahci                   25631  2 
libahci                26336  1 ahci
sdhci_pci              18265  0 
sdhci                  32339  1 sdhci_pci
tg3                   150733  0 
ptp                    18232  1 tg3
pps_core               13736  1 ptp
ssb                    51554  1 b43


```

cat /etc/modules

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
b43
#ssb


```

cat /etc/NetworkManager/NetworkManager.conf

```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```

---

### Post by Hadaka on 2013-09-26
Thanks, lets see if you have your ESSID being managed by NetworkManager
please post..
```
nmcli -p con
cat /etc/network/interfaces
```
is your essid in the list?

---

### Post by akamaras2 on 2013-09-26
nmcli -p con (my ESSID is SRF_F360)

```
======================================================================================================================
                                                   Connection list
======================================================================================================================
NAME                      UUID                                   TYPE              TIMESTAMP-REAL                    
----------------------------------------------------------------------------------------------------------------------
Wired connection 1        647ffbd8-d1ea-491c-a891-c02001afd852   802-3-ethernet    Thu 26 Sep 2013 04:36:30 PM CEST  
SFR_F360                  b81ea941-b4e9-4230-946e-00e5cf0af152   802-11-wireless   Thu 26 Sep 2013 08:01:24 PM CEST  

```

cat /etc/network/interfaces

```
auto lo
iface lo inet loopback
```

---

### Post by Hadaka on 2013-09-26
looking great so far, ok lets do this..
since you were messing about a bit..just to
make sure..please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
then from a wired connection do..
```
sudo apt-get update
sudo apt-get upgrade
```
when thats done,disconnect the ethernet cable and
boot
then..
click your wireless icon (network manager)
click Edit Connections
click Wireless
click your essid
click edit..then configure like the attached...includeing the dns
also be sure to check connect automaticlly
[ATTACH=CONFIG]246524[/ATTACH][ATTACH=CONFIG]246525[/ATTACH]
boot
does it connect correctly now?

---

### Post by akamaras2 on 2013-09-26
Dear Hadaka,

This is the output after I've made the modifications:

sudo apt-get remove --purge bcmwl-kernel-source

```
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu diffstat module-assistant quilt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

sudo apt-get upgrade

```
Reading package lists... Done
Building dependency tree      
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

So nothing have changed I assume. When I change the connection parameters as you suggested - I can connect to Wireless, but, as previously, after running ```
sudo iwlist scan
``` a couple of times.

Unfortunatelly, the problem remains.

---

### Post by Hadaka on 2013-09-26
interesting...
please do..
```
sudo apt-get remove --purge firmware-b43-lpphy-installer
```
then from a wired connection do..
```
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -rf b43
sudo modprobe b43
```
any improvement?

---

### Post by akamaras2 on 2013-09-26
Unfortunatelly, no change. I still get this ```
[   20.549205] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
``` on dmesg and still need to run sudo iwlist scan.

---

### Post by Hadaka on 2013-09-26
hi, this..
"IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready"
is normal, it is for IP6 you are using IPv4
IPv6 should be set to IGNORE..yet you will till get this message.
Did you configure your Network Manager  like the attached sent
earlier?

---

### Post by akamaras2 on 2013-09-26
Yes, it is set to ignore. And I actually still get this at dmesg after connecting:

```
[  225.089435] wlan0: authenticate with 24:95:04:75:f3:64
[  225.100662] wlan0: send auth to 24:95:04:75:f3:64 (try 1/3)
[  225.102691] wlan0: authenticated
[  225.104213] wlan0: associate with 24:95:04:75:f3:64 (try 1/3)
[  225.106966] wlan0: RX AssocResp from 24:95:04:75:f3:64 (capab=0x411 status=0 aid=1)
[  225.107809] wlan0: associated
[  225.107839] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

---

### Post by Hadaka on 2013-09-26
Yes, that is normal,we could disable IPv6 but i doubt 
thats the problem. To disable do..
```
sudo gedit /etc/sysctl.conf
```
add the following lines to the bottom of the file
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```
save and close gedit. 
to view the changed file do..
```
sudo sysctl -p
```
*Note this will be YOUR choice..i dont think this is the problem
but it wont hurt anything.
lastly, Looking around i found some post with a different driver for your card.
so please do..
from a wired connection
```
sudo apt-get remove --purge firmware-b43-lpphy-installer
```
```
sudo apt-get install linux-firmware-nonfree 
sudo modprobe -rf b43
sudo modprobe -v b43
```
thanks.

---

### Post by akamaras2 on 2013-09-26
sudo gedit /etc/sysctl.conf

Added your line at the end of sysctl.conf. Restarted the computer and still get ```
[   56.447589] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
``` after <sudo iwlist scan>

When sudo sysctl -p is run:

```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

Then done:

sudo apt-get remove --purge firmware-b43-lpphy-installer
sudo apt-get remove --purge b43-fwcutter

And sudo apt-get install linux-firmware-nonfree && sudo modprobe -rf b43

After sudo modprobe -v b43 get this output:

```
insmod /lib/modules/3.8.0-30-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/b43/b43.ko
```

Then I run sudo iwlist scan couple of times and Wireless is on again.
lsmod

```
Module                  Size  Used by
b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453853  2 b43,mac80211
ssb                    51554  1 b43
bcma                   39810  1 b43
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     36564  1 
snd_hda_codec_idt      64649  1 
snd_hda_intel          38819  3 
snd_hda_codec         118650  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
uvcvideo               72250  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
videobuf2_core         39385  1 uvcvideo
videodev               96131  2 uvcvideo,videobuf2_core
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
joydev                 17329  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  550344  3 
r852                   17873  0 
sm_common              16772  1 r852
snd                    57014  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand                   54027  2 r852,sm_common
mtd                    38990  2 sm_common,nand
drm_kms_helper         47749  1 i915
coretemp               13324  0 
soundcore              12600  1 snd
drm                   233935  4 i915,drm_kms_helper
nand_ids                8547  1 nand
gpio_ich               13278  0 
nand_bch               13003  1 nand
dell_wmi               12601  0 
bch                    21767  1 nand_bch
r592                   17808  0 
dell_laptop            17209  0 
sparse_keymap          13658  1 dell_wmi
memstick               15885  1 r592
dcdbas                 14065  1 dell_laptop
i2c_algo_bit           13316  1 i915
nand_ecc               13105  1 nand
psmouse                82769  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
microcode              18433  0 
serio_raw              13031  0 
wmi                    18744  1 dell_wmi
lpc_ich                17048  0 
mac_hid                13077  0 
arc4                   12509  2 
video                  19116  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              18265  0 
sdhci                  32339  1 sdhci_pci
firewire_ohci          35914  0 
ahci                   25631  2 
libahci                26336  1 ahci
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   150733  0 
ptp                    18232  1 tg3
pps_core               13736  1 ptp

```

Problem persists

---

### Post by akamaras2 on 2013-09-26
It seems b43 driver is still in use although I've removed it: ls /sys/class/net/wlan0/device/driver/module/drivers ```
bcma:b43  ssb:b43
``` Don't get it.

---

### Post by Hadaka on 2013-09-26
b43 is in use because its suppose to be in use.
your card requires the b43,ssb,bcma modules
so if you have them blacklisted somewhere or
deleted..you need to add them back. Also I noted
you made mention of fwcutter..all these drivers are separate..fwcutter
doesnt belong with the lppy or the linux non free. Im guessing when
you undo whatever you deleted or blacklisted...your connection will
behave as its suppose to. Once you get that figured out and restore
the b43 files to where they belong if you have problems..post back.
thanks.

---

### Post by akamaras2 on 2013-09-26
Un-blacklisted bcma, still the same problem. And firmware-b43-lpphy-installer co-installs with b43-fwcutter when you use Synaptic packet manager. I would say they are somehow interdependent, but you know better.

Well, thank you a lot for the help and the effort. I can live with this problem, it's just bit annoying since everything was running fine in 11.10. Now I'm facing multiple issues since upgrading to 12.04. Probably that's a sign that I should switch to Debian after using Ubuntu for 7 years or so.

---

### Post by theDaveTheRave on 2013-09-27
> **akamaras2 said:**
> 
I am sorry for stating the information in ambiguous manner.


It wasn't particularly ambiguous, more covering all the silly potential problems (like plugging in the power) before getting into config files etc.
but I'm sure you understand if the link was apparently up and had an IP address, then it would have been an entirely different sort of problem with your card.

However it looks as though hadaka is going to be the best for getting you straight....

good luck.

David

---

### Post by varunendra on 2013-09-27
> **akamaras2 said:**
> I can live with this problem, it's just bit annoying since everything was running fine in 11.10. Now I'm facing multiple issues since upgrading to 12.04. Probably that's a sign that I should switch to Debian after using Ubuntu for 7 years or so.
This problem is being reported frequently for a few days with *this particular card*. The behaviour is same - people need to scan as root to initiate a connection. I have no idea what is causing this problem but it seems to be kernel related. As such, you will most probably face the same issue with any distro that uses the same kernel.

If you have used Debian before (quite a respectable distro I must admit), you may be already aware that you can use the /etc/rc.local file to make this scanning thing automatic. A line (above the last line "exit 0") something like this -
```
sleep 30 && iwlist scan
```

The time 30 (seconds) can be increased or decreased as per whatever suits you best. Of course this is a crude workaround and I'd love to dig up the cause, and possibly the fix. Unfortunately, so far we have no clear hints. But then I haven't tried very hard either.. :)

---

### Post by theDaveTheRave on 2013-09-30
> **varunendra said:**
> 
If you have used Debian before (quite a respectable distro I must admit), you may be already aware that you can use the /etc/rc.local file to make this scanning thing automatic. A line (above the last line "exit 0") something like this -
```
sleep 30 && iwlist scan
```

I was thinking of proposing the same thing, but maybe connecting it to a 'hot key' combo.

If you are on a laptop you probably have a button to turn the wifi on/off.

you should be able to customise the script that the button calls to. Otherwise you could place a link on the desktop for all users and have it point to the same script.

here is a starting point of a script that you cold link the button to, it will test the to see if the link it up, and if not run the iwlist scan (it will do this upto 5 times in case it fails the first time ~ ie if the card isn't activated properly).

```

#!/bin/bash

#Author david myers (http://ubuntuforums.org/member.php?u=246735 or http://sourceforge.net/users/davemyersuk ~ sept 2013)
#short script to test for network connectivity via the wifi card

echo script to test wifi link
#ping the ubuntu forums address (www.ubuntuforums.com or 91.189.94.12), one time only
#you should probably change this to the numeric IP address of your
#dhcp  server (ie your wifi box ~ often something like 192.0.0.1) or nameserver of your ISP.
pingThisIP="nonesenseIP"

echo testing to $pingThisIP

`ping -c1 $pingThisIP`

#catch the return val
wifiUp=$?
loopCount=1

while  [ $loopCount -lt 5 ]; do
        echo "test $loopCount cannot reach IP $pingThisIP"
    if  ( [ $wifiUp -ne 0 ]   &&   [ $loopCount -lt 5 ] ); then
         #sleep before trying again
        `sleep 5`
        #increment our loop counter
        (( loopCount++ ))
        #re  ping the address
        `ping -c1 $pingThisIP`
        #catch the return
        wifiUp=$?
    fi
#loop back and retest
done

if [ $wifiUp -ne 0 ]; then
    echo unable to reach $pingThisIP
    exit 1;
fi

```

You could put this into its own startup file to run on boot.

Things to do to the script.

Modify to a more sensible IP address to ping (another pc on your local netwok would be good).
Add a logic control to bring the link up / down depending on current state (especially if you hook it into a hot key combo.
I haven't included an logging to dmesg ~ you chould be able to modify the echos as required.


Remember you will need to have this file saved and run as root.

scripts that are run as root are dangerous, you should not just 'run' any script as root that you get from other users.
If you are not happy about what the above script does, drop me a note and I'll add further explanations.

David

---


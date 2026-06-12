---
title: "Grayed-out &quot;Wi-Fi networks, device not ready&quot; Toshiba Satellite A200, Ubuntu 13.10"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by micha3l.1993 on 2013-11-13
Hello! 
I wanted to literally revive my old laptop by installing Ubuntu on it. Had a few issues, but finnaly got it working. Next problem is I can't get wireless working - in network manager I have grayed-out writing "Wi-Fi networks, device not ready". Earlier got some problems with grayed-out "Enable Wi-Fi" button, but I fixed it. Right now I tried a lot of different solutions, but none of them helped. The laptop is Toshiba Satellite A200, not sure about specs (don't know how to find any information about that in ubuntu) but probably some Intel Core Duo, with Intel graphic card, 1gb ram. Wired connection works fine (using it right now). I am a complete newbie with Linux. I apologize for my poor English, thats not my first language.

Now some data from terminal.

$ lspci
```
toshiba@Satellite-A200:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


```

ifconfig and iwconfig
```
toshiba@Satellite-A200:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:10:47:26  
          inet addr:192.168.1.83  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe10:4726/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28517153 (28.5 MB)  TX bytes:1350209 (1.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:117738 (117.7 KB)  TX bytes:117738 (117.7 KB)

toshiba@Satellite-A200:~$ iwconfig
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.


```

lsmod
```
toshiba@Satellite-A200:~$ lsmod
Module                  Size  Used by
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18893  2 
rfcomm                 53664  12 
btusb                  23443  0 
bluetooth             323534  22 bnep,btusb,rfcomm
coretemp               13195  0 
joydev                 17097  0 
snd_hda_codec_realtek    45473  1 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
pcmcia                 51368  0 
snd_hda_intel          42658  3 
arc4                   12536  2 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
microcode              18830  0 
yenta_socket           40193  0 
lpc_ich                16864  0 
tifm_7xx1              13163  0 
psmouse                90642  0 
serio_raw              13189  0 
tifm_core              15040  1 tifm_7xx1
pcmcia_rsrc            18319  1 yenta_socket
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
iwl4965               106818  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
toshiba_bluetooth      12748  0 
i915                  589697  3 
drm_kms_helper         46867  1 i915
iwl3945                63619  0 
toshiba_acpi           18301  0 
drm                   242354  4 i915,drm_kms_helper
video                  18777  1 i915
snd                    60790  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
sparse_keymap          13708  1 toshiba_acpi
iwlegacy               87971  2 iwl3945,iwl4965
mac80211              513247  3 iwl3945,iwl4965,iwlegacy
i2c_algo_bit           13197  1 i915
wmi                    18590  1 toshiba_acpi
soundcore              12600  1 snd
mac_hid                13037  0 
cfg80211              401436  4 iwl3945,iwl4965,iwlegacy,mac80211
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
sdhci_pci              18481  0 
firewire_ohci          35257  0 
sdhci                  37468  1 sdhci_pci
firewire_core          57656  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  61434  0 
mii                    13654  1 r8169


```


dmesg
this repeats over and over
```
03800+4 (of 788), is 0x2069, s/b 0x400000
[ 1639.814260] iwl4965 0000:04:00.0: Unable to set up bootstrap uCode: -5
[ 1643.816231] iwl4965 0000:04:00.0: START_ALIVE timeout after 4000ms.
[ 1647.820196] iwl4965 0000:04:00.0: START_ALIVE timeout after 4000ms.
[ 1647.822369] iwl4965 0000:04:00.0: BSM uCode verification failed at addr 0x00003800+8 (of 788), is 0x402069, s/b 0x2069
[ 1647.822380] iwl4965 0000:04:00.0: Unable to set up bootstrap uCode: -5
[ 1647.822866] iwl4965 0000:04:00.0: BSM uCode verification failed at addr 0x00003800+4 (of 788), is 0x2069, s/b 0x400000
[ 1647.822874] iwl4965 0000:04:00.0: Unable to set up bootstrap uCode: -5


```


$ sudo lshw -C network
```
toshiba@Satellite-A200:~$ sudo lshw -C network
[sudo] password for toshiba: 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:33:27:41
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.11.0-12-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:d8000000-d8001fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:10:47:26
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.83 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:4000(size=256) memory:da000000-da000fff memory:d4000000-d401ffff


```


iwlist scan
```
toshiba@Satellite-A200:~$ iwlist scan
wlan0     Failed to read scan data : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

uname -mr
```
toshiba@Satellite-A200:~$ uname -mr
3.11.0-12-generic i686


```


$ sudo service networking restart 
it froze my computer last time so I'm not gonna do that now, until requested.


Thank you for any help, I hope I provided enough information.

---

### Post by Bucky Ball on 2013-11-13
Plenty of information, good descriptive thread title. I wish all users were this efficient. It increases your chances of getting support. ;)

The following thread is for Dell and 10.04, but might give you some clues. Essentially, make sure wireless is switched on in BIOS then reboot and see if it comes up. If not, install wicd in place of network manager. All details here:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1491147](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1491147)

---

### Post by micha3l.1993 on 2013-11-13
Wi-Fi is on, I tried to install wicd following this guide ([https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)) and failed miserably. Got [FONT=Verdana]  "Could not connect to wicd's D-Bus interface.  Check the wicd log for error messages" error, found some solution ([http://ubuntuforums.org/showthread.php?t=1457602](http://ubuntuforums.org/showthread.php?t=1457602))[/FONT], but there is no such file in var/log/wicd.

---

### Post by Bucky Ball on 2013-11-13
You are online with a cable? Sounds silly, but ...

---

### Post by micha3l.1993 on 2013-11-13
I wrote that message from my main laptop. Same as this one.

---

### Post by mörgæs on 2013-11-13
You could try running the script mentioned here

[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385)

and post the results (which are in part what you have done already, but more extensive).

---


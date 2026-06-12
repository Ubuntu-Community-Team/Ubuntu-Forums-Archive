---
title: "Wifi doesn't work if I don't boot Kubuntu after Windows / &quot;nobody cared&quot;"
date: 2018-01-07
forum: Networking &amp; Wireless
---

### Post by homme-nuage on 2018-01-07
Hello,

My system is Kubuntu 17.04.

For some time, the wifi worked well. But for a few days, I've been having this problem I already encountered with Linux Mint: the wifi works if I boot Kubuntu after shutting down Windows, but it doesn't work at all if I boot Kubuntu after shutting it down. 

At boot, when the wifi is not going not work, Kubuntu tells me:

```
[    16.680902] irq 17: nobody cared
 (try booting with the "irqpoll" option)
 [    16.680985] handlers:
 [    16.681004] [<ffffffffc07b5380>] azx_interrupt [snd_hda_codec]
 [    16.681018] Disabling IRQ #17
```

I didn't try booting with irqpoll, because apparently it requires modifying grub, and I don't want to mess with it because I'm a noob. 

I have a "802.11n Wireless LAN Card" by Ralink Technology.

I tried running a series of commands, to not avail.


lspci
 
 
 ```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18) 
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) 
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06) 
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) 
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6) 
00:1f.0 ISA bridge: Intel Corporation H57 Chipset LPC Interface Controller (rev 06) 
00:1f.2 RAID bus controller: Intel Corporation SATA Controller [RAID mode] (rev 06) 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06) 
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 405] (rev a2) 
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1) 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (r
ev 03) 
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller (rev 01) 
04:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe 
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05) 
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05) 
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05) 
ff:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 05) 
ff:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05) 
ff:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05)

```

iwconfig

When the wifi works

```
 lo        no wireless extensions. 

wlp4s0    IEEE 802.11  ESSID:"Bbox-7FD95BF4"   
         Mode:Managed  Frequency:2.437 GHz  Access Point: 00:78:9E:7B:9B:90    
         Bit Rate=57.8 Mb/s   Tx-Power=20 dBm    
         Retry short limit:7   RTS thr:off   Fragment thr:off 
         Power Management:on 
         Link Quality=53/70  Signal level=-57 dBm   
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
         Tx excessive retries:1  Invalid misc:0   Missed beacon:0 

enp2s0    no wireless extensions.

 
```

When it doesn't

```
 lo        no wireless extensions. 

wlp4s0    IEEE 802.11  ESSID:off/any   
         Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
         Retry short limit:7   RTS thr:off   Fragment thr:off 
         Power Management:off 
          
enp2s0    no wireless extensions.
 
```

inxi -Fxz
 
When wifi doesn't work: 

```
System:   Host: Melchizedek Kernel: 4.10.0-42-generic x86_64 (64 bit gcc: 6.3.0)
Desktop: KDE Plasma 5.9.5 (Qt 5.7.1) Distro: Ubuntu 17.04
Machine:  Device: desktop System: Hewlett-Packard product: p6710fr v: xxx0204GRxxxxxxxx0
Mobo: MSI model: 2A9C v: 1.1 BIOS: American Megatrends v: 6.14 date: 11/05/2010
CPU:      Dual core Intel Core i3 550 (-HT-MCP-) cache: 4096 KB
flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12769
clock speeds:max: 3200 MHz 1: 1200 MHz 2: 1200 MHz 3: 1600 MHz 4: 2400 MHz
Graphics: Card: NVIDIA GT218 [GeForce 405] bus-ID: 01:00.0
Display Server: X.Org 1.19.3 drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
Resolution: 1920x1080@60.00hz
GLX Renderer: GeForce 405/PCIe/SSE2 GLX Version: 3.3.0 NVIDIA 340.102 Direct Rendering: Yes
Audio:    Card-1 Intel 5 Series/3400 Series High Definition Audio driver: snd_hda_intel bus-ID: 00:1b.0
Card-2 NVIDIA High Definition Audio Controller driver: snd_hda_intel bus-ID: 01:00.1
Sound: Advanced Linux Sound Architecture v: k4.10.0-42-generic
Network:  Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
driver: r8169 v: 2.3LK-NAPI port: d800 bus-ID: 02:00.0
IF: enp2s0 state: down mac: <filter>
Card-2: Ralink RT3090 Wireless 802.11n 1T/1R PCIe driver: rt2800pci v: 2.3.0 bus-ID: 04:00.0
IF: wlp4s0 state: down mac: <filter>
Drives:   HDD Total Size: 2320.5GB (11.6% used)
ID-1: /dev/sda model: WDC_WD20EARS size: 2000.4GB temp: 0C
ID-2: USB /dev/sdb model: 3200BEV_External size: 320.1GB temp: 0C
Partition:ID-1: / size: 826G used: 252G (33%) fs: ext4 dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:  System Temperatures: cpu: 45.0C mobo: N/A gpu: 0.0:58C
Fan Speeds (in rpm): cpu: N/A
Info:     Processes: 198 Uptime: 6 min Memory: 1579.6/5828.6MB Init: systemd runlevel: 5 Gcc sys: 6.3.0                 
Client: Shell (bash 4.4.71) inxi: 2.3.8


```

When it does work, it's pretty much the same, except I see "IF: wlp4s0 state: up" in "Network"


ifconfig

When the wifi works

```
enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500 
       ether 6c:62:6d:c8:52:8b  txqueuelen 1000  (Ethernet) 
       RX packets 0  bytes 0 (0.0 B) 
       RX errors 0  dropped 0  overruns 0  frame 0 
       TX packets 0  bytes 0 (0.0 B) 
       TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0 

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536 
       inet 127.0.0.1  netmask 255.0.0.0 
       inet6 ::1  prefixlen 128  scopeid 0x10<host> 
       loop  txqueuelen 1000  (Boucle locale) 
       RX packets 1420  bytes 95628 (95.6 KB) 
       RX errors 0  dropped 0  overruns 0  frame 0 
       TX packets 1420  bytes 95628 (95.6 KB) 
       TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0 

wlp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500 
       inet 192.168.1.89  netmask 255.255.255.0  broadcast 192.168.1.255 
       inet6 fe80::7f4:f224:6db3:6bcb  prefixlen 64  scopeid 0x20<link> 
       ether 1c:65:9d:eb:b4:1c  txqueuelen 1000  (Ethernet) 
       RX packets 23  bytes 2638 (2.6 KB) 
       RX errors 0  dropped 0  overruns 0  frame 0 
       TX packets 98  bytes 14055 (14.0 KB) 
       TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```

When it doesn't work

```
enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500 
       ether 6c:62:6d:c8:52:8b  txqueuelen 1000  (Ethernet) 
       RX packets 0  bytes 0 (0.0 B) 
       RX errors 0  dropped 0  overruns 0  frame 0 
       TX packets 0  bytes 0 (0.0 B) 
       TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0 

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536 
       inet 127.0.0.1  netmask 255.0.0.0 
       inet6 ::1  prefixlen 128  scopeid 0x10<host> 
       loop  txqueuelen 1000  (Boucle locale) 
       RX packets 992  bytes 73472 (73.4 KB) 
       RX errors 0  dropped 0  overruns 0  frame 0 
       TX packets 992  bytes 73472 (73.4 KB) 
       TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```

Ismod

When the wifi works

```
Module                  Size  Used by 
ccm                    20480  2 
nvidia_uvm             36864  0 
gpio_ich               16384  0 
snd_hda_codec_hdmi     49152  4 
joydev                 20480  0 
input_leds             16384  0 
nvidia              10563584  92 nvidia_uvm 
snd_hda_codec_realtek    90112  1 
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek 
intel_powerclamp       16384  0 
coretemp               16384  0 
snd_hda_intel          36864  5 
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek 
kvm                   593920  0 
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realte
k 
irqbypass              16384  1 kvm 
snd_hwdep              16384  1 snd_hda_codec 
intel_cstate           20480  0 
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi 
arc4                   16384  2 
snd_rawmidi            32768  1 snd_seq_midi 
rt2800pci              16384  0 
rt2800mmio             16384  1 rt2800pci 
rt2800lib              94208  2 rt2800mmio,rt2800pci 
rt2x00pci              16384  1 rt2800pci 
rt2x00mmio             16384  2 rt2800mmio,rt2800pci 
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi 
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci 
mac80211              782336  3 rt2800lib,rt2x00pci,rt2x00lib 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi 
snd_timer              32768  2 snd_seq,snd_pcm 
drm                   352256  3 nvidia 
cfg80211              602112  2 rt2x00lib,mac80211 
snd                    77824  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,s
nd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm 
eeprom_93cx6           16384  1 rt2800pci 
lpc_ich                24576  0 
soundcore              16384  1 snd 
mei_me                 40960  0 
mei                   102400  1 mei_me 
shpchp                 36864  0 
wmi                    16384  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                49152  3 lp,parport_pc,ppdev 
ip_tables              24576  0 
x_tables               36864  1 ip_tables 
autofs4                40960  2 
uas                    24576  0 
usb_storage            69632  2 uas 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   114688  2 hid_generic,usbhid 
ahci                   36864  3 
firewire_ohci          40960  0 
r8169                  81920  0 
firewire_core          65536  1 firewire_ohci 
libahci                32768  1 ahci 
crc_itu_t              16384  1 firewire_core 
mii                    16384  1 r8169 
fjes                   73728  0


```

When it doesn't

```
Module                  Size  Used by 
snd_hda_codec_hdmi     49152  4 
nvidia_uvm             36864  0 
gpio_ich               16384  0 
nvidia              10563584  84 nvidia_uvm 
snd_hda_codec_realtek    90112  1 
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek 
arc4                   16384  2 
joydev                 20480  0 
rt2800pci              16384  0 
snd_hda_intel          36864  5 
input_leds             16384  0 
rt2800mmio             16384  1 rt2800pci 
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek 
rt2800lib              94208  2 rt2800mmio,rt2800pci 
snd_seq_midi           16384  0 
rt2x00pci              16384  1 rt2800pci 
intel_powerclamp       16384  0 
rt2x00mmio             16384  2 rt2800mmio,rt2800pci 
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci 
snd_seq_midi_event     16384  1 snd_seq_midi 
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realte
k 
snd_rawmidi            32768  1 snd_seq_midi 
snd_hwdep              16384  1 snd_hda_codec 
coretemp               16384  0 
mac80211              782336  3 rt2800lib,rt2x00pci,rt2x00lib 
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi 
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi 
drm                   352256  3 nvidia 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi 
cfg80211              602112  2 rt2x00lib,mac80211 
eeprom_93cx6           16384  1 rt2800pci 
snd_timer              32768  2 snd_seq,snd_pcm 
kvm                   593920  0 
mei_me                 40960  0 
snd                    77824  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,s
nd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm 
mei                   102400  1 mei_me 
lpc_ich                24576  0 
irqbypass              16384  1 kvm 
intel_cstate           20480  0 
shpchp                 36864  0 
soundcore              16384  1 snd 
wmi                    16384  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                49152  3 lp,parport_pc,ppdev 
ip_tables              24576  0 
x_tables               36864  1 ip_tables 
autofs4                40960  2 
uas                    24576  0 
usb_storage            69632  1 uas 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   114688  2 hid_generic,usbhid 
ahci                   36864  1 
firewire_ohci          40960  0 
libahci                32768  1 ahci 
firewire_core          65536  1 firewire_ohci 
r8169                  81920  0 
crc_itu_t              16384  1 firewire_core 
mii                    16384  1 r8169 
fjes                   73728  0


```

sudo lshw -c net; lspci -nnk | grep -iA2 net
 
When the wifi works

```
*-network                  
      description: Ethernet interface 
      product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
      vendor: Realtek Semiconductor Co., Ltd. 
      physical id: 0 
      bus info: pci@0000:02:00.0 
      logical name: enp2s0 
      version: 03 
      serial: 6c:62:6d:c8:52:8b 
      size: 10Mbit/s 
      capacity: 1Gbit/s 
      width: 64 bits 
      clock: 33MHz 
      capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt
-fd 1000bt 1000bt-fd autonegotiation 
      configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic
/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
      resources: irq:25 ioport:d800(size=256) memory:fbdff000-fbdfffff memory:f8ffc000-f8ffffff memory:fbdc0000-fbddffff 
 *-network 
      description: Wireless interface 
      product: RT3090 Wireless 802.11n 1T/1R PCIe 
      vendor: Ralink corp. 
      physical id: 0 
      bus info: pci@0000:04:00.0 
      logical name: wlp4s0 
      version: 00 
      serial: 1c:65:9d:eb:b4:1c 
      width: 32 bits 
      clock: 33MHz 
      capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
      configuration: broadcast=yes driver=rt2800pci driverversion=4.10.0-42-generic firmware=0.40 ip=192.168.1.89 latenc
y=0 link=yes multicast=yes wireless=IEEE 802.11 
      resources: irq:17 memory:fbff0000-fbffffff 
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Contro
ller [10ec:8168] (rev 03) 
       Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:2a9c] 
       Kernel driver in use: r8169 
       Kernel modules: r8169 
--
04:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090] 
       Subsystem: Lite-On Communications Inc RT3090 Wireless 802.11n 1T/1R PCIe [11ad:6632] 
       Kernel driver in use: rt2800pci


```

When it doesn't work , it seems to be the same, except I see « network DISABLED » for the wireless interface and « link=yes » in configuration.



rfkill list all

Whether the wifi works or not

```
 
0: phy0: Wireless LAN
     Soft blocked: no
     Hard blocked: no
 
```


"rfkill unblock wifi" and "rfkill unblock all" don&#8217;t change the results of iwconfig.





"sudo service network-manager restart" restarts the network manager but doesn&#8217;t change the problem.

 "sudo modprobe rt2800pci" didn&#8217;t activate the wifi.

---

### Post by jeremy31 on 2018-01-07
If you are using Win10 without disabling the hybrid shutdown, it could cause many issues.  Are you saying the wifi works when you use windows to restart the computer and not when you use power off?

---

### Post by homme-nuage on 2018-01-07
I'm on Windows 7 (service pack 1).

I shut down Windows/Kubuntu normally. I doesn't matter whether I restart or turn off the computer. But after using Windows, the wifi works on Kubuntu.

---

### Post by jeremy31 on 2018-01-07
In terminal ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Then see if there is any difference

---

### Post by homme-nuage on 2018-01-07
I did it. It didn't make the wifi work. Then I restarted; I didn't see the error "nobody cared", but wifi still wasn't working. I restarted and booted Windows, then restarted and booted Kubuntu, and restarted and booted Kubuntu once again, and the error "nobody cared" was back. I redid the whole process with the same results.

---

### Post by jeremy31 on 2018-01-08
Seems like the only possible solution is to add irqpoll
```
sudo -H kate /etc/default/grub
```

Find the line that is ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Make it be
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll"
```
Save and exit the text editor, then
```
sudo update-grub
```
See if it fixes that irq issue

---

### Post by homme-nuage on 2018-01-08
Thank you for your help.

Now the error "nobody cared" never appears, but the wifi doesn't work any better.

I managed to take a picture of the message that often appears briefly when I shutdown Kubuntu after a wifi failure:

```
Ubuntu 17.04 Melchizedek ttyl

Melchizedek login: [   197.13308]  ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000078]
[   199.144937] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000078]
[   199.144988] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   201.180800] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000078]
[   203.180717] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000078]
[   203.180767] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
```

Also, I always have this message on boot, whether the wifi is going to work or not:

```
[    2.805187] sd 6:0:0:0: [sdb] No Caching mode page found
[    2.805236] sd 6:0:0:0: [sdb] Assuming drive cache: write through
```

Finally, orange dots appear on startup whether the wifi is going to work or not. When I type 'esc', I see (whether wifi is going to work or not):

```
[FAILED] Failed to activate swap /swapfile.
See 'systemctl status swapfile.swap' for details.
[DEPEND] Dependency failed for Swap
```

So I entered 'systemctl status swapfile.swap' in the terminal, and I saw:

```
&#9679; swapfile.swap - /swapfile
   Loaded: loaded (/etc/fstab; generated; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2018-01-08 16:44:21 CET; 6min ago
     What: /swapfile
     Docs: man:fstab(5)
           man:systemd-fstab-generator(8)

janv. 08 16:44:21 Melchizedek systemd[1]: Activating swap /swapfile...
janv. 08 16:44:21 Melchizedek swapon[384]: swapon: /swapfile : read swap header failed
janv. 08 16:44:21 Melchizedek systemd[1]: swapfile.swap: Swap process exited, code=exited status=255
janv. 08 16:44:21 Melchizedek systemd[1]: Failed to activate swap /swapfile.
janv. 08 16:44:21 Melchizedek systemd[1]: swapfile.swap: Unit entered failed state.
```

---


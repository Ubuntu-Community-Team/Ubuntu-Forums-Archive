---
title: "Broadcom Drivers Installed But Not Working"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by PearlStreet on 2008-09-28
I have installed the new broadcom drivers as explained in the sticky at the top of this board.  I still am not seeing any wireless networks showing up in network manager (though there are 20+ in range). Here's the relevant information:

uname -a
```
Linux travis-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

```

lspci -nn
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

dpkg -l | grep linux-restricted
```
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.22-14-generic 2.6.22.4-14.9                            Non-free Linux 2.6.22 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

```

lshw -C network
```
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:19:7e:65:58:9b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

```

lsmod
```
af_packet              23812  2 
ipv6                  267780  8 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ieee80211_crypt_tkip    11648  0 
wl                   1073940  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
pcmcia                 40876  0 
snd_hda_intel         344856  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
sky2                   47620  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
container               5632  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
video                  19856  0 
output                  4736  1 video
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tifm_7xx1               8576  0 
serio_raw               7940  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_core              11012  1 tifm_7xx1
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                40336  0 
battery                14212  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
button                  9232  0 
acer_acpi              18112  0 
led_class               6020  1 acer_acpi
intel_agp              25492  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
wmi_acer                9644  1 acer_acpi
soundcore               8800  1 snd
agpgart                34760  3 drm,intel_agp
pcspkr                  4224  0 
evdev                  13056  7 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
ata_piix               19588  2 
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 

```

This driver is supposed to work with a 4311 and it sounds like other people are having success... I just can't seem to find what's wrong.  Any thoughts?

---

### Post by Ayuthia on 2008-09-28
Can you also post the results of:
```
sudo ifconfig
sudo iwconfig
sudo iwlist scan
```Maybe they will provide some clues.

---

### Post by PearlStreet on 2008-09-29
Okay, let's see what we've got...

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:19:7e:65:58:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1b:24:33:be:6e  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe33:be6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11735 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20089271 (19.1 MB)  TX bytes:1840208 (1.7 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81400 (79.4 KB)  TX bytes:81400 (79.4 KB)

```

iwconfig
```
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist scan
```
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Failed to read scan data : Invalid argument

```

---

### Post by Ayuthia on 2008-09-29
I think we might need to take a look at demsg.  Check and see if there are any error messges associated with the wl driver:
```
dmesg|grep wl
```This might bring more information than just the the wl driver but it will help cut down on some of the information that dmesg produces.

I am not used to seeing the wireless show up before the wired, but that should not be an issue.

EDIT:
Another thing to try is the following:
```
sudo ifconfig eth0 up
sudo iwlist scan
```
It looks like your card is not turned on.  If have a switch to turn it on and off, you might check and see if it is on.  If it is on, you might check the BIOS to see if it is turned off there.  Another option is if you have Windows installed also, you can go in there and see if you can connect there.  That might turn on your card.

---

### Post by superprash2003 on 2008-09-29
hope this helps [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by PearlStreet on 2008-09-29
Thanks for the responses.  Still no luck on this end.  I know the wireless card is powered on b/c it worked previously with ndiswrapper.  I had it set up and working for a few months as described in the article linked above by superprash2003.

Unfortunately, that started running into its own problems, which I was unable to resolve, so I thought I would give this new broadcom driver a shot.  (Basically, with ndiswrapper, the wireless would work after reboot for about 5 minutes and then shut down - something I was unable to find a solution to after working on it for a few weeks)

Ayuthia, running the code described in your edit did not alleviate the problem either, and iwlist scan returned the same result as before.

Here's the result of dmesg|grep wl
```
[   34.579921] wl: module license 'MIXED/Proprietary' taints kernel.
[   34.623794]  [<e05cca04>] dev_wlc_ioctl+0x54/0xa0 [wl]
[   34.623829]  [<e05cd39a>] dev_wlc_intvar_set+0x4a/0x60 [wl]
[   34.623872]  [<e05d138b>] wl_pci_probe+0x41b/0x488 [wl]
[   34.624049]  [<e05cca04>] dev_wlc_ioctl+0x54/0xa0 [wl]
[   34.624077]  [<e05cd39a>] dev_wlc_intvar_set+0x4a/0x60 [wl]
[   34.624119]  [<e05d138b>] wl_pci_probe+0x41b/0x488 [wl]
[   34.624292]  [<e05cca04>] dev_wlc_ioctl+0x54/0xa0 [wl]
[   34.624320]  [<e05cd39a>] dev_wlc_intvar_set+0x4a/0x60 [wl]
[   34.624362]  [<e05d138b>] wl_pci_probe+0x41b/0x488 [wl]
[   34.624540]  [<e05cca04>] dev_wlc_ioctl+0x54/0xa0 [wl]
[   34.624569]  [<e05cd39a>] dev_wlc_intvar_set+0x4a/0x60 [wl]
[   34.624611]  [<e05d138b>] wl_pci_probe+0x41b/0x488 [wl]

```

---

### Post by ccwjones on 2008-10-01
I installed Ubuntu on a Compaq laptop. Initially broadcom wireless worked ok after turning on Hardware drivers.

Not working in that it won't detect wireless network (ACER beside it works fine)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 lshw -C network

 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:9b:7d:f8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:ce:3d:51
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

uname -a

Linux christopher-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

lspci -nn


06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


Any suggestions?

---

### Post by Crafty Kisses on 2008-10-01
First, you may want to install this package:
```
sudo apt-get install ndisgtk
```
Once you have that installed you want to get the .inf file and blacklist the driver, so you want to do the following:
```
'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```
Then you need to configure your iwconfig to your settings, so do the following:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
[B]wireless-essid MYSSID
wireless-key s:mysecretwepkey
[/B]
auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```
After you've done that, download the driver for your card, right [**here**]("www.drivershq.com/Drivers/VistaDevices/ACER-Broadcom-4311-a-b-g-Wireless-Lan-Driver/16024/Drivers.aspx"). Once you have the drivers downloaded, run the following command:
```
sudo ndiswrapper -i drivername.inf
```
Then install the .inf file via ndisgtk, and let's see if that springs your card to life.

---

### Post by ccwjones on 2008-10-04
I removed the Broadcom drivers from  System>>Administration>>Hardware drivers.

Then by creating a blacklist file which seemed to clean things up.

I then deleted the blacklist file and then System>>Administration>>Hardware drivers and reinstalled the drivers just by clicking on the Enabled button.

It now works....

sudo gedit /etc/modprobe.d/blacklist-bcm43

And paste into file

blacklist b43
blacklist ssb
blacklist b43legacy

---


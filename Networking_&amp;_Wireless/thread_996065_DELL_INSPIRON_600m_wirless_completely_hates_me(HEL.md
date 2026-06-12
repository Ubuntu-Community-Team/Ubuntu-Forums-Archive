---
title: "DELL INSPIRON 600m wirless completely hates me(HELP!)"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by ReSoL603 on 2008-11-28
Into: So my name is Chris, I just installed UBUNTU on my laptop and have searched/tried everything. I can't figure out what else to do. Please help. Thank you. I am also on aim, screen name: RESOL603


1 ) Machine Brand and Model (PC/Laptop):
```
DELL INSPIRON 600M laptop
```

2 ) Wireless Brand, Model and Wireless Chipset:
```
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```


3 ) check interface:
```
wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 4E:2A:2A:B5:92:1C   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



4 ) Check for modules:
```
 lsmod 
Module                  Size  Used by
ipv6                  263972  8 
ipt_MASQUERADE         10752  0 
xt_state               10112  0 
ipt_REJECT             11136  0 
xt_tcpudp              11008  0 
nf_nat_h323            14464  0 
nf_conntrack_h323      56904  1 nf_nat_h323
nf_nat_pptp            11136  0 
nf_conntrack_pptp      14084  1 nf_nat_pptp
nf_conntrack_proto_gre    13056  1 nf_conntrack_pptp
nf_nat_proto_gre       10372  1 nf_nat_pptp
nf_nat_tftp             9600  0 
nf_conntrack_tftp      12308  1 nf_nat_tftp
nf_nat_sip             14976  0 
nf_conntrack_sip       26260  1 nf_nat_sip
nf_nat_irc             10240  0 
nf_conntrack_irc       13348  1 nf_nat_irc
nf_nat_ftp             10880  0 
nf_conntrack_ftp       15652  1 nf_nat_ftp
iptable_nat            13448  0 
nf_nat                 25368  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      21900  3 iptable_nat,nf_nat
nf_conntrack           72032  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
af_packet              25728  8 
rfkill_input           12672  0 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
cpufreq_ondemand       14988  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      11396  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
pci_slot               12552  0 
iptable_filter         10752  0 
ip_tables              19600  2 iptable_nat,iptable_filter
x_tables               22916  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
lp                     17156  0 
joydev                 18368  0 
pcmcia                 43052  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
dcdbas                 15008  0 
b43                   131356  0 
rfkill                 17176  3 rfkill_input,b43
mac80211              216820  1 b43
cfg80211               32392  1 mac80211
evdev                  17696  11 
led_class              12164  1 b43
input_polldev          11912  1 b43
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
psmouse                45200  0 
serio_raw              13444  0 
yenta_socket           31756  2 
rsrc_nonstatic         19072  1 yenta_socket
snd_seq_dummy          10884  0 
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  25104  0 
output                 11008  1 video
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                 10624  0 
button                 14224  0 
battery                18436  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                     12292  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  1 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  2 drm,intel_agp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
loop                   23180  2 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  2 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
b44                    35984  0 
ata_piix               24580  1 
libata                177312  3 pata_acpi,ata_generic,ata_piix
ssb                    40580  2 b43,b44
mii                    13440  1 b44
uhci_hcd               30736  0 
ehci_hcd               43276  0 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
usbcore               148848  3 uhci_hcd,ehci_hcd
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 

```



5 ) Kernel boot messages
Code:

```
[  110.286424] wlan0: Trigger new scan to find an IBSS to join
[  110.952052] b43-phy0: Radio hardware status changed to DISABLED
[  113.060048] wlan0: Trigger new scan to find an IBSS to join
[  115.836044] wlan0: Trigger new scan to find an IBSS to join
[  118.612043] wlan0: Trigger new scan to find an IBSS to join
[  119.388088] wlan0: Creating new IBSS network, BSSID 9a:f8:bb:11:08:0a
[  120.495647] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[  120.497244] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[  120.497254] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[  120.497257] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[  121.096920] wlan0: disassociating by local choice (reason=3)
[  161.271707] wlan0: Trigger new scan to find an IBSS to join
[  162.360169] ppdev0: registered pardevice
[  162.408048] ppdev0: unregistered pardevice
[  163.112235] ppdev0: registered pardevice
[  163.190795] ppdev0: unregistered pardevice
[  164.048049] wlan0: Trigger new scan to find an IBSS to join
[  164.975151] ppdev0: registered pardevice
[  165.032150] ppdev0: unregistered pardevice
[  166.824149] wlan0: Trigger new scan to find an IBSS to join
[  169.608051] wlan0: Trigger new scan to find an IBSS to join
[  170.384097] wlan0: Creating new IBSS network, BSSID ca:33:4b:44:3b:72
[  171.524748] wlan0: disassociating by local choice (reason=3)
[  231.156779] wlan0: Selected IBSS BSSID ca:33:4b:44:3b:72 based on configured SSID
[  232.315862] wlan0: disassociating by local choice (reason=3)
[  350.000197] b44: eth0: Link is up at 100 Mbps, full duplex.
[  350.000206] b44: eth0: Flow control is off for TX and off for RX.
[  403.000108] b44: eth0: Link is down.
[  434.000183] b44: eth0: Link is up at 100 Mbps, full duplex.
[  434.000196] b44: eth0: Flow control is off for TX and off for RX.
[  435.000103] b44: eth0: Link is down.
[  438.000180] b44: eth0: Link is up at 100 Mbps, full duplex.
[  438.000193] b44: eth0: Flow control is off for TX and off for RX.
[  464.379020] NET: Registered protocol family 10
[  464.380747] lo: Disabled Privacy Extensions
[  474.428028] eth0: no IPv6 routers present
[  475.096028] wlan0: no IPv6 routers present
[ 1987.604214] input: b43-phy0 as /devices/virtual/input/input11
[ 1987.772044] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1987.884532] Registered led device: b43-phy0::tx
[ 1987.886573] Registered led device: b43-phy0::rx
[ 1987.887497] Registered led device: b43-phy0::radio
[ 1988.612059] b43-phy0: Radio hardware status changed to DISABLED
[ 1991.680220] b43-phy0: Radio turned on by software
[ 1991.680229] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 1998.880214] wlan0: no IPv6 routers present
[ 2045.868448] wlan0: Trigger new scan to find an IBSS to join
[ 2048.644045] wlan0: Trigger new scan to find an IBSS to join
[ 2051.420121] wlan0: Trigger new scan to find an IBSS to join
[ 2054.196091] wlan0: Trigger new scan to find an IBSS to join
[ 2054.976287] wlan0: Creating new IBSS network, BSSID 4e:2a:2a:b5:92:1c
[ 2054.977091] wlan0: disassociating by local choice (reason=3)
[ 2084.976080] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2142.412046] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2202.416043] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2262.424043] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2322.424051] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2382.428049] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2442.432059] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2502.436052] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2562.440043] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2622.444053] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2682.444043] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2742.452054] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2802.476053] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2862.464048] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2922.468056] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2982.472047] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3042.476062] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3102.480048] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3162.488053] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3222.488048] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3282.500048] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3342.496054] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3402.500045] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3462.504052] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3522.508047] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
```


6 ) Network configuration
Code:

```
 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:fa:a8:4c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.101 latency=32 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a4:23:3f:a0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 02:fb:6f:a0:97:e7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

7 ) Scan for networks:
Code:

```
 scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```




8 ) Ubuntu Version:
```
 lsb_release -d
Description:	Ubuntu 8.10

```

9 ) Kernel/architecture (including 32 vs. 64 bit):
```
uname -mr
2.6.27-9-generic i686

```

10 ) Restarting the network:
```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                         Ignoring unknown interface eth0=eth0.

```

---

### Post by ReSoL603 on 2008-11-28
P.S. I have no idea what I am doing.

---

### Post by ReSoL603 on 2008-11-28
Okay I after all the stuff I tried, I hit "FN+F2" and now it works, so something I did fixed it. Thank you.

---

### Post by Ayuthia on 2008-11-28
> [ 1991.680229] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
By any chance, is there a switch for your wireless card?  If so, is it on?

EDIT: Oops.  Too slow.

---

### Post by andrew.mckevitt on 2008-11-28
Fn+F2 on dells switches the wireless on and off (including bluetooth)

---


---
title: "Wireless Adapter is not receiving packages"
date: 2017-04-26
forum: Networking &amp; Wireless
---

### Post by t.leary on 2017-04-26
Hey,

I'm trying to set up a hot-spot on my Laptop. This worked totally fine using Ubuntu 16.10,
however I'm facing a problem with Ubuntu 17.04 which I cannot resolve on my own.

Essentially I used this guide [https://askubuntu.com/questions/180733/how-to-setup-an-access-point-mode-wi-fi-hotspot/439530#439530](https://askubuntu.com/questions/180733/how-to-setup-an-access-point-mode-wi-fi-hotspot/439530#439530) to set up the hot-spot.[URL="https://askubuntu.com/questions/180733/how-to-setup-an-access-point-mode-wi-fi-hotspot/439530#439530"]
[/URL]The Wi-Fi Network is also shown in the Network Indicator Menu and can be found by other devices, however no other device (e.g. smartphone) can connect to the network
and it seems like the Wi-Fi adapter is not receiving any packages.

Here are my configurations:

```

$uname -a
Linux wifinetworkpc 4.10.0-20-generic #22-Ubuntu SMP Thu Apr 20 09:22:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```



ifconfig when hot-spot is "running":
```
$ifconfig
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.28.147  netmask 255.255.255.0  broadcast 192.168.28.255
        inet6 fe80::c1cd:d57d:57f2:897  prefixlen 64  scopeid 0x20<link>
        ether AA:AA:AA:AA:AA:AA  txqueuelen 1000  (Ethernet)
        RX packets 56390  bytes 35653746 (35.6 MB)
        RX errors 206  dropped 0  overruns 0  frame 64
        TX packets 49337  bytes 5921572 (5.9 MB)
        TX errors 2  dropped 0 overruns 0  carrier 3  collisions 2975

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2017780  bytes 368269094 (368.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2017780  bytes 368269094 (368.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.42.0.1  netmask 255.255.255.0  broadcast 10.42.0.255
        inet6 fe80::227c:8fff:fe4c:7108  prefixlen 64  scopeid 0x20<link>
        ether AA:AA:AA:AA:AA:AA  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1948  bytes 271499 (271.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

ifconfig when hot-spot is NOT "running":
```
$ifconfig
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.28.147  netmask 255.255.255.0  broadcast 192.168.28.255
        inet6 fe80::c1cd:d57d:57f2:897  prefixlen 64  scopeid 0x20<link>
        ether AA:AA:AA:AA:AA:AA  txqueuelen 1000  (Ethernet)
        RX packets 60579  bytes 37174724 (37.1 MB)
        RX errors 224  dropped 0  overruns 0  frame 67
        TX packets 53215  bytes 6671388 (6.6 MB)
        TX errors 2  dropped 0 overruns 0  carrier 3  collisions 3208

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2053977  bytes 374820722 (374.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2053977  bytes 374820722 (374.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether AA:AA:AA:AA:AA:AA  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2049  bytes 285673 (285.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

As you can see, neither way my Wi-Fi adapter receives packets.

More info about my adapter:

```

$lspci -vv -s 02:00.0
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
    Subsystem: Quanta Microsystems, Inc RTL8191SEvB Wireless LAN Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 3000 [size=256]
    Region 1: Memory at d7800000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <512ns, L1 <64us
            ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [140 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
            Status:    NegoPending- InProgress-
    Capabilities: [160 v1] Device Serial Number AA-AA-AA-AA-AA-AA-AA-AA
    Kernel driver in use: rtl8192se
    Kernel modules: rtl8192se

```

```
$iwconfig
iwconfig
enp3s0    no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

```

System network configuration

```
$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

```
$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.

nameserver 127.0.0.1

```

```
$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    wifinetworkpc

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```


NetworkManager configuration:

```

$cat /etc/NetworkManager/system-connections/ Wi-Fi\ connection\ 1
[connection]
id=Wi-Fi connection 1
uuid=2b15b006-7168-4ba1-a5bd-751fa52290db
type=wifi
interface-name=wlp2s0
permissions=
secondaries=
timestamp=1493236722

[wifi]
mac-address=AA:AA:AA:AA:AA:AA
mac-address-blacklist=
mac-address-randomization=0
mode=ap
seen-bssids=AA:AA:AA:AA:AA:AA;
ssid=mobile-wifi

[wifi-security]
group=
key-mgmt=wpa-psk
pairwise=
proto=
psk=somepass

[ipv4]
dns-search=
method=shared

[ipv6]
addr-gen-mode=stable-privacy
dns-search=
ip6-privacy=0
method=ignore

```

```
$ cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

```
$ cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

WLAN state and drivers:

```
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         16384  0
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
xt_conntrack           16384  0
ipt_REJECT             16384  0
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  0
iptable_filter         16384  0
nf_nat_h323            20480  0
nf_conntrack_h323      73728  1 nf_nat_h323
nf_nat_pptp            16384  0
nf_nat_proto_gre       16384  1 nf_nat_pptp
nf_conntrack_pptp      16384  1 nf_nat_pptp
nf_conntrack_proto_gre    16384  1 nf_conntrack_pptp
nf_nat_tftp            16384  0
nf_conntrack_tftp      16384  1 nf_nat_tftp
nf_nat_sip             20480  0
nf_conntrack_sip       28672  1 nf_nat_sip
nf_nat_irc             16384  0
nf_conntrack_irc       16384  1 nf_nat_irc
nf_nat_ftp             16384  0
nf_conntrack_ftp       20480  1 nf_nat_ftp
iptable_nat            16384  0
nf_conntrack_ipv4      16384  1
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  9 nf_nat_pptp,nf_nat_proto_gre,nf_nat_h323,nf_nat_sip,nf_nat_irc,nf_nat_ftp,nf_nat_masquerade_ipv4,nf_nat_ipv4,nf_nat_tftp
nf_conntrack          131072  19 nf_nat_pptp,nf_conntrack_sip,nf_conntrack_irc,nf_nat_h323,nf_conntrack_ftp,nf_nat_sip,nf_conntrack_ipv4,nf_conntrack_tftp,ipt_MASQUERADE,nf_nat_irc,nf_conntrack_pptp,nf_nat_ftp,nf_conntrack_proto_gre,nf_nat_masquerade_ipv4,nf_conntrack_h323,xt_conntrack,nf_nat_ipv4,nf_nat_tftp,nf_nat
libcrc32c              16384  1 nf_nat
bbswitch               16384  0
nvidia_uvm            647168  0
mxm_wmi                16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             200704  0
snd_hda_codec_hdmi     49152  1
kvm                   593920  1 kvm_intel
snd_hda_codec_realtek    90112  1
irqbypass              16384  1 kvm
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
intel_cstate           20480  0
snd_hda_intel          36864  3
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
input_leds             16384  0
snd_rawmidi            32768  1 snd_seq_midi
serio_raw              16384  0
arc4                   16384  2
intel_ips              20480  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
rtl8192se              65536  0
rtl_pci                28672  1 rtl8192se
rtlwifi                73728  2 rtl8192se,rtl_pci
mac80211              782336  3 rtl8192se,rtl_pci,rtlwifi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
cfg80211              602112  2 mac80211,rtlwifi
snd                    77824  17 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
lpc_ich                24576  0
mei_me                 40960  0
soundcore              16384  1 snd
mei                   102400  1 mei_me
shpchp                 36864  0
wmi                    16384  1 mxm_wmi
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  2 iptable_filter,iptable_nat
x_tables               36864  6 ipt_REJECT,ip_tables,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_conntrack
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
hid                   114688  2 hid_generic,usbhid
nvidia_drm             49152  2
nvidia_modeset        790528  6 nvidia_drm
i915                 1449984  8
nvidia              12136448  97 nvidia_modeset,nvidia_uvm
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  2 i915,nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
psmouse               139264  0
fb_sys_fops            16384  1 drm_kms_helper
atl1c                  49152  0
drm                   352256  6 i915,nvidia_drm,drm_kms_helper
ahci                   36864  2
libahci                32768  1 ahci
fjes                   73728  0
video                  40960  1 i915

```

Other might relevant information:
I upgraded the machine from 16.10 to 17.04, so it's not an out-of-the box 17.04. The hotspot worked just fine in 16.10 as it does in win7.
I installed hostapd and dnsmasq in hopes it would fix it. It did not.
Also I can see other Wi-Fi networks (which should not be possible, if the Wi-Fi adapter isn't receiving any packages, right?).

If I forgot to post something relevant, let me know!



Help would be greatly appreciated!
t.leary

---

### Post by chili555 on 2017-04-27
I flunked hotspot in the good old days at Torvalds U., so I hope you don't ask me too many questions. I probably don't have the answer.> wlp2s0    IEEE 802.11  ESSID:off/any  
          [COLOR="#FF0000"]Mode:Managed [/COLOR] Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          That suggests that the setting in Network Manager is still Client and not Hotspot. Please check.

Does the hardware and driver think it is capable of AP mode?```
iw list
```You should see, approximately:> Supported interface modes:
		 * IBSS
		 * managed
		 *[COLOR="#FF0000"] AP[/COLOR]
		 * AP/VLAN
		 * monitor
		 * P2P-client
		 * P2P-GO
		 * P2P-device
That's it. I'm fresh out of talent.

---


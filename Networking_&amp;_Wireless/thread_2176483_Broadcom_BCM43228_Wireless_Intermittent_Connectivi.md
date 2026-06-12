---
title: "Broadcom BCM43228 Wireless Intermittent Connectivity Issues"
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by Kirk Schnable on 2013-09-24
Good afternoon,

We're troubleshooting intermittent WiFi connectivity problems.  We have over 500 computers running Xubuntu 12.04 with Broadcom wireless cards, and we're seeing about 10-20 come down per hour with connectivity issues.

Some of our issues seem to be resolved by restarting Network Manager.  Others, I've found a combination of stopping network manager, scanning for APs, and restarting network manager fixes it, and still other times I've had to recompile the drivers.

Some of the fixes I've seen so far, depending on severity of the issue:

```
service network-manager restart
```

```
service network-manager stop
ifconfig eth1 up
iwlist scan
service network-manager start
```

```
service network-manager stop
dpkg-reconfigure bcmwl-kernel-source
reboot
```

I've taken aside one netbook which should have similar hardware and software versions to the rest.  Here's some information I've selected to post.  Please let me know if there's other information which would be useful to you.

```
0c:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
    Subsystem: Dell Device 0014
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at f6cfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=2 PME-
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [d0] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM unknown, Latency L0 <4us, L1 <64us
            ClockPM+ Surprise- LLActRep+ BwNot-
        LnkCtl:    ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [13c v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
    Capabilities: [160 v1] Device Serial Number 00-00-84-ff-ff-32-1c-3e
    Capabilities: [16c v1] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl
```

```
# uname -r
3.2.0-53-generic
```

```
# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise
```

```
# dpkg --list | grep bcmwl
ii  bcmwl-kernel-source                           6.20.155.1+bdcom-0ubuntu0.0.2           Broadcom 802.11 Linux STA wireless driver source
```

```
# lsmod
Module                  Size  Used by
nf_conntrack_ipv4      19084  1 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_state               12514  1 
nf_conntrack           73847  2 nf_conntrack_ipv4,xt_state
xt_tcpudp              12531  2 
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               22011  4 xt_state,xt_tcpudp,iptable_filter,ip_tables
promethean             47575  0 
dell_wmi               12601  0 
joydev                 17393  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  4 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
dell_laptop            17767  0 
snd_rawmidi            25424  1 snd_seq_midi
dcdbas                 14098  1 dell_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
lib80211_crypt_tkip    17240  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
wl                   2906597  0 
videodev               86588  1 uvcvideo
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
cfg80211              178877  1 wl
snd                    62218  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rts_pstor             353252  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i915                  428021  2 
drm_kms_helper         45466  1 i915
mac_hid                13077  0 
drm                   197641  3 i915,drm_kms_helper
wmi                    18744  1 dell_wmi
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158447  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
psmouse                96744  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
```

Our WiFi cards are BCM943224HMS cards.
[[IMG]http://binaryimpulse.com/wp-content/uploads/2013/09/wifi-broadcom-card-800x597.jpeg[/IMG]]("http://binaryimpulse.com/wp-content/uploads/2013/09/wifi-broadcom-card.jpeg")

We've seen a variety of different errors being spit out on TTY1, such as:
**ERROR @wl_cfg80211_get_tx_power : error (-1)**
**ERROR @wl_dev_intvar_get : error (-1)**
[[IMG]http://binaryimpulse.com/wp-content/uploads/2013/09/wifi-broadcom-errors-1-800x450.jpg[/IMG]]("http://binaryimpulse.com/wp-content/uploads/2013/09/wifi-broadcom-errors-1.jpg")

**ERROR @wl_cfg80211_get_station : Wrong Mac address**
[[IMG]http://binaryimpulse.com/wp-content/uploads/2013/09/wifi-broadcom-errors-2-800x597.jpeg[/IMG]]("http://binaryimpulse.com/wp-content/uploads/2013/09/wifi-broadcom-errors-2.jpeg")


Does anybody have any experience dealing with these issues with the Broadcom cards\drivers, who might have some advice for us?  Any help or ideas would be greatly appreciated.

Thanks!
Kirk

---

### Post by praseodym on 2013-09-24
Hi,

did you install/uninstall the following:
```

sudo apt-get remove --purge linux-backports-modules-cw*
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
```
Reboot.

I strongly recommend using pure WPA2-AES(CCMP) encryption instead of WPA or mixed WPA/WPA2 (TKIP):
> 
```
lib80211_crypt_[COLOR="#FF0000"]tkip[/COLOR]    17240  0 
```

---

### Post by Kirk Schnable on 2013-09-25
> **praseodym said:**
> Hi,

did you install/uninstall the following:
```

sudo apt-get remove --purge linux-backports-modules-cw*
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
```
Reboot.

The linux-backports-modules packages do not appear to be installed on my test machine.
```
Reading package lists...
Building dependency tree...
Reading state information...
Package linux-backports-modules-cw-3.3-3.2.0-23-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-23-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-24-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-24-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-25-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-25-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-26-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-26-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-27-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-27-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-29-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-29-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-30-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-30-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-31-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-31-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-32-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-32-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-33-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-33-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-34-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-34-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-35-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-35-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-35-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-36-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-36-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-36-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-37-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-37-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-37-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-38-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-38-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-38-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-39-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-39-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-39-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-40-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-40-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-40-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-41-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-41-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-41-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-43-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-43-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-43-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-44-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-44-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-44-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-45-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-45-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-45-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-48-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-48-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-48-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-49-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-49-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-49-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-51-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-51-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-51-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-52-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-52-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-52-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-53-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-53-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-53-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-precise-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-precise-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-29-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-29-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-30-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-30-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-31-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-31-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-32-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-32-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-33-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-33-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-34-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-34-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-35-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-35-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-35-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-36-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-36-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-36-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-37-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-37-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-37-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-38-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-38-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-38-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-39-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-39-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-39-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-40-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-40-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-40-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-41-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-41-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-41-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-43-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-43-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-43-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-44-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-44-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-44-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-45-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-45-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-45-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-48-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-48-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-48-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-49-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-49-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-49-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-51-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-51-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-51-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-52-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-52-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-52-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-53-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-53-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-53-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-precise-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-precise-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-33-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-33-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-34-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-34-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-35-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-35-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-35-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-36-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-36-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-36-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-37-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-37-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-37-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-38-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-38-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-38-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-39-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-39-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-39-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-40-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-40-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-40-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-41-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-41-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-41-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-43-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-43-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-43-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-44-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-44-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-44-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-45-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-45-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-45-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-48-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-48-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-48-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-49-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-49-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-49-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-51-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-51-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-51-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-52-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-52-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-52-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-53-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-53-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-53-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-precise-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-precise-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-33-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-33-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-34-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-34-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-35-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-35-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-35-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-36-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-36-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-36-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-37-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-37-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-37-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-38-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-38-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-38-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-39-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-39-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-39-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-40-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-40-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-40-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-41-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-41-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-41-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-43-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-43-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-43-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-44-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-44-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-44-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-45-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-45-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-45-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-48-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-48-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-48-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-49-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-49-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-49-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-51-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-51-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-51-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-52-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-52-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-52-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-53-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-53-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-53-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-precise-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-precise-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-41-generic is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-41-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-41-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-43-generic is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-43-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-43-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-44-generic is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-44-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-44-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-45-generic is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-45-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-45-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-48-generic is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-48-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-48-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-49-generic is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-49-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-49-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-51-generic is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-51-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-51-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-52-generic is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-52-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-52-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-53-generic is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-53-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.7-3.2.0-53-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.7-precise-generic is not installed, so not removed
Package linux-backports-modules-cw-3.7-precise-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-41-generic is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-41-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-41-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-43-generic is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-43-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-43-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-44-generic is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-44-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-44-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-45-generic is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-45-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-45-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-48-generic is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-48-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-48-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-49-generic is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-49-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-49-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-51-generic is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-51-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-51-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-52-generic is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-52-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-52-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-53-generic is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-53-generic-pae is not installed, so not removed
Package linux-backports-modules-cw-3.8-3.2.0-53-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.8-precise-generic is not installed, so not removed
Package linux-backports-modules-cw-3.8-precise-generic-pae is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 189 not upgraded.
```

It looks like I may not have installed the Linux Headers on the test machine.  Would that make a difference with the Broadcom drivers?

```
# apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-generic linux-headers-3.2.0-53 linux-headers-3.2.0-53-generic
  linux-image-3.2.0-53-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.2.0-53 linux-headers-3.2.0-53-generic
  linux-image-3.2.0-53-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 3 newly installed, 3 reinstalled, 0 to remove and 186 not upgraded.
Need to get 12.8 MB/51.8 MB of archives.
After this operation, 181 MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

> I strongly recommend using pure WPA2-AES(CCMP) encryption instead of WPA or mixed WPA/WPA2 (TKIP):
Noted, however, the SSID which the Dell netbooks connect to has no encryption at all.  It is secured by a Cisco webauth portal, and there is no encryption key for that wireless network whatsoever.  I'm not sure why we're seeing a tkip module loaded if it shouldn't be, as it should not be in use.

Thanks,
Kirk

---

### Post by Kirk Schnable on 2013-09-25
daftykins on Freenode #ubuntu channel suggested I try some different drivers on a test machine.
Following [this guide]("http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers"), I uninstalled the** bcmwl-kernel-source** driver on a single machine, and installed** firmware-b43-installer** and **b43-fwcutter**.

[quote="http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers"]open the 'Synaptic Package Manager' and search for bcm
uninstall the bcm-kernel-source package[/quote]
```
# apt-get remove bcmwl-kernel-source --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-45 linux-headers-3.2.0-45-generic dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,668 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 364530 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-53-generic
#
```

[quote="http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers"]make sure that the firmware-b43-installer and the b43-fwcutter packages are installed[/quote]
```
# apt-get install firmware-b43-installer b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-45 linux-headers-3.2.0-45-generic dkms
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.4 kB of archives.
After this operation, 111 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main b43-fwcutter i386 1:015-9 [18.9 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/multiverse firmware-b43-installer all 1:015-9 [3,524 B]
Fetched 22.4 kB in 0s (96.3 kB/s)            
Selecting previously unselected package b43-fwcutter.
(Reading database ... 364461 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-9_i386.deb) ...
Selecting previously unselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a015-9_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:015-9) ...
Setting up firmware-b43-installer (1:015-9) ...
No chroot environment found. Starting normal installation
This card work with newer 5.10.56.27.3 firmware. Trying to install it.
--2013-09-25 09:48:36--  http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
Resolving mirror2.openwrt.org (mirror2.openwrt.org)... 46.4.11.11
Connecting to mirror2.openwrt.org (mirror2.openwrt.org)|46.4.11.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1596823 (1.5M) [application/x-bzip2]
Saving to: `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2'

100%[======================================>] 1,596,823    261K/s   in 6.6s    

2013-09-25 09:48:43 (237 KB/s) - `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2' saved [1596823/1596823]

broadcom-wl-5.10.56.27.3/driver/
broadcom-wl-5.10.56.27.3/driver/Makefile
broadcom-wl-5.10.56.27.3/driver/aiutils.c
broadcom-wl-5.10.56.27.3/driver/bcmsrom.c
broadcom-wl-5.10.56.27.3/driver/bcmutils.c
broadcom-wl-5.10.56.27.3/driver/hnddma.c
broadcom-wl-5.10.56.27.3/driver/hndpmu.c
broadcom-wl-5.10.56.27.3/driver/include/
broadcom-wl-5.10.56.27.3/driver/include/UdpLib.h
broadcom-wl-5.10.56.27.3/driver/include/aidmp.h
broadcom-wl-5.10.56.27.3/driver/include/arminc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcdc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aes.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aeskeywrap.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bcmccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bn.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/ccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/des.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/dh.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/hmac_sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md5.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/passhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/prf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rc4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rijndael-alg-fst.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha1.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/tkhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdefs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdevs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmendian.h
broadcom-wl-5.10.56.27.3/driver/include/bcmnvram.h
broadcom-wl-5.10.56.27.3/driver/include/bcmotp.h
broadcom-wl-5.10.56.27.3/driver/include/bcmparams.h
broadcom-wl-5.10.56.27.3/driver/include/bcmperf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmrobo.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_fmt.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_tbl.h
broadcom-wl-5.10.56.27.3/driver/include/bcmstdlib.h
broadcom-wl-5.10.56.27.3/driver/include/bcmutils.h
broadcom-wl-5.10.56.27.3/driver/include/bcmwifi.h
broadcom-wl-5.10.56.27.3/driver/include/bitfuncs.h
broadcom-wl-5.10.56.27.3/driver/include/dmemc_core.h
broadcom-wl-5.10.56.27.3/driver/include/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/igs/
broadcom-wl-5.10.56.27.3/driver/include/epivers.h
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.in
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.prev
broadcom-wl-5.10.56.27.3/driver/include/etioctl.h
broadcom-wl-5.10.56.27.3/driver/include/flash.h
broadcom-wl-5.10.56.27.3/driver/include/flashutl.h
broadcom-wl-5.10.56.27.3/driver/include/hndarm.h
broadcom-wl-5.10.56.27.3/driver/include/hndchipc.h
broadcom-wl-5.10.56.27.3/driver/include/hndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/hnddma.h
broadcom-wl-5.10.56.27.3/driver/include/hndgige.h
broadcom-wl-5.10.56.27.3/driver/include/hndjtagdefs.h
broadcom-wl-5.10.56.27.3/driver/include/hndmips.h
broadcom-wl-5.10.56.27.3/driver/include/hndpci.h
broadcom-wl-5.10.56.27.3/driver/include/hndpmu.h
broadcom-wl-5.10.56.27.3/driver/include/hndsoc.h
broadcom-wl-5.10.56.27.3/driver/include/linux_gpio.h
broadcom-wl-5.10.56.27.3/driver/include/linux_osl.h
broadcom-wl-5.10.56.27.3/driver/include/linuxver.h
broadcom-wl-5.10.56.27.3/driver/include/min_osl.h
broadcom-wl-5.10.56.27.3/driver/include/mips33_core.h
broadcom-wl-5.10.56.27.3/driver/include/mips74k_core.h
broadcom-wl-5.10.56.27.3/driver/include/mipsinc.h
broadcom-wl-5.10.56.27.3/driver/include/ndiserrmap.h
broadcom-wl-5.10.56.27.3/driver/include/nicpci.h
broadcom-wl-5.10.56.27.3/driver/include/osl.h
broadcom-wl-5.10.56.27.3/driver/include/pci_core.h
broadcom-wl-5.10.56.27.3/driver/include/pcicfg.h
broadcom-wl-5.10.56.27.3/driver/include/pcie_core.h
broadcom-wl-5.10.56.27.3/driver/include/proto/
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11e.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.1d.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmeth.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmevent.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmip.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmtcp.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eap.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eapol.h
broadcom-wl-5.10.56.27.3/driver/include/proto/ethernet.h
broadcom-wl-5.10.56.27.3/driver/include/proto/vlan.h
broadcom-wl-5.10.56.27.3/driver/include/proto/wpa.h
broadcom-wl-5.10.56.27.3/driver/include/rts/
broadcom-wl-5.10.56.27.3/driver/include/rts/crc.h
broadcom-wl-5.10.56.27.3/driver/include/sbchipc.h
broadcom-wl-5.10.56.27.3/driver/include/sbconfig.h
broadcom-wl-5.10.56.27.3/driver/include/sbgige.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndarm.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/sbhnddma.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndpio.h
broadcom-wl-5.10.56.27.3/driver/include/sbmemc.h
broadcom-wl-5.10.56.27.3/driver/include/sbpcmcia.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdio.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdpcmdev.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsocram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsprom.h
broadcom-wl-5.10.56.27.3/driver/include/sflash.h
broadcom-wl-5.10.56.27.3/driver/include/siutils.h
broadcom-wl-5.10.56.27.3/driver/include/trxhdr.h
broadcom-wl-5.10.56.27.3/driver/include/typedefs.h
broadcom-wl-5.10.56.27.3/driver/include/wlc_ethereal.h
broadcom-wl-5.10.56.27.3/driver/include/wlioctl.h
broadcom-wl-5.10.56.27.3/driver/include/wllmacctl.h
broadcom-wl-5.10.56.27.3/driver/linux_osl.c
broadcom-wl-5.10.56.27.3/driver/nicpci.c
broadcom-wl-5.10.56.27.3/driver/nvram_stub.c
broadcom-wl-5.10.56.27.3/driver/sbutils.c
broadcom-wl-5.10.56.27.3/driver/siutils.c
broadcom-wl-5.10.56.27.3/driver/siutils_priv.h
broadcom-wl-5.10.56.27.3/driver/wl_apsta/
broadcom-wl-5.10.56.27.3/driver/wl_apsta/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_dbg.h
broadcom-wl-5.10.56.27.3/driver/wl_export.h
broadcom-wl-5.10.56.27.3/driver/wl_iw.c
broadcom-wl-5.10.56.27.3/driver/wl_iw.h
broadcom-wl-5.10.56.27.3/driver/wl_linux.c
broadcom-wl-5.10.56.27.3/driver/wl_linux.h
broadcom-wl-5.10.56.27.3/driver/wlc_key.h
broadcom-wl-5.10.56.27.3/driver/wlc_pub.h
broadcom-wl-5.10.56.27.3/nas_exe.o
broadcom-wl-5.10.56.27.3/shared/
broadcom-wl-5.10.56.27.3/shared/Makefile
broadcom-wl-5.10.56.27.3/shared/UdpLib.c
broadcom-wl-5.10.56.27.3/shared/bcmcvar.h
broadcom-wl-5.10.56.27.3/shared/bcmtimer.h
broadcom-wl-5.10.56.27.3/shared/ctype.c
broadcom-wl-5.10.56.27.3/shared/linux_timer.c
broadcom-wl-5.10.56.27.3/shared/netconf.h
broadcom-wl-5.10.56.27.3/shared/opencrypto.h
broadcom-wl-5.10.56.27.3/shared/rte_timers.c
broadcom-wl-5.10.56.27.3/shared/shutils.c
broadcom-wl-5.10.56.27.3/shared/shutils.h
broadcom-wl-5.10.56.27.3/shared/wl.c
broadcom-wl-5.10.56.27.3/shared/wl_linux.c
broadcom-wl-5.10.56.27.3/shared/wlutils.h
broadcom-wl-5.10.56.27.3/wl_exe.o
This file is recognised as:
  filename   :  wl_prebuilt.o
  version    :  508.1084
  MD5        :  490d4e149ecc45eb1a91f06aa75be071
Extracting b43/ucode19.fw
Extracting b43/lp0initvals14.fw
Extracting b43/ucode16_lp.fw
Extracting b43/ucode16_sslpn.fw
  ucode revision: 1084
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/sslpn2bsinitvals17.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/ucode16_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/sslpn2initvals17.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ucode17.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/pcm5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/ucode20.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
#
```

[quote="http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers"]type into terminal:

cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
(you may want to copy this) and see if the term blacklist bcm43xx is there

if it is, type cd /etc/modprobe.d/ and then sudo gedit blacklist.conf

put a # in front of the line: blacklist bcm43xx[/quote]
```
# cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
# wl module from Broadcom conflicts with ssb
blacklist b43legacy
blacklist b43
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
#
```

I found that the module was blacklisted, so I did as they said and edited **blacklist.conf** and commented out the line:
**# blacklist bcm43xx**

After a reboot, I'll do some testing and see if the new drivers are working better.

_**EDIT**_: After a reboot, these drivers don't seem to be working at all.  I'm double checking my Blacklists to see if anything else should be commented out...

Kirk

---

### Post by praseodym on 2013-09-25
Broadcom-STA is the right driver for this particular device. The kernel-headers. build-essential and dkms will build the module after kernel upgrades automatically. Check the blacklists:
```

egrep 'b43|wl|bcma|brcm' /etc/modprobe.d/*
```

---

### Post by varunendra on 2013-09-26
> **praseodym said:**
> Broadcom-STA is the right driver for this particular device.

+1
The b43 driver won't work with this card at all (see the supported device table [here]("http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices"))

Also, since you are on 12.04.3, have you tried updating the systems? I believe an update should upgrade your systems to kernel 3.8+
After that, you may try the latest version of the sta driver (version 6.30) from here : [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/)

As per change log on broadcom's site, there seem to be some very significant and useful changes being introduced in this version.

---

### Post by Kirk Schnable on 2013-09-26
Thank you, apparently one of my problems is the assumption that my vendor sent me all the same wireless card.  We have the BCM43228 cards, and I have a batch of BCM943228HM4L cards.  After checking my hardware database though, I'm not sure if the 943228 shows up as a 43228 card... maybe they're the same driver... I'll have to look at this further.

What would you think about using the brcmsmac driver for this card?  It seems like it might work.

---

### Post by Kirk Schnable on 2013-09-26
I ran into this issue a lot today.  I'm really anxious to come up with a solution.

I had to hand touch about 50 computers today for this issue.  I stopped doing diagnosis and started just running **sudo dpkg-reconfigure bcmwl-kernel-source && sudo reboot** on all of them.  About half of them immediatley fired up and worked afterward, and the other half needed me to do my **sudo  service network-manager stop && sudo ifconfig eth1 up  && sudo iwlist scan && service network-manager start** fix after recompiling the drivers before they'd connect.

I have not had a chance to try out the most recent Broadcom STA drivers  as of yet, but I think that's definitely something we need to do.  Any  other suggestions would be very much appreciated!  Thanks!

---

### Post by varunendra on 2013-09-26
> **Kirk Schnable said:**
> Thank you, apparently one of my problems is the assumption that my vendor sent me all the same wireless card. We have the BCM43228 cards, and I have a batch of BCM943228HM4L cards.  After checking my hardware database though, I'm not sure if the 943228 shows up as a 43228 card...
If you are not already aware, you can check the card with -
```
lspci -nn | grep 0280
```
This gives you both the chip ID *(e.g. BCM43228)* and PCI ID *(e.g. [14e4:4359] or [14e4:435a], both of these have same Chip ID (BCM43228) and use the same "wl" driver only)*. Note that the same Chip ID can have multiple and different PCI IDs, and it is the PCI ID that decides which driver is going to work.

In case of BCM43228, although there are two variations available as pointed out above, both variations use the proprietary "sta" driver (appears as "wl in lsmod).

Based on the [supported device table]("http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices") I linked to earlier, it doesn't look like these cards are supported by the brcmsmac.

Unfortunately, if you are doubtful if you have these same cards or not, you'll have to run "lspci -nn | grep 0280" on each netbook to be sure, we don't know any shortcut to that ;)

If you happen to have different cards than these two, write down a list of them and post back here. We may then be able to work out a solution list for you accordingly. :P

---

### Post by Kirk Schnable on 2013-09-27
Thanks for your responses so far everyone.

We've been very overwhelmed in my department by this problem the past few days.  I've created a bandaid which we will plan to cron on all of our machines after testing them.  Hopefully this will lighten the load on our resources enough that we'll have time for a proper fix.

Anyone else having the issue, please feel free to use and improve my script!  Let me know if you encounter any issues.

```
#!/bin/bash
###############################################################################
#                               Wireless Fix                                  #
#                         Written by Kirk Schnable                            #
###############################################################################
#         This fix is a band-aid for the Broadcom STA Driver bug.             #
###############################################################################

#> Paths To Binaries
    IWCONFIG="/sbin/iwconfig"
    IFCONFIG="/sbin/ifconfig"
    IWLIST="/sbin/iwlist"
    SERVICE="/usr/bin/service"
    ECHO="/bin/echo"
    GREP="/bin/grep"
    AWK="/usr/bin/awk"
    HEAD="/usr/bin/head"
    WC="/usr/bin/wc"

#> Service Names
    NetworkManager="network-manager"

#> Functions
    output(){
        $ECHO $@
    }

############################## CODE, DO NOT EDIT ##############################

#> Find WiFi Interface
    output "Detecting wireless interfaces..."
    WLANINT=$($IWCONFIG | $GREP "IEEE 802.11" | $AWK {'print $1'} | $HEAD -n 1)
    if [ -z $WLANINT ];
    then
        output "No wireless interfaces detected.  Exiting."
        exit 0
    fi

#> Determine Whether It Has An IP Already
    output "Checking for an IP Addresses other than loopback..."
    IPcount=$($IFCONFIG | $GREP "inet addr" | $GREP -v 127.0.0.1 | $WC -l)
    if [ "$IPcount" -gt "0" ]; then
        output "IP address detected. Taking no action."
        exit 0
    fi

#> Stop Network Manager
    output "Stopping Network Manager Service..."
    $SERVICE $NetworkManager stop

#> Up The Interface Manually
    output "Bringing up $WLANINT..."
    $IFCONFIG $WLANINT up

#> Rescan For New Access Points
    output "Scanning for nearby wireless access points..."
    $IWLIST scan

#> Start Network Manager
    output "Restarting Network Manager Service..."
    $SERVICE $NetworkManager start

#> Finished
    output "Finished. Please verify your wireless connectivity."
    exit 0
```

---

### Post by Kirk Schnable on 2013-09-27
> **varunendra said:**
> If you are not already aware, you can check the card with -
```
lspci -nn | grep 0280
```
This gives you both the chip ID *(e.g. BCM43228)* and PCI ID *(e.g. [14e4:4359] or [14e4:435a], both of these have same Chip ID (BCM43228) and use the same "wl" driver only)*. Note that the same Chip ID can have multiple and different PCI IDs, and it is the PCI ID that decides which driver is going to work.

In case of BCM43228, although there are two variations available as pointed out above, both variations use the proprietary "sta" driver (appears as "wl in lsmod).
Yeah, I think I've seen that command once or twice before.  Here's the output for one of my test machines:

```
09:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
```

I'll need to keep my eye on this and see if there are other revisions of this card floating around.

> **varunendra said:**
>  Based on the [supported device table]("http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices") I linked to earlier, it doesn't look like these cards are supported by the brcmsmac.
Yes, I agree.  I've loaded the module manually a few times, and it doesn't seem that brcmsmac works with these cards.

> **varunendra said:**
>  Unfortunately, if you are doubtful if you have these same cards or not, you'll have to run "lspci -nn | grep 0280" on each netbook to be sure, we don't know any shortcut to that ;)

If you happen to have different cards than these two, write down a list of them and post back here. We may then be able to work out a solution list for you accordingly. :P
Yeah, I'll keep an eye on it. 

So far, I'll be using my bandaid script for a quick fix.
> **Kirk Schnable said:**
> ```
#!/bin/bash
###############################################################################
#                               Wireless Fix                                  #
#                         Written by Kirk Schnable                            #
###############################################################################
#         This fix is a band-aid for the Broadcom STA Driver bug.             #
###############################################################################

#> Paths To Binaries
    IWCONFIG="/sbin/iwconfig"
    IFCONFIG="/sbin/ifconfig"
    IWLIST="/sbin/iwlist"
    SERVICE="/usr/bin/service"
    ECHO="/bin/echo"
    GREP="/bin/grep"
    AWK="/usr/bin/awk"
    HEAD="/usr/bin/head"
    WC="/usr/bin/wc"

#> Service Names
    NetworkManager="network-manager"

#> Functions
    output(){
        $ECHO $@
    }

############################## CODE, DO NOT EDIT ##############################

#> Find WiFi Interface
    output "Detecting wireless interfaces..."
    WLANINT=$($IWCONFIG | $GREP "IEEE 802.11" | $AWK {'print $1'} | $HEAD -n 1)
    if [ -z $WLANINT ];
    then
        output "No wireless interfaces detected.  Exiting."
        exit 0
    fi

#> Determine Whether It Has An IP Already
    output "Checking for an IP Addresses other than loopback..."
    IPcount=$($IFCONFIG | $GREP "inet addr" | $GREP -v 127.0.0.1 | $WC -l)
    if [ "$IPcount" -gt "0" ]; then
        output "IP address detected. Taking no action."
        exit 0
    fi

#> Stop Network Manager
    output "Stopping Network Manager Service..."
    $SERVICE $NetworkManager stop

#> Up The Interface Manually
    output "Bringing up $WLANINT..."
    $IFCONFIG $WLANINT up

#> Rescan For New Access Points
    output "Scanning for nearby wireless access points..."
    $IWLIST scan

#> Start Network Manager
    output "Restarting Network Manager Service..."
    $SERVICE $NetworkManager start

#> Finished
    output "Finished. Please verify your wireless connectivity."
    exit 0
```


Thanks
Kirk

---

### Post by varunendra on 2013-09-28
> **Kirk Schnable said:**
> Here's the output for one of my test machines:

```
09:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n **[14e4:4353]** (rev 01)
```

Now this one is compatible with all three drivers, and my personal preference would be b43. To make it work, make sure to 'purge' (not just 'remove') the sta driver first -
```
sudo apt-get purge bcmwl-kernel-source
```

Then install the firmware for b43 -
```
sudo apt-get install linux-firmware-nonfree
```
Then either reboot or load b43 with -
```
sudo modprobe -v b43
```

If your script works as expected, I'd suggest you get some time to check all of the systems and create a list of all the variations of cards you have. It being such a huge network, I assume you should have a way to upload an output from each system to a particular system/server. If so, a command like the following one may make your task much easier -
```
echo -e "\n$HOSTNAME \t-->\t `lspci -nn | grep 0280 | sed 's/.*\[0280\]: //'`" >> (path to target syetem)/wifi-card-list.txt
```
This will create a list of all the systems (their Hostnames) with the wireless card they are using, in a single file "wifi-card-list.txt" in the target system.

Once this list is created, you can create a sorted copy of it to see all the card models you have. Pick one system for each model for your experiments, and as soon as the optimal driver/solution is found for it, apply it on all the identical system in whatever way you like.

**PS:**
Was the same setup working fine before? I am suspecting that maybe a network congestion or access-point limitation could also be a factor? If not the sole reason..

---

### Post by Kirk Schnable on 2013-09-30
> **varunendra said:**
> Now this one is compatible with all three drivers, and my personal preference would be b43. To make it work, make sure to 'purge' (not just 'remove') the sta driver first -
```
sudo apt-get purge bcmwl-kernel-source
```

Then install the firmware for b43 -
```
sudo apt-get install linux-firmware-nonfree
```
Then either reboot or load b43 with -
```
sudo modprobe -v b43
```
Knowing that we have so many different Broadcom devices made me a bit skeptical that blaming the drivers could have been ignoring a bigger picture problem.

> **varunendra said:**
>  If your script works as expected, I'd suggest you get some time to check all of the systems and create a list of all the variations of cards you have. It being such a huge network, I assume you should have a way to upload an output from each system to a particular system/server. If so, a command like the following one may make your task much easier -
```
echo -e "\n$HOSTNAME \t-->\t `lspci -nn | grep 0280 | sed 's/.*\[0280\]: //'`" >> (path to target syetem)/wifi-card-list.txt
```
This will create a list of all the systems (their Hostnames) with the wireless card they are using, in a single file "wifi-card-list.txt" in the target system.

Once this list is created, you can create a sorted copy of it to see all the card models you have. Pick one system for each model for your experiments, and as soon as the optimal driver/solution is found for it, apply it on all the identical system in whatever way you like.
I do have a custom hardware scraping system which I wrote 2 years ago in place today.  It doesn't report back that much detail about the wireless card (PCI IDs are not included), but I did run a quick SQL query on that database and I found these Broadcom models in circulation:

I'm guessing these are the old non-dual band cards that we're trying to phase out:
BCM4312 802.11b/g
BCM4313 802.11b/g/n

These should represent our dual band cards which we are phasing in:
BCM43224 802.11a/b/g/n
BCM43228 802.11a/b/g/n

> **varunendra said:**
> **PS:**
Was the same setup working fine before? I am suspecting that maybe a network congestion or access-point limitation could also be a factor? If not the sole reason..
Your question made me think about things.

I was pretty sure that the setup was the same, but I remembered having a conversation with our network administrator last week about how some of our APs were overloaded while others sat idle, so he was going to turn on Cisco's load balancing on our controller.

As I mentioned in [this other thread]("http://ubuntuforums.org/showthread.php?t=2177780"), a lot of our association requests are timing out.

```
Sep 30 10:26:29 Hostname wpa_supplicant[948]: Trying to associate with ##:##:##:##:##:## (SSID='OurSSID' freq=2462 MHz)
Sep 30 10:26:29 Hostname wpa_supplicant[948]: Association request to the driver failed
Sep 30 10:26:29 Hostname NetworkManager[877]: <info> (eth1): supplicant interface state: scanning -> associating
Sep 30 10:26:34 Hostname wpa_supplicant[948]: Authentication with ##:##:##:##:##:## timed out.
Sep 30 10:26:34 Hostname NetworkManager[877]: <info> (eth1): supplicant interface state: associating -> scanning
Sep 30 10:26:36 Hostname wpa_supplicant[948]: Trying to associate with ##:##:##:##:##:## (SSID='OurSSID' freq=2412 MHz)
Sep 30 10:26:36 Hostname wpa_supplicant[948]: Association request to the driver failed
Sep 30 10:26:36 Hostname NetworkManager[877]: <info> (eth1): supplicant interface state: scanning -> associating
Sep 30 10:26:41 Hostname wpa_supplicant[948]: Authentication with ##:##:##:##:##:## timed out.
Sep 30 10:26:41 Hostname NetworkManager[877]: <info> (eth1): supplicant interface state: associating -> scanning
Sep 30 10:26:44 Hostname wpa_supplicant[948]: Trying to associate with ##:##:##:##:##:## (SSID='OurSSID' freq=2412 MHz)
Sep 30 10:26:44 Hostname wpa_supplicant[948]: Association request to the driver failed
Sep 30 10:26:44 Hostname NetworkManager[877]: <info> (eth1): supplicant interface state: scanning -> associating
```

This got me thinking... what if the requests were timing out because Cisco's load balancing was trying to tell the laptop not to connect to the access point due to it being overloaded?  This might explain why in a room of 25 people, 10 are usually affected.

I talked this over with our network administrator over lunch today, and we have turned off the load balancing on the controller.  So far, I've only had 3 people come down with wireless issues, and all of them were broken DPKG updates from shutting down the computer while cron-apt was running.

My going theory is that Cisco's load balancing was causing this problem all along.  We'll see how things go the rest of the day today... and then hopefully tomorrow will start off smoothly!  I'll keep you informed.

Thanks,
Kirk

---

### Post by gordintoronto on 2013-10-01
Is it more or less true that you have 20 rooms with 25 computers in each? How many routers do you have? Do you set them to different channels? Do they all use the same ESSID? 

From Full Circle Magazine: "Sometimes the problem in 'campus' type networks is that they have multiple access points sharing the same ESSID. That can make the wireless device go crazy trying to roam to the nearest / strongest access point. Run this command: sudo iwlist scan
Add the MAC-address of the nearest access point into the field "BSSID" in the network-manager applet. (You'll need to change it if you move to a different location.)"

---

### Post by MIJ-VI on 2013-10-01
A process of elimination long-shot:

I remedied a Broadcom BCM4311 hair-pull in a neighbour's notebook a few months back by installing: [SIZE=1][FONT=courier new]linux-firmware-nonfree[/FONT][/SIZE] from the repos.

---

### Post by Kirk Schnable on 2013-10-01
> **gordintoronto said:**
> Is it more or less true that you have 20  rooms with 25 computers in each? How many routers do you have? Do you  set them to different channels? Do they all use the same ESSID?
We have 72 access points.  Rooms have anywhere from 5 to 35 computers.   We use 3 different ESSID's and all the APs transmit them all.

> **gordintoronto said:**
>  From Full Circle Magazine: "Sometimes the  problem in 'campus' type networks is that they have multiple access  points sharing the same ESSID. That can make the wireless device go  crazy trying to roam to the nearest / strongest access point. Run this  command: sudo iwlist scan
Add the MAC-address of the nearest access point into the field "BSSID"  in the network-manager applet. (You'll need to change it if you move to a  different location.)"
I am aware of this mindset, but this hasn't been an issue for us.  The  issues I was experiencing involved a timeout between the computer and  the AP, not the computer randomly AP hopping.

Setting a static BSSID is not an option for 400+ of our machines which move around the building with the students.

---


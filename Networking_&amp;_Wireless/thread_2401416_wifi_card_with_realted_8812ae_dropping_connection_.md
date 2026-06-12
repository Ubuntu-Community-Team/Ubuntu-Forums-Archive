---
title: "wifi card with realted 8812ae dropping connection on ubuntu 18.04"
date: 2018-09-18
forum: Networking &amp; Wireless
---

### Post by tbabula on 2018-09-18
I have old Dell Optiplex 980 and use Asus RTL8812AE 802.11ac PCIe to connect to my wifi network. I would prefer wired, but live in a small studio with odd layout and running CAT cable is not really an option for me.

I installed Ubuntu 18.04 fresh. To my knowledge there is some issue with full support of wifi cards with Realtek chipset on Linux. After installation, the wifi worked straight out of box but it was slow. Upgraded wifi drivers with rtlwifi_new stack from GIT. It allowed the card to have full speed, however next time after reboot, the pages were loading slow or timing out. I reloaded the wifi module  and rebooted  my machine a few times   which  had no effect on the connection's reliability. I turn my computer next day to gather some diagnostic data and post to forum and all of sudden it is working! :confused: During this whole time it has stayed on 5GHz frequency. During the same time I tested other devices to my wifi network with no issues.  

Previously I had ubuntu 16.04 and after installing rtlwifi_new stack, I had no problems except it tended to drop randomly from 5 to 2.4 GHz and I figured out how to force it to stay on 5 Ghz. Sometimes it would had dropped wifi connection for a second and re-establish connection. 

If anyone knows a good source of drivers to try or what settings I should look at with configuration files please share!

If these lead to no progress, I am thinking about switching to Mint to address reliability but is it worth it since it is based on Ubuntu? In worst case, if performance deteriorates and stays unstable, I may have to go full with Windows 10 and install Ubuntu as VM since the card works consistently well under that platform.

Thanks!

>  
[B]lspci | grep Wireless
[/B]01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter (rev 01)


**iwconfig**
eno1      no wireless extensions.

wlp1s0    IEEE 802.11  ESSID:"skywalker"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: E4:F0:42:EB:EF:5A   
          Bit Rate=400 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:389   Missed beacon:0

**sudo lspci -vv -s 01:00.0**
[sudo] password for tom: 
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter (rev 01)
    Subsystem: ASUSTeK Computer Inc. RTL8812AE 802.11ac PCIe Wireless Network Adapter
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 28
    Region 0: I/O ports at dc00 [size=256]
    Region 2: Memory at f7afc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee04004  Data: 4025
    Capabilities: [70] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset- SlotPowerLimit 10.000W
        DevCtl:    Report errors: Correctable- Non-Fatal+ Fatal+ Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <512ns, L1 <64us
            ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis+, LTR+, OBFF Via message/WAKE#
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis+, LTR-, OBFF Disabled
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [140 v1] Device Serial Number 00-12-88-fe-ff-4c-e0-00
    Capabilities: [150 v1] Latency Tolerance Reporting
        Max snoop latency: 0ns
        Max no snoop latency: 0ns
    Capabilities: [158 v1] L1 PM Substates
        L1SubCap: PCI-PM_L1.2+ PCI-PM_L1.1+ ASPM_L1.2+ ASPM_L1.1+ L1_PM_Substates+
              PortCommonModeRestoreTime=150us PortTPowerOnTime=150us
        L1SubCtl1: PCI-PM_L1.2- PCI-PM_L1.1- ASPM_L1.2- ASPM_L1.1-
               T_CommonMode=0us LTR1.2_Threshold=0ns
        L1SubCtl2: T_PwrOn=10us
    Kernel driver in use: rtl8821ae
    Kernel modules: rtl8821ae

[B]nmcli -f GENERAL,WIFI-PROPERTIES dev show wlp1s0
[/B]GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8812AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.15.0-34-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         B0:6E:BF:DC:0D:90
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     skywalker
GENERAL.CON-UUID:                       6a983e1f-ba82-4095-8875-e61d3ade306b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes




[B]
modinfo rtl8821ae[/B]
filename:       /lib/modules/4.15.0-34-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw_29.bin
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     2CE28F5AC9749CAF48145E8
alias:          pci:v000010ECd00008821sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008812sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
retpoline:      Y
name:           rtl8821ae
vermagic:       4.15.0-34-generic SMP mod_unload 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)


**lsmod**
Module                  Size  Used by
ccm                    20480  6
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          40960  6
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
gpio_ich               16384  0
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
arc4                   16384  2
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
rtl8821ae             233472  0
btcoexist             172032  1 rtl8821ae
rtl_pci                32768  1 rtl8821ae
rtlwifi                98304  3 rtl_pci,btcoexist,rtl8821ae
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
intel_powerclamp       16384  0
coretemp               16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
kvm_intel             212992  0
snd_timer              32768  2 snd_seq,snd_pcm
dcdbas                 16384  0
sch_fq_codel           20480  6
mac80211              778240  3 rtl_pci,rtlwifi,rtl8821ae
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
intel_cstate           20480  0
snd                    81920  23 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
joydev                 24576  0
input_leds             16384  0
sparse_keymap          16384  0
dell_wmi_descriptor    16384  0
wmi_bmof               16384  0
cfg80211              622592  2 mac80211,rtlwifi
soundcore              16384  1 snd
serio_raw              16384  0
mei_me                 40960  0
mei                    90112  1 mei_me
lpc_ich                24576  0
shpchp                 36864  0
mac_hid                16384  0
parport_pc             36864  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
i915                 1617920  31
video                  45056  1 i915
i2c_algo_bit           16384  1 i915
psmouse               147456  0
drm_kms_helper        172032  1 i915
ahci                   36864  1
libahci                32768  1 ahci
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
e1000e                249856  0
fb_sys_fops            16384  1 drm_kms_helper
drm                   401408  17 i915,drm_kms_helper
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
pata_acpi              16384  0
wmi                    24576  2 wmi_bmof,dell_wmi_descriptor



**lshw -C network**
WARNING: you should run this program as super-user.
  *-network                 
       description: Wireless interface
       product: RTL8812AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 01
       serial: b0:6e:bf:dc:0d:90
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.15.0-34-generic firmware=N/A ip=192.168.86.32 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:28 ioport:dc00(size=256) memory:f7afc000-f7afffff




---

### Post by jz888888 on 2018-10-05
It seems the default driver for RTL8812AE has problems on power saving. So I tried to solve it with this [https://ubuntuforums.org/showthread.php?t=2348161&page=2&highlight=rtl8812ae]("http://post https://ubuntuforums.org/showthread.php?t=2348161&page=2&highlight=rtl8812ae") to turn the power save off. It did work and the connection did not get down again. However, the connection speed is still unstable. Next, I may try [https://ubuntuforums.org/showthread.php?t=2351156&page=3&highlight=rtl8812ae](https://ubuntuforums.org/showthread.php?t=2351156&page=3&highlight=rtl8812ae) and [https://ubuntuforums.org/showthread.php?t=2293272](https://ubuntuforums.org/showthread.php?t=2293272)

---


---
title: "Restoring Network Manager"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by earl100 on 2011-05-31
I installed Ubuntu 10.10

I now don't have Network Manager.  Not just the icon missing from the toolbar, but can't connect to wireless network.  

Installed Ubuntu again, in a different partition.  It has Network Manager.

Would like to copy Network Manager from the second partition to the first. Or, somehow, download the applet and install to the partition which lacks it.

Any suggestions?


Here's some data from the partition which cannot connect to the wireless network that it recognizes.


ran these:

nm-tool

sudo lshw -C network

rfkill list all

lsmod

sudo iwconfig

sudo iwlist scan


Results

 **nm-tool** 

NetworkManager Tool 

State: disconnected 

- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            r8169 
  State:             unavailable 
  Default:           no 
  HW Address:        00:26:22:F9:BB:1D 

  Capabilities: 
    Carrier Detect:  yes 
    Speed:           10 Mb/s 

  Wired Properties 
    Carrier:         off 


- Device: wlan1 ---------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            rtl819xU 
  State:             disconnected 
  Default:           no 
  HW Address:        00:E0:4C:00:74:F2 

  Capabilities: 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points 
    MainLib-Guest:   Infra, 00:23:33:21:56:30, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 
  
  Type:              802.11 WiFi 
  Driver:            ath9k 
  State:             disconnected 
  Default:           no 
  HW Address:        00:26:B6:84:45:35 

  Capabilities: 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points 
    
    MainLib-Guest:   Infra, 00:21:1C:FD:F3:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 
    

 sudo lshw -C network 
  *-network               
       description: Wireless interface 
       product: AR9285 Wireless Network Adapter (PCI-Express) 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wlan0 
       version: 01 
       serial: 00:26:b6:84:45:35 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:17 memory:f0100000-f010ffff 
  *-network 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:26:22:f9:bb:1d 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
       resources: irq:44 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff 
  *-network 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan1 
       serial: 00:e0:4c:00:74:f2 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=802.11b/g/n 

rfkill list all 

0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 


lsmod 

Apparently there is some sort of limitation re posting, so I've interrupted the msg.

---

### Post by el_koraco on 2011-05-31
First go to startup applications and see if the nm applet (or network manager) is set to autostart.

---

### Post by earl100 on 2011-05-31
Module                  Size  Used by 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   217980  1 
arc4                    1165  2 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               5040  1 snd_hda_codec 
ath9k                  88756  0 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec 
ath9k_common            5982  1 ath9k 
snd_seq_midi            4588  0 
joydev                  8735  0 
i915                  291004  4 
snd_rawmidi            17783  1 snd_seq_midi 
ath9k_hw              292297  2 ath9k,ath9k_common 
ath                     8153  2 ath9k,ath9k_hw 
snd_seq_midi_event      6047  1 snd_seq_midi 
drm_kms_helper         30200  1 i915 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event 
drm                   168054  5 i915,drm_kms_helper 
mac80211              231541  2 ath9k,ath9k_common 
snd_timer              19067  2 snd_pcm,snd_seq 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq 
uvcvideo               55847  0 
r8192s_usb            287340  0 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211 
videodev               43098  1 uvcvideo 
intel_agp              26360  2 i915 
psmouse                59033  0 
i2c_algo_bit            5168  1 i915 
led_class               2633  1 ath9k 
soundcore                880  1 snd 
agpgart                32011  2 drm,intel_agp 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm 
v4l1_compat            13359  2 uvcvideo,videodev 
video                  18712  1 i915 
eeprom_93cx6            1345  1 r8192s_usb 
usb_storage            40172  1 
serio_raw               4022  0 
output                  1883  1 video 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp 
r8169                  36489  0 
mii                     4425  1 r8169

---

### Post by earl100 on 2011-05-31
Thanks for the quick attention.  No. The nm applet (or network manager) is not set to autostart

---

### Post by earl100 on 2011-06-01
Still cannot connect to wifi without network manager.  My laptop has a 802.11g card, and there seems to be a driver installed, recognizes nearby nets, but won't connect.  Any suggestions?

Stewart

---

### Post by grahammechanical on 2011-06-01
I am confused. 

1) If Network Manager was not set as a startup application, did you select it to autostart and then shutdown and restart? If not then Network Manager will not load when you switch on the computer.

2) If Network Manager is not functioning how is it that you say this?

>  recognizes nearby nets, but won't connect.

If after marking Network Manager as a Startup application and rebooting you still do not see the Network manager icon in the top panel, then click on the top panel and select Add to Panel. Select Notification area to be added to the top panel. This should put the Network Manager icon in the top panel.

Left click the icon and select your wireless network and typing the wireless key or pass phrase when asked to and also set the encryption or security method.

Regards.

---

### Post by earl100 on 2011-06-01
> **grahammechanical said:**
> I am confused. 

1) If Network Manager was not set as a startup application, did you select it to autostart and then shutdown and restart? If not then Network Manager will not load when you switch on the computer.

2) If Network Manager is not functioning how is it that you say this?



If after marking Network Manager as a Startup application and rebooting you still do not see the Network manager icon in the top panel, then click on the top panel and select Add to Panel. Select Notification area to be added to the top panel. This should put the Network Manager icon in the top panel.

Left click the icon and select your wireless network and typing the wireless key or pass phrase when asked to and also set the encryption or security method.

Regards.
Thanks for the reply Graham,

In my first post I said:  "I now don't have Network Manager. Not just the icon missing from the toolbar, but can't connect to wireless network".

I have a network card...wifi "g", and it apparently recognizes wifi networks. I would like to connect to one so I can reinstall Network Manager.  

Network Manager is set as a strartup application .  The box on the set up page is checked.  But the application itself got uninstalled.  I want to reinstall it.  In order to reinstall it I have to connect to the internet.  I can't connect to the internet , even though my card recognizes wifi connections, because I don't have the applet called Network Manager.

How can I connect to the internet?

Does that unconfuse?

---


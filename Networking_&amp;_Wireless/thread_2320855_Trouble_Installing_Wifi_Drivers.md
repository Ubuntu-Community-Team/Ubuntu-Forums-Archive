---
title: "Trouble Installing Wifi Drivers"
date: 2016-04-18
forum: Networking &amp; Wireless
---

### Post by Megaride on 2016-04-18
In my case I am using Ubuntu 14.04.4 LTS x86_64 but I am stucked with this AC600 driver too.Here are some output:
```

**lsmod**

Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
mt7610u_sta           900453  0 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
arc4                   12608  2 
radeon               1417263  4 
ath9k                 141379  0 
snd_hda_codec_realtek    77696  1 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
snd_hda_intel          30549  3 
mac80211              652716  1 ath9k
ttm                    93588  1 radeon
drm_kms_helper         61574  1 radeon
snd_hda_controller     30228  1 snd_hda_intel
kvm_amd                60404  0 
snd_hda_codec         139719  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
cfg80211              498458  5 ath,ath9k_common,ath9k,mac80211,mt7610u_sta
snd_hwdep              17698  1 snd_hda_codec
kvm                   456292  1 kvm_amd
snd_pcm               104112  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
drm                   311061  7 ttm,drm_kms_helper,radeon
snd_rawmidi            31348  1 snd_seq_midi
snd_seq                63130  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
parport_pc             32741  0 
joydev                 17393  0 
ppdev                  17671  0 
i2c_algo_bit           13413  1 radeon
serio_raw              13483  0 
snd_timer              29562  2 snd_pcm,snd_seq
ene_ir                 18449  0 
k10temp                13144  0 
toshiba_acpi           28272  0 
rc_core                28718  1 ene_ir
sparse_keymap          13948  1 toshiba_acpi
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
snd                     79468  16  snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
shpchp                 37047  0 
wmi                    19193  1 toshiba_acpi
mac_hid                13227  0 
toshiba_bluetooth      12867  0 
soundcore              15047  2 snd,snd_hda_codec
i2c_piix4              22166  0 
video                  20128  0 
psmouse               106767  0 
r8169                  71694  0 
mii                    13934  1 r8169
ahci                   34142  3 
libahci                32424  1 ahci
```

```
**ifconfig ra0 up**

SIOCSIFFLAGS: Operation not permitted

```
```
**sudo lshw -C network**

*-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 05
       serial: b8:70:f4:4d:e3:ee
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw  ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:c000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network DISABLED
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan1
       version: 01
       serial: c0:f8:da:4c:83:98
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k  driverversion=3.16.0-70-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:fe900000-fe90ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA

```
```
**dmesg | grep mt7610u_sta**

[   22.362268] mt7610u_sta: module verification failed: signature and/or  required key missing - tainting kernel

```
```
[B]rfkill list all

[/B]0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by coffeecat on 2016-04-18
5 posts merged, code tags added for readability and moved to own thread.

---

### Post by chili555 on 2016-04-18
Let me guess. You could never get the internal wireless going even though you have a driver and an interface, wlan1. You decided to get a USB wireless and installed the driver and now it doesn't work either. Isn't that about it?

The problem isn't the driver at all; it's this:> 0: phy0: Wireless LAN
    Soft blocked: no
    [COLOR="#FF0000"]Hard blocked: yes[/COLOR]
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: noThe hardware switch or key combination is set to disable wireless.> *-network [COLOR="#FF0000"]DISABLED[/COLOR]
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan1
       version: 01
       serial: c0:f8:da:4c:83:98
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k  driverversion=3.16.0-70-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:fe900000-fe90ffff
  *-network [COLOR="#FF0000"]DISABLED[/COLOR]
       description: Wireless interface
       physical id: 1
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STAUntil you find and switch the switch, I'm afraid we will get nowhere. When you do switch the switch, I suspect that the internal device will work perfectly well.

---

### Post by Megaride on 2016-04-18
Followed the thread and tried last tip but this TP-LINK archer is not working.

This is my ubuntu version:

Ubuntu 14.04.4 LTS x86_64
[B]
rfkill list all[/B]
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2016-04-18
> rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: **yes**[/COLOR]
2: phy2: Wireless LAN
Soft blocked: no
Hard blocked: no Find and switch the wireless switch or key combination and I suspect your wireless will work as expected.

---

### Post by Megaride on 2016-04-18
Oh that is the inner wifi that is not working so it has been disconnected phy2 is not blocked

---

### Post by chili555 on 2016-04-18
> **Megaride said:**
> Oh that is the inner wifi that is not working so it has been disconnected phy2 is not blockedPlease return to your original thread here. [http://ubuntuforums.org/showthread.php?t=2320855](http://ubuntuforums.org/showthread.php?t=2320855)

I have, over the years, had no luck at all trying to answer a post in 2-3 places at once.

---

### Post by chili555 on 2016-04-18
> Oh that is the inner wifi that is not working so it has been disconnected phy2 is not blockedThen why does it show as DISABLED?

---

### Post by coffeecat on 2016-04-18
And more posts moved from the other thread into this one.

@Megaride, please stop hijacking someone else's thread. That is why I moved your original posts to create this thread so that those helping you can do so in your own thread. If you post to someone else's thread, things get confusing. Chilli555 is giving you excellent support, but you can help him to help you by confining yourself to this thread for this problem.

---

### Post by Megaride on 2016-04-19
Ok now I see sorry for that messing up. I will write only in this thread.
My laptop wireless card stopped working, instead of replacing  it I bought a TP LINK archer T2u AC600 usb adapter, it works perfectly with windows but have problems with ubuntu, tried several times the switch FN F8 of my laptop, but still will not fix the problem.

---

### Post by chili555 on 2016-04-19
> **Megaride said:**
> Ok now I see sorry for that messing up. I will write only in this thread.
My laptop wireless card stopped working, instead of replacing  it I bought a TP LINK archer T2u AC600 usb adapter, it works perfectly with windows but have problems with ubuntu, tried several times the switch FN F8 of my laptop, but still will not fix the problem.Let's start by blacklisting the driver for the internal device and see if it helps. Please open a terminal and do:```
sudo -i
echo "blacklist ath9k"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and show us:```
rfkill list all
dmesg | grep mt76
```Thanks.

---


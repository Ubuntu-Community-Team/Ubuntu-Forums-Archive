---
title: "I broke all the networking."
date: 2014-06-07
forum: Networking &amp; Wireless
---

### Post by dan-du on 2014-06-07
So, on my laptop, I installed Ubuntu 14.10, and installed the linux-firmware-nonfree for my wireless to work (BCM4311). At first this worked awesomely.
But 2 days later, it stopped detecting my wireless network (but it detected a neighbors wireless printer). So, in my attempt to fix it (with a ton of google), I came across this page on the Ubuntu wiki 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20Internet%20access) 
So I followed the b43 instructions for 8.04-10.04, not realizing there was instructions for 14.04 below that.
After I followed the instructions, my eth0 broke. (And my wifi still didn't work.) So then I followed the b43 - No Internet access instructions (for 14.04, should be close enough) and my wifi still doesn't work. (Nor does the ethernet, which uses a BCM4401-B0 10/100 controller.)

---

### Post by oldos2er on 2014-06-07
Moved to Networking & Wireless.

---

### Post by chili555 on 2014-06-07
Please open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
```Reboot and let us hear an update.

---

### Post by dan-du on 2014-06-08
That partially worked, the ethernet is back, and the wifi is too, but i'm still having the issue of my wifi not getting detected.

---

### Post by chili555 on 2014-06-10
Please show us:```
sudo iwlist wlan0 scan
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```We don't need to see the entire scan results; just tell us if it scans and sees your own network.

---

### Post by dan-du on 2014-06-10
```
dan@dan-Inspiron-1501:~$ sudo iwlist wlan0 scan[sudo] password for dan: 
wlan0     No scan results


dan@dan-Inspiron-1501:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
dan@dan-Inspiron-1501:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false
dan@dan-Inspiron-1501:~$ 

```

In other words, no, it doesn't detect it.
[SIZE=1](u jelly of my non-crowded 2.4GHz band? ;) )[/SIZE]

---

### Post by dan-du on 2014-06-12
So, is there no way to fix it? I need this laptop very soon and Windows outright sucks.
(LRN2DRIVERS ATI)

---

### Post by steeldriver on 2014-06-12
The above outputs look OK to me... can you also post outputs from

```

sudo lshw -C network -sanitize

lsmod

```

The 1st command may take some time to probe the H/W - please be patient

---

### Post by dan-du on 2014-06-12
```
  
*-network                      description: Network controller
       produit: BCM4311 802.11b/g WLAN
       fabriquant: Broadcom Corporation
       identifiant matériel: 0
       information bus: pci@0000:05:00.0
       version: 01
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       ressources: irq:18 mémoire:c0200000-c0203fff
  *-network
       description: Ethernet interface
       produit: BCM4401-B0 100Base-TX
       fabriquant: Broadcom Corporation
       identifiant matériel: 0
       information bus: pci@0000:08:00.0
       nom logique: eth0
       version: 02
       numéro de série: [REMOVED]
       taille: 100Mbit/s
       capacité: 100Mbit/s
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=[REMOVED] latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       ressources: irq:21 mémoire:c0300000-c0301fff
  *-network
       description: Interface réseau sans fil
       identifiant matériel: 2
       nom logique: wlan0
       numéro de série: [REMOVED]
       fonctionnalités: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.15.0-5-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg



```

```
Module                  Size  Used bysnd_hda_codec_idt      59067  1 
arc4                   12608  2 
snd_hda_codec_generic    68937  2 snd_hda_codec_idt
snd_hda_intel          30353  3 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139464  4 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               108688  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30544  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
radeon               1554449  4 
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
kvm_amd                60163  0 
dell_wmi               12761  0 
kvm                   447151  1 kvm_amd
sparse_keymap          13948  1 dell_wmi
b43                   387398  0 
ttm                    85279  1 radeon
snd                    73731  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
bcma                   52320  1 b43
drm_kms_helper         55228  1 radeon
joydev                 17393  0 
serio_raw              13483  0 
mac80211              632953  1 b43
edac_core              58195  0 
k8temp                 12990  0 
edac_mce_amd           22617  0 
bnep                   19624  2 
drm                   305004  7 ttm,drm_kms_helper,radeon
soundcore              12680  2 snd,snd_hda_codec
sp5100_tco             13999  0 
cfg80211              488654  2 b43,mac80211
i2c_piix4              22166  0 
ssb_hcd                12884  0 
i2c_algo_bit           13413  1 radeon
shpchp                 37047  0 
wmi                    19193  1 dell_wmi
rfcomm                 69473  0 
bluetooth             437343  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
video                  19494  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
binfmt_misc            17468  1 
pata_acpi              13053  0 
b44                    40400  0 
psmouse               106478  0 
sdhci_pci              23256  0 
sdhci                  43015  1 sdhci_pci
mii                    13934  1 b44
ssb                    62352  3 b43,b44,ssb_hcd
pata_atiixp            13279  0 
ahci                   29966  2 
libahci                32082  1 ahci

```

---

### Post by chili555 on 2014-06-12
May we also see:```
dmesg | grep -e b43 -e wlan
```

---

### Post by dan-du on 2014-06-13
```

[   21.221698] b43-phy0: Broadcom 4311 WLAN found (core revision 10)[   21.292979] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   26.712051] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   26.795752] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  391.808292] b43-phy0: Radio hardware status changed to DISABLED
[  731.828068] b43-phy0: Radio hardware status changed to ENABLED
[  731.992071] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  732.080986] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```
(i disabled it via the keyboard toggle buttons thing)

---

### Post by chili555 on 2014-06-14
It appears that the ethernet is attached and has an IP address. Network Manager will default to ethernet if it is available as it is usually faster and more secure. Please detach the ethernet, reboot so we have a clean slate and then run:```
dmesg  > wifi_dandu.txt
```Hook up the ethernet and find the file wifi_dandu.txt in your user directory and post it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by praseodym on 2014-06-14
Try to load the drivers in the right order via:
```

echo -e "blacklist b43\nblacklist b44\nblacklist ssb\nblacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf 
sudo sed -i "s/exit 0/# starting order for the broadcom drivers/g" /etc/rc.local
echo -e "modprobe ssb\nmodprobe bcma\nmodprobe b43\nmodprobe b44\nexit 0" | sudo tee -a /etc/rc.local
```
Reboot and check
```

iwconfig
rfkill list
iwlist chan sudo iwlist scan
ifconfig -a
route -n
cat /etc/resolv.conf
```

---

### Post by Phateless on 2014-06-15
I've been struggling with this same issue on a Dell D620. Go back to 14.04 or 13.10 and it will work perfectly.

The b43 instructions (link below) have always worked for me but in the past couple months they don't anymore.

[http://linuxg.net/how-to-fix-broadcom-bcm4311-wireless-driver-on-ubuntu-and-linux-mint/](http://linuxg.net/how-to-fix-broadcom-bcm4311-wireless-driver-on-ubuntu-and-linux-mint/)


I tried Zorin OS Lite (slightly less up to date Lubuntu variant) and it worked fine.

Other machines work perfectly on the same live usb with no issues.

---

### Post by dan-du on 2014-06-20
TY all for your help, but I ended up formatting.
Also, thanks for the tips in case I run into this problem again!

---

### Post by zipzapzoom on 2014-06-24
Hi Dan,

I am running into the same issue - upgraded to 14.10 and lost wireless. i.e; I can see a few networks but cant see mine. very strange. I've now tried everything and nothing works - ndiswrpapper b43 all of those end up in the same boat. I can see others networks but not mine - There are otehr devices that work fine without an issue. Just this one I believe due to 14.10. 

So curious as to what you meant when you said reformatted. Did yo reformat and install 14.04 ? 

Also any help is welcome. Please let me know if logs need to be posted etc. 

Thanks,

---

### Post by zipzapzoom on 2014-06-24
I believe the root of the problem is a kernel bug ?? 
The below shows up in dmesg everytime module wl is loaded. 
```

[   36.145755] ------------[ cut here ]------------
[   36.145812] kernel BUG at include/net/cfg80211.h:3275!
[   36.145866] invalid opcode: 0000 [#1] SMP 
[   36.145915] Modules linked in: wl(POE+) acer_wmi sparse_keymap uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq coretemp snd_seq_device snd_timer r852 sm_common nand joydev serio_raw lib80211 nand_ecc nand_bch bch snd nand_ids lpc_ich r592 cfg80211 mtd memstick shpchp soundcore cuse parport_pc ppdev lp parport mac_hid i915 firewire_ohci firewire_core sdhci_pci tg3 i2c_algo_bit drm_kms_helper psmouse sdhci crc_itu_t pata_acpi ptp drm pps_core wmi video
[   36.146637] CPU: 0 PID: 333 Comm: systemd-udevd Tainted: P           OE 3.15.0-6-generic #11-Ubuntu
[   36.146721] Hardware name: Acer, inc. \xffffffff\xffffffff\xffffffff\xffffffff\xffffffff\xffffffff\xffffffff\xffffffff\xffffffff\xffffffff\xffffffff\xffffffff\xffffffff\xffffffff\xffffffff /Nestos          , BIOS v1.3808 02/18/2008
[   36.146811] task: f6016d80 ti: f0c4e000 task.ti: f0c4e000
[   36.146885] EIP: 0060:[<f966bff6>] EFLAGS: 00010246 CPU: 0
[   36.146990] EIP is at wdev_priv.part.9+0x3/0x5 [wl]
[   36.147036] EAX: 00000000 EBX: f60fc634 ECX: f60fdc00 EDX: f60fc634
[   36.147095] ESI: f3e33000 EDI: f60fdc00 EBP: f0c4fbb8 ESP: f0c4fbb8
[   36.147154]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   36.147205] CR0: 80050033 CR2: bfe39e90 CR3: 30c94000 CR4: 000007f0
[   36.147264] Stack:
[   36.147287]  f0c4fbd0 f966ba17 6a73f414 f60fc634 f3e33000 f60fdc00 f0c4fbe8 f96643c3
[   36.147385]  f60fc60c f60fc600 f3e33000 e9c2f000 f0c4fc94 f9664a68 00000046 00000384
[   36.147483]  f0c4fc34 c10a96c7 c1afa9a0 00000400 01000002 00000046 00000383 00000000
[   36.147580] Call Trace:
[   36.147650]  [<f966ba17>] wl_cfg80211_detach+0xf7/0x100 [wl]
[   36.147753]  [<f96643c3>] wl_free_if.isra.12+0x23/0xa0 [wl]
[   36.147848]  [<f9664a68>] wl_free+0x78/0x260 [wl]
[   36.147899]  [<c10a96c7>] ? console_unlock+0x287/0x460
[   36.147956]  [<c1675552>] ? printk+0x50/0x52
[   36.148005]  [<f9664f5e>] wl_pci_probe+0x30e/0x630 [wl]
[   36.148005]  [<c1421be1>] ? __pm_runtime_resume+0x51/0x70
[   36.148005]  [<c133cd0f>] pci_device_probe+0x6f/0xc0
[   36.148005]  [<c11e66e5>] ? sysfs_create_link+0x25/0x40
[   36.148005]  [<c14196c3>] driver_probe_device+0x93/0x3a0
[   36.148005]  [<c133cc62>] ? pci_match_device+0xb2/0xc0
[   36.148005]  [<c1419a81>] __driver_attach+0x71/0x80
[   36.148005]  [<c1419a10>] ? __device_attach+0x40/0x40
[   36.148005]  [<c1417b67>] bus_for_each_dev+0x47/0x80
[   36.148005]  [<c141918e>] driver_attach+0x1e/0x20
[   36.148005]  [<c1419a10>] ? __device_attach+0x40/0x40
[   36.148005]  [<c1418de7>] bus_add_driver+0x157/0x230
[   36.148005]  [<c141a049>] driver_register+0x59/0xe0
[   36.148005]  [<f89ac000>] ? 0xf89abfff
[   36.148005]  [<c133b712>] __pci_register_driver+0x32/0x40
[   36.148005]  [<f89ac017>] wl_module_init+0x17/0x1000 [wl]
[   36.148005]  [<c1002142>] do_one_initcall+0xd2/0x190
[   36.148005]  [<f89ac000>] ? 0xf89abfff
[   36.148005]  [<c104e10f>] ? set_memory_nx+0x5f/0x70
[   36.148005]  [<c16757ea>] ? set_section_ro_nx+0x54/0x59
[   36.148005]  [<c10c9e40>] load_module+0x1210/0x1900
[   36.148005]  [<c10ca695>] SyS_finit_module+0x75/0xc0
[   36.148005]  [<c114059b>] ? vm_mmap_pgoff+0x7b/0xa0
[   36.148005]  [<c168875f>] sysenter_do_call+0x12/0x28
[   36.148005] Code: 0f b6 c7 38 d8 74 0d 0f b6 d2 89 c8 66 66 90 66 66 90 eb 0c 89 d0 f0 66 0f b1 19 66 39 d0 75 e7 5b 5d c3 55 89 e5 0f 0b 55 89 e5 <0f> 0b 55 89 e5 66 66 66 66 90 0f 0b 55 89 e5 66 66 66 66 90 0f
[   36.148005] EIP: [<f966bff6>] wdev_priv.part.9+0x3/0x5 [wl] SS:ESP 0068:f0c4fbb8
[   36.175418] ---[ end trace 95fef6be17c12521 ]---
```

---

### Post by chili555 on 2014-06-24
> The below shows up in dmesg everytime module wl is loaded. Is *wl* correct for your device?```
lspci -nn -d 14e4:
```

---

### Post by dan-du on 2014-06-25
I went to windows, i needed the computer quickly but I do plan to switching back to linux soon

---


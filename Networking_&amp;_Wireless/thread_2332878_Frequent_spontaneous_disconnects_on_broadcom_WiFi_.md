---
title: "Frequent spontaneous disconnects on broadcom WiFi in Ubuntu 16.04"
date: 2016-08-04
forum: Networking &amp; Wireless
---

### Post by Nathaniel_Osgood on 2016-08-04
[COLOR=#111111][FONT=Ubuntu]I recently purchased an HP Notebook 17-y020ca and installed XUbuntu 16.04. This notebook has a Broadcom Corporation BCM43142 wireless card.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This wireless card was not originally detected, and I followed the instructions at the following to install support using the bcmwl-kernel-source:
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][http://askubuntu.com/questions/76558...n-ubuntu-16-04]("http://askubuntu.com/questions/765584/is-it-possible-to-use-broadcom-bcm43142-wifi-in-ubuntu-16-04")
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After some futzing (resolved at [http://ubuntuforums.org/showthread.php?t=2329060](http://ubuntuforums.org/showthread.php?t=2329060)) the WiFi has been able to regularly detect networks and connect at least transiently.  By performing a ping, I was able to get beyond some earlier issues, apparently caused by the network card entering power saving mode.

[/FONT][/COLOR][COLOR=#000000]However, I am encountering severe problems with the network disconnecting periodically on my home and certain other WiFi networks. These disconnections occur every 4-6 minutes or so -- [/COLOR][COLOR=#000000]Given that this is a laptop which registers decent signal strength when connected, the problem seems to occur in close proximity to routers, and I therefore doubt any signal-strength issues. [/COLOR][COLOR=#000000] I am also experiencing [/COLOR]irregular ping timings to my local router (going from low milliseconds to hundreds times that).  [COLOR=#000000]I am not yet certain if the problem occurs uniformly across all networks, but the problem certainly appears to occur in most networks. [/COLOR]
[COLOR=#000000]Because of this problem, my laptop is only barely in a working state on WiFi -- it is hard to get work done or use the web in a reliable manner.[/COLOR]

[COLOR=#000000]Running the standard ubuntu forums wireless-info scripts gives the following:[/COLOR]
 [ATTACH]270581[/ATTACH]

Looking at logs via journalctl -f seems to suggests that the problem is related to a kernel fault in wl_event_handle (see stack trace below).

```
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel: ------------[ cut here ]------------
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel: WARNING: CPU: 2 PID: 677 at /home/kernel/COD/linux/net/w
ireless/sme.c:850 cfg80211_roamed+0x86/0xa0 [cfg80211]()
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel: Modules linked in: uas usb_storage cmac rfcomm pci_stub 
vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep nls_iso8859_1 wl(POE) uvcvideo videobuf2_vmallo
c videobuf2_memops videobuf2_v4l2 videobuf2_core kvm_amd kvm videodev btusb snd_hda_codec_realtek btrtl ir
qbypass media btbcm btintel snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hda_c
ore bluetooth crct10dif_pclmul snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event crc32_pclmul snd_rawmidi 
snd_seq hp_wmi snd_seq_device sparse_keymap ghash_clmulni_intel aesni_intel snd_timer snd aes_x86_64 lrw e
dac_mce_amd soundcore cfg80211 gf128mul glue_helper ablk_helper cryptd edac_core joydev input_leds k10temp
 fam15h_power serio_raw shpchp i2c_piix4 hp_wireless tpm_crb i2c_designware_platform i2c_designware_core
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  mac_hid 8250_dw parport_pc ppdev lp parport autofs4 amd
kfd amd_iommu_v2 amdgpu i2c_algo_bit ttm psmouse drm_kms_helper syscopyarea sysfillrect sdhci_pci sysimgbl
t fb_sys_fops sdhci ahci libahci drm r8169 mii wmi fjes video
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel: CPU: 2 PID: 677 Comm: wl_event_handle Tainted: P        
W  OE   4.5.7-040507-generic #201606100436
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel: Hardware name: HP HP Notebook/8221, BIOS F.05 05/05/2016
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  0000000000000286 0000000079d4cdf0 ffff8800dd8a7dc8 ffff
ffff813e1173
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  0000000000000000 ffffffffc03640e0 ffff8800dd8a7e00 ffff
ffff81080ff2
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  ffff8801f11d7000 ffff88009f413e40 00000000000000a3 ffff
88009f413d80
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel: Call Trace:
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  [<ffffffff813e1173>] dump_stack+0x63/0x90
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  [<ffffffff81080ff2>] warn_slowpath_common+0x82/0xc0
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  [<ffffffff8108113a>] warn_slowpath_null+0x1a/0x20
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  [<ffffffffc033f966>] cfg80211_roamed+0x86/0xa0 [cfg8021
1]
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  [<ffffffffc0838965>] wl_notify_roaming_status+0xc5/0x14
0 [wl]
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  [<ffffffffc0837fb0>] wl_event_handler+0x60/0x1e0 [wl]
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  [<ffffffffc0837f50>] ? wl_notify_scan_status+0x320/0x32
0 [wl]
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  [<ffffffff810a06a8>] kthread+0xd8/0xf0
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  [<ffffffff810a05d0>] ? kthread_create_on_node+0x1a0/0x1
a0
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  [<ffffffff81825bcf>] ret_from_fork+0x3f/0x70
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel:  [<ffffffff810a05d0>] ? kthread_create_on_node+0x1a0/0x1
a0
Aug 04 20:37:39 ndo885-HP-Notebook-6-2016 kernel: ---[ end trace c4267130c856d7a7 ]---
Aug 04 20:37:40 ndo885-HP-Notebook-6-2016 dhclient[12383]: DHCPDISCOVER on eno1:avahi to 255.255.255.255 p
ort 67 interval 10 (xid=0x6cdae14e)
Aug 04 20:37:40 ndo885-HP-Notebook-6-2016 dhclient[11017]: DHCPDISCOVER on eno1:avahi to 255.255.255.255 p
ort 67 interval 8 (xid=0x98c7e761)
Aug 04 20:37:40 ndo885-HP-Notebook-6-2016 dhclient[22642]: DHCPDISCOVER on eno1 to 255.255.255.255 port 67
 interval 3 (xid=0x10ef8076)
Aug 04 20:37:40 ndo885-HP-Notebook-6-2016 dhclient[17647]: DHCPDISCOVER on eno1 to 255.255.255.255 port 67
 interval 11 (xid=0xfbc60b)
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 dhclient[18737]: DHCPDISCOVER on eno1:avahi to 255.255.255.255 p
ort 67 interval 16 (xid=0xe81fff0e)
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 dhclient[27033]: DHCPDISCOVER on eno1 to 255.255.255.255 port 67
 interval 17 (xid=0xdec5e41f)
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 dhclient[776]: DHCPDISCOVER on eno1 to 255.255.255.255 port 67 i
nterval 8 (xid=0x609b6905)
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 wpa_supplicant[1859]: wlo1: CTRL-EVENT-SSID-REENABLED id=0 ssid=
"SASKTEL3453"
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 wpa_supplicant[1859]: wlo1: Trying to associate with 20:76:00:1a
:6e:28 (SSID='SASKTEL3453' freq=2442 MHz)
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 NetworkManager[7570]: <info>  [1470364661.7964] device (wlo1): s
upplicant interface state: scanning -> associating
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 wpa_supplicant[1859]: wlo1: Associated with 20:76:00:1a:6e:28
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 NetworkManager[7570]: <info>  [1470364661.8252] device (wlo1): s
upplicant interface state: associating -> associated
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 NetworkManager[7570]: <info>  [1470364661.8349] device (wlo1): s
upplicant interface state: associated -> 4-way handshake
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 wpa_supplicant[1859]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=COUNTR
Y_IE type=COUNTRY alpha2=CA
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 NetworkManager[7570]: <warn>  [1470364661.8792] device (wlo1): l
ink timed out.
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 NetworkManager[7570]: <info>  [1470364661.8793] device (wlo1): s
tate change: activated -> failed (reason 'supplicant-timeout') [100 120 11]
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 NetworkManager[7570]: <info>  [1470364661.8799] manager: Network
Manager state is now CONNECTED_LOCAL
Aug 04 20:37:41 ndo885-HP-Notebook-6-2016 whoopsie[837]: [20:37:41] offline

```


This is a major practical problem -- I would be deeply grateful for anyone who can help!

Sincerely,
Nathaniel Osgood

---

### Post by wildmanne39 on 2016-08-05
Thread closed. Please do not post duplicates, it dilutes community effort.

---


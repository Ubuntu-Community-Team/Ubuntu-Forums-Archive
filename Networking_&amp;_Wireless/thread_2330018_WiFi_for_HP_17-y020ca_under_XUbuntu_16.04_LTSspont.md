---
title: "WiFi for HP 17-y020ca under XUbuntu 16.04 LTSspontaneously disconnects very frequentl"
date: 2016-07-07
forum: Networking &amp; Wireless
---

### Post by Nathaniel_Osgood on 2016-07-07
[COLOR=#111111][FONT=Ubuntu]I recently purchased an HP Notebook 17-y020ca and installed XUbuntu 16.04. This notebook has a Broadcom Corporation BCM43142 wireless card.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This wireless card was not originally detected, and I followed the instructions at the following to install support using the bcmwl-kernel-source:
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][http://askubuntu.com/questions/76558...n-ubuntu-16-04]("http://askubuntu.com/questions/765584/is-it-possible-to-use-broadcom-bcm43142-wifi-in-ubuntu-16-04")
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After some futzing (resolved at [http://ubuntuforums.org/showthread.php?t=2329060](http://ubuntuforums.org/showthread.php?t=2329060))  the WiFi has been able to regularly detect networks and connect at least transiently.

[/FONT][/COLOR]However, I am encountering severe problems with the network disconnecting periodically on my home and certain other WiFi networks.  These disconnections occur every 1-4 minutes or so -- so frequently that it is hard to stay connected, and the laptop appears to spend more time disconnected than connected!  I am not yet certain if the problem occurs uniformly across all networks, but the problem certainly appears to occur in most networks.  Occasionally, I will be presented with a dialog box asking for the WPA/WPA2 network password (with the correct password already proposed), but this does not occur during most connections/reconnections.

Because of this problem, my laptop is only barely in a working state on WiFi -- it is hard to get work done or use the web in a reliable manner.

Running the standard ubuntu forums wireless-info scripts gives the following (pastebinned to the default pastebin provider)
[http://paste.ubuntu.com/18681683/](http://paste.ubuntu.com/18681683/)

Given that  this is a laptop which registers decent signal strength when connected, the problem seems to occur in close proximity to routers, and I therefore doubt any signal-strength issues.  
Poking around elsewhere, I tried the following:

```

sudo cat /var/log/syslog | grep -e ipw -e firmware -e wpa -e wlan -e etork | tail -n55

```

The command above returned the below, showing the disconnection events.  It seems worth noting the large number of disconnection (CTRL-EVENT-DISCONNECTED) and domain change (CTRL-EVENT-REGDOM-CHANGE) events, which are puzzling as they are not sought or caused by any change in networks caused by e.g., change in location.   
(Please note that because I was posting from the wireless network, and have found that resetting the network can sometimes be fruitful, it is possible that the below includes one manual disconnection, but this common sequence is seen when connected with many other networks/routers in different settings, and without manual disconnection. 


```



Jul  6 21:58:43 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-DISCONNECTED bssid=20:76:00:1a:6e:28 reason=3 locally_generated=1
Jul  6 21:58:43 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: nl80211: Was expecting local disconnect but got another disconnect event first
Jul  6 21:58:43 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jul  6 21:58:43 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: nl80211: deinit ifname=wlo1 disabled_11b_rates=0
Jul  6 21:58:48 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Jul  6 21:58:48 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: dbus: Failed to construct signal
Jul  6 21:58:49 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Trying to associate with 20:76:00:1a:6e:28 (SSID='SASKTEL3453' freq=2442 MHz)
Jul  6 21:58:49 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-ASSOC-REJECT bssid=20:76:00:1a:6e:28 status_code=16
Jul  6 21:58:50 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Trying to associate with 20:76:00:1a:6e:28 (SSID='SASKTEL3453' freq=2442 MHz)
Jul  6 21:58:50 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Associated with 20:76:00:1a:6e:28
Jul  6 21:58:50 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=CA
Jul  6 21:59:00 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Authentication with 20:76:00:1a:6e:28 timed out.
Jul  6 21:59:00 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-DISCONNECTED bssid=20:76:00:1a:6e:28 reason=3 locally_generated=1
Jul  6 21:59:00 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: nl80211: Was expecting local disconnect but got another disconnect event first
Jul  6 21:59:00 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jul  6 21:59:00 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Trying to associate with 20:76:00:1a:6e:28 (SSID='SASKTEL3453' freq=2442 MHz)
Jul  6 21:59:01 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-ASSOC-REJECT bssid=20:76:00:1a:6e:28 status_code=16
Jul  6 21:59:01 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="SASKTEL3453" auth_failures=1 duration=10 reason=CONN_FAILED
Jul  6 21:59:12 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-SSID-REENABLED id=0 ssid="SASKTEL3453"
Jul  6 21:59:12 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Trying to associate with 20:76:00:1a:6e:28 (SSID='SASKTEL3453' freq=2442 MHz)
Jul  6 21:59:12 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-ASSOC-REJECT bssid=20:76:00:1a:6e:28 status_code=16
Jul  6 21:59:12 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="SASKTEL3453" auth_failures=2 duration=20 reason=CONN_FAILED
Jul  6 21:59:14 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Trying to associate with 20:76:00:1a:6e:28 (SSID='SASKTEL3453' freq=2442 MHz)
Jul  6 21:59:14 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-ASSOC-REJECT bssid=20:76:00:1a:6e:28 status_code=16
Jul  6 21:59:14 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="SASKTEL3453" auth_failures=1 duration=10 reason=CONN_FAILED
Jul  6 21:59:25 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-SSID-REENABLED id=0 ssid="SASKTEL3453"
Jul  6 21:59:25 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Trying to associate with 20:76:00:1a:6e:28 (SSID='SASKTEL3453' freq=2442 MHz)
Jul  6 21:59:25 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Associated with 20:76:00:1a:6e:28
Jul  6 21:59:25 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: WPA: Key negotiation completed with 20:76:00:1a:6e:28 [PTK=CCMP GTK=TKIP]
Jul  6 21:59:25 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-CONNECTED - Connection to 20:76:00:1a:6e:28 completed [id=0 id_str=]
Jul  6 21:59:25 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=CA
Jul  6 22:12:44 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-DISCONNECTED bssid=20:76:00:1a:6e:28 reason=3 locally_generated=1
Jul  6 22:12:44 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: nl80211: Was expecting local disconnect but got another disconnect event first
Jul  6 22:12:45 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jul  6 22:12:45 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: nl80211: deinit ifname=wlo1 disabled_11b_rates=0
Jul  6 22:12:53 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Jul  6 22:12:53 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: dbus: Failed to construct signal
Jul  6 22:12:54 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Trying to associate with 20:76:00:1a:6e:28 (SSID='SASKTEL3453' freq=2442 MHz)
Jul  6 22:12:54 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-ASSOC-REJECT bssid=20:76:00:1a:6e:28 status_code=16
Jul  6 22:12:55 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Trying to associate with 20:76:00:1a:6e:28 (SSID='SASKTEL3453' freq=2442 MHz)
Jul  6 22:12:55 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Associated with 20:76:00:1a:6e:28
Jul  6 22:12:55 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=CA
Jul  6 22:13:05 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Authentication with 20:76:00:1a:6e:28 timed out.
Jul  6 22:13:05 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-DISCONNECTED bssid=20:76:00:1a:6e:28 reason=3 locally_generated=1
Jul  6 22:13:05 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: nl80211: Was expecting local disconnect but got another disconnect event first
Jul  6 22:13:05 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jul  6 22:13:06 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Trying to associate with 20:76:00:1a:6e:28 (SSID='SASKTEL3453' freq=2442 MHz)
Jul  6 22:13:06 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-ASSOC-REJECT bssid=20:76:00:1a:6e:28 status_code=16
Jul  6 22:13:06 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="SASKTEL3453" auth_failures=1 duration=10 reason=CONN_FAILED
Jul  6 22:13:17 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-SSID-REENABLED id=0 ssid="SASKTEL3453"
Jul  6 22:13:17 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Trying to associate with 20:76:00:1a:6e:28 (SSID='SASKTEL3453' freq=2442 MHz)
Jul  6 22:13:17 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: Associated with 20:76:00:1a:6e:28
Jul  6 22:13:17 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: WPA: Key negotiation completed with 20:76:00:1a:6e:28 [PTK=CCMP GTK=TKIP]
Jul  6 22:13:17 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-CONNECTED - Connection to 20:76:00:1a:6e:28 completed [id=0 id_str=]
Jul  6 22:13:17 ndo885-HP-Notebook-6-2016 wpa_supplicant[1042]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=CA



```

[COLOR=#111111][FONT=Ubuntu]I would be truly grateful for any suggestions that anyone could give. I much appreciate your consideration![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]

Sincerely,

Nathaniel Osgood
[/FONT][/COLOR]

---

### Post by souradeep100 on 2016-07-10
I am facing the same problem with broadcomm 43142 in ubuntu 16.04. 
I have tried the following:
1)Changing the auth in router to not to use tkip
2)made the wlan mode to b/g/n .
3)Disabling ipv6 through network manager.
4)sudo apt-get dist-upgrade
5)Installing latest broadcom-sta-dkms using synaptic package mananger instead of bcmwl kernel source.
6)changing the regulatory domain to my country. 
Still the problem happens . So you can  try these steps. Then check , if the problem persists.
For me the problem is still there.

---

### Post by souradeep_chakraba on 2016-07-19
I have finally found a  work around , that have a ping session open to 192.168.1.1 in a terminal and wifi connection is then stable. In my case 192.168.1.1 is my router ip address. So no problem in data usage and connection is solid and stable.

---

### Post by Nathaniel_Osgood on 2016-08-04
Thanks.  As it turns out, I had independently discovered the same ping trick.  This appeared to help much in terms of reducing the disconnections.

However, I am still experiencing very frequent disconnections -- as well as irregular ping timings to my local router (going from low milliseconds to hundreds times that).

Logs via journalctl -f seems to suggests that the problem is related to a kernel fault in wl_event_handle (see stack trace below).

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

This remains a major headache and practical problem.  Please see the following for the report for my machine from the wireless-info script:
  [ATTACH]270581[/ATTACH]

I would be deeply grateful for anyone who can help!

Sincerely,
Nathaniel Osgood

---

### Post by Nathaniel_Osgood on 2016-09-05
bump

---

### Post by praseodym on 2016-09-06
Try this driver:

[https://forum.ubuntuusers.de/topic/wlan-probleme-seit-neuer-o2-box-nur-unter-linu/2/#post-8031898](https://forum.ubuntuusers.de/topic/wlan-probleme-seit-neuer-o2-box-nur-unter-linu/2/#post-8031898)

Before: Uninstall the older one:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
```
Be sure having a LAN connection for the installation

---


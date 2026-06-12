---
title: "lspci - no network devices"
date: 2016-07-05
forum: Networking &amp; Wireless
---

### Post by bradleypariah on 2016-07-05
Hello, I have a Kangaroo (a mini desktop).  It came with Windows 10. I wiped it and installed 16.04.
No wireless devices are found during installation.

After install, when I run **lspci **from the terminal, there are no network devices listed.
This is not a BIOS issue, I checked to be sure.  Also, since I hadn't personalized Ubuntu yet, I wiped the PC again and put Win10 back just to check device manager.  See image at the bottom.
WiFi is enabled and working correctly out of the box.
Windows Device Manager recognizes it as a Broadcom SDIO adapter, but no specific model number is given.

I am reinstalling Ubuntu to begin troubleshooting again as we speak.  I do have a USB D-Link to use to download drivers/packages/etc.  I simply cannot keep it connected to this device.  The D-Link is needed on the desktop from which it came.  The Kangaroo clearly has WiFi, so I'd like to get its own connection working.  Any help would be greatly appreciated.

I of course started with the sticky: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
Again, **lspci ***doesn't yield results*.  See image below.

I have also tried:
[http://ubuntuforums.org/showthread.php?t=2317843&page=6&p=13495163#post13495163](http://ubuntuforums.org/showthread.php?t=2317843&page=6&p=13495163#post13495163)


[http://i6.photobucket.com/albums/y236/the_jerk/Untitled_zpsk021dzsw.png](http://i6.photobucket.com/albums/y236/the_jerk/Untitled_zpsk021dzsw.png)

[http://i6.photobucket.com/albums/y236/the_jerk/IMG_20160705_110709_zpsbyzjmkmb.jpg](http://i6.photobucket.com/albums/y236/the_jerk/IMG_20160705_110709_zpsbyzjmkmb.jpg)

---

### Post by X-RED_Tech on 2016-07-05
A SDIO device won't show up with lspci, different buses...
I'm not sure but not long ago this devices were simply not supported. I don't know if there was some progress. Nevertheless I can assure you the installation has nothing to do with traditional desktops/notebooks.

---

### Post by ajgreeny on 2016-07-05
Please do not use large images inline in your posts.  Some users still have slow connections and may not therefore wait for the post to show.

---

### Post by chili555 on 2016-07-05
Let's have a look at the message log. I suspect that your device is recognized and simply needs firmware. Please run and post:```
dmesg | grep brcm
```

---

### Post by bradleypariah on 2016-07-06
Sorry about the inline images, ajgreeny.

chili555, here is that output:
```
bradley@kangaroo:~$ dmesg | grep brcm
[    5.037451] brcmf_sdio_drivestrengthinit: No SDIO Drive strength init done for chip 4324 rev 5 pmurev 17
[    5.040163] usbcore: registered new interface driver brcmfmac
[    5.048456] brcmfmac_sdio mmc0:0001:1: Direct firmware load for brcm/brcmfmac43241b4-sdio.txt failed with error -2
[    6.053390] brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50
[    7.057345] brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50
bradley@kangaroo:~$ 

```

---

### Post by X-RED_Tech on 2016-07-06
Dr. Chili555 was right. It failed to load the firmware.
This means the typical SDIO WiFi of so many Bay Trail tablets is supported already and just a matter of loading the firmware?

---

### Post by chili555 on 2016-07-06
> **X-RED_Tech said:**
> Dr. Chili555 was right. It failed to load the firmware.
This means the typical SDIO WiFi of so many Bay Trail tablets is supported already and just a matter of loading the firmware?Probably. Let's try and see what happens.  If you otherwise have internet access, tethered, ethernet, etc., please open a terminal and do:```
cd /lib/firmware/brcm
sudo wget https://github.com/jfwells/linux-asus-t100ta/raw/master/nvram/lib/firmware/brcm/brcmfmac43241b4-sdio.txt
```If you haven't any internet access, download the file on any other computer, transfer it on a USB key or similar to the desktop and then:```
sudo cp ~/Desktop/brcmfmac43241b4-sdio.txt  /lib/firmware/brcm

```Now we need to edit the file:```
sudo gedit brcmfmac43241b4-sdio.txt
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the macaddr to the MAC address of your device. Is it on a sticker on the bottom? Is it available somewhere in the Device Manager as you showed us previously? Format the macaddr as in the existing file; that is 00:90:4c:cc:11:aa and not 00:90:4C:CC:11:AA, nor 00904ccc11aa, etc. Of course, substitute your details here.

Proofread carefully, save and close the text editor.
```
sudo modprobe -r brcmfmac && sudo modprobe brcmfmac
```Any improvement? 

May we see a new log?```
dmesg | grep brcm
```


----------------------
Reference: [http://ubuntuforums.org/showthread.php?t=2276504&page=2](http://ubuntuforums.org/showthread.php?t=2276504&page=2)

---

### Post by bradleypariah on 2016-07-06
Thank you!  :)

I found this:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I don't have my D-Link today, so I have to follow the "b43 - No Internet access" directions.
The releases mentioned on that page only go up to Trusty, though.  Do you possibly know if I have to modify those directions for Xenial?

---

### Post by bradleypariah on 2016-07-06
Oops, you replied as I was typing, chili555.

If it's going to be worlds easier to do this with my D-Link, I can just pick this up where we left off tomorrow.  I'll be happy either way.  Thank you so much for your time.

---

### Post by jeremy31 on 2016-07-06
Check ```
ls /sys/firmware/efi/efivars | grep nvram
``` and see if it shows nvram-74b00bd9-805a-4d61-b51f-43268123d113 as you may be able to use it

---

### Post by chili555 on 2016-07-06
> **bradleypariah said:**
> Thank you!  :)

I found this:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I don't have my D-Link today, so I have to follow the "b43 - No Internet access" directions.
The releases mentioned on that page only go up to Trusty, though.  Do you possibly know if I have to modify those directions for Xenial?Please note, from there:> brcmfmac driver (Open-source)
[COLOR="#FF0000"]SDIO[/COLOR]: For Chip ID BCM 4329, 4330, 4334, 4335, 4354, 43143, [COLOR="#FF0000"]43241[/COLOR], and 43362. 
USB: For Chip ID BCM 43143, 43242, 43566, and 43569. 

The open-source brcmfmac driver is available from the brcm80211 module of the linux kernel package, maintained upstream by the linux kernel community. For more granular support information, please see their wiki page here.

You have and are loading *brcmfmac*. As far as I can tell, you only need firmware and maybe a tweak or two.

> If it's going to be worlds easier to do this with my D-Link, Like Ike and Tina, I never do it nice and easy, I prefer nice and rough; meaning, let's get the proper internal device and driver working and if, after all of our skill and magical powers, just can't get it working, then we'll try another device.

---

### Post by bradleypariah on 2016-07-06
I formatted the PC, reinstalled Win10, ran **ipconfig /all**, grabbed my MAC address, reformatted, and I'm back to Ubuntu 16.04.

> **chili555 said:**
> Any improvement? 

May we see a new log?

Right after I finished your directions, the WiFi icon actually listed the networks in the building.  I put in the password for our network, but Ubuntu kept asking me for the password over and over again, and it wouldn't connect.

I rebooted, and now I don't see the local networks listed anymore.  I tried to run this command again:
```
sudo modprobe -r brcmfmac && sudo modprobe brcmfmac
```

But still no networks show.  I tried to add the credentials manually, but it didn't work.

Here's the new log:
```
bradley@kangaroo:~$ dmesg | grep brcm
[    3.695665] brcmf_sdio_drivestrengthinit: No SDIO Drive strength init done for chip 4324 rev 5 pmurev 17
[    3.696533] usbcore: registered new interface driver brcmfmac
[    3.908690] brcmf_c_preinit_dcmds: Firmware version = wl0: Jul 17 2013 07:36:07 version 6.10.197.71 (r412987) FWID 01-882d2634
[    5.420657] brcmf_cfg80211_reg_notifier: not a ISO3166 code
[    5.688701] brcmf_add_if: ERROR: netdev:wlan0 already exists
[    5.688709] brcmf_add_if: ignore IF event
[    7.737259] brcmf_sdio_bus_rxctl: resumed on timeout
[    7.737270] brcmf_dongle_scantime: Scan passive time error (-52)
[   10.201315] brcmf_sdio_bus_rxctl: resumed on timeout
[   10.205159] brcmf_add_if: ERROR: netdev:wlan0 already exists
[   10.205215] brcmf_add_if: ignore IF event
[   12.573367] brcmf_sdio_bus_rxctl: resumed on timeout
[   12.573380] brcmf_run_escan: error (-52)
[   12.573387] brcmf_cfg80211_scan: scan error (-52)
[   14.061332] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   14.061344] brcmf_fweh_event_worker: event handler failed (69)
[   14.061464] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   14.061470] brcmf_fweh_event_worker: event handler failed (69)
[   14.061586] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   14.061592] brcmf_fweh_event_worker: event handler failed (69)
[   14.089051] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   14.089058] brcmf_fweh_event_worker: event handler failed (69)
[   14.089170] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   14.089173] brcmf_fweh_event_worker: event handler failed (69)
[   14.112986] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   14.112994] brcmf_fweh_event_worker: event handler failed (69)
[   14.113095] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   14.113099] brcmf_fweh_event_worker: event handler failed (69)
[   39.037906] brcmf_sdio_bus_rxctl: resumed on timeout
[   39.037921] brcmf_run_escan: error (-52)
[   39.037927] brcmf_cfg80211_scan: scan error (-52)
[   72.066570] brcmf_sdio_bus_rxctl: resumed on timeout
[   72.066582] brcmf_run_escan: error (-52)
[   72.066588] brcmf_cfg80211_scan: scan error (-52)
[   73.049585] WARNING: driver brcmfmac_sdio did not remove its interrupt handler!
[   73.053141] brcmf_sdio_dpc: failed backplane access over SDIO, halting operation
[   73.650680] usbcore: deregistering interface driver brcmfmac
[   73.917294] brcmf_sdio_drivestrengthinit: No SDIO Drive strength init done for chip 4324 rev 5 pmurev 17
[   73.917699] usbcore: registered new interface driver brcmfmac
[   74.122002] brcmf_c_preinit_dcmds: Firmware version = wl0: Jul 17 2013 07:36:07 version 6.10.197.71 (r412987) FWID 01-882d2634
[   75.650633] brcmf_cfg80211_reg_notifier: not a ISO3166 code
[   75.899125] brcmf_add_if: ERROR: netdev:wlan0 already exists
[   75.899136] brcmf_add_if: ignore IF event
[   77.974688] brcmf_sdio_bus_rxctl: resumed on timeout
[   77.974699] brcmf_netdev_open: failed to bring up cfg80211
[   78.114976] brcmf_add_if: ERROR: netdev:wlan0 already exists
[   78.114984] brcmf_add_if: ignore IF event
[   78.570888] brcmf_add_if: ERROR: netdev:wlan0 already exists
[   78.570896] brcmf_add_if: ignore IF event
[   80.646740] brcmf_sdio_bus_rxctl: resumed on timeout
[   80.646751] brcmf_p2p_create_p2pdev: retrieving discover bsscfg index failed
[   82.654775] brcmf_sdio_bus_rxctl: resumed on timeout
[   82.654787] brcmf_run_escan: error (-52)
[   82.654794] brcmf_cfg80211_scan: scan error (-52)
[   84.062559] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   84.062570] brcmf_fweh_event_worker: event handler failed (69)
[   84.062937] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   84.062943] brcmf_fweh_event_worker: event handler failed (69)
[   84.063051] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   84.063056] brcmf_fweh_event_worker: event handler failed (69)
[   84.063182] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   84.063188] brcmf_fweh_event_worker: event handler failed (69)
[   84.063309] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   84.063314] brcmf_fweh_event_worker: event handler failed (69)
[   84.090529] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   84.090537] brcmf_fweh_event_worker: event handler failed (69)
[   84.090704] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   84.090712] brcmf_fweh_event_worker: event handler failed (69)
[   84.090856] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   84.090865] brcmf_fweh_event_worker: event handler failed (69)
[  109.063313] brcmf_sdio_bus_rxctl: resumed on timeout
[  109.063324] brcmf_run_escan: error (-52)
[  109.063330] brcmf_cfg80211_scan: scan error (-52)
[  142.051969] brcmf_sdio_bus_rxctl: resumed on timeout
[  142.051980] brcmf_run_escan: error (-52)
[  142.051986] brcmf_cfg80211_scan: scan error (-52)
[  185.040831] brcmf_sdio_bus_rxctl: resumed on timeout
[  185.040850] brcmf_run_escan: error (-52)
[  185.040856] brcmf_cfg80211_scan: scan error (-52)
[  238.093889] brcmf_sdio_bus_rxctl: resumed on timeout
[  238.093901] brcmf_run_escan: error (-52)
[  238.093907] brcmf_cfg80211_scan: scan error (-52)
[  301.051156] brcmf_sdio_bus_rxctl: resumed on timeout
[  301.051168] brcmf_run_escan: error (-52)
[  301.051174] brcmf_cfg80211_scan: scan error (-52)
[  364.100417] brcmf_sdio_bus_rxctl: resumed on timeout
[  364.100429] brcmf_run_escan: error (-52)
[  364.100434] brcmf_cfg80211_scan: scan error (-52)
[  427.053671] brcmf_sdio_bus_rxctl: resumed on timeout
[  427.053694] brcmf_run_escan: error (-52)
[  427.053704] brcmf_cfg80211_scan: scan error (-52)
[  490.050873] brcmf_sdio_bus_rxctl: resumed on timeout
[  490.050895] brcmf_run_escan: error (-52)
[  490.050905] brcmf_cfg80211_scan: scan error (-52)
[  553.108212] brcmf_sdio_bus_rxctl: resumed on timeout
[  553.108223] brcmf_run_escan: error (-52)
[  553.108229] brcmf_cfg80211_scan: scan error (-52)
[  616.057480] brcmf_sdio_bus_rxctl: resumed on timeout
[  616.057491] brcmf_run_escan: error (-52)
[  616.057498] brcmf_cfg80211_scan: scan error (-52)
[  679.054739] brcmf_sdio_bus_rxctl: resumed on timeout
[  679.054750] brcmf_run_escan: error (-52)
[  679.054756] brcmf_cfg80211_scan: scan error (-52)
[  742.115997] brcmf_sdio_bus_rxctl: resumed on timeout
[  742.116008] brcmf_run_escan: error (-52)
[  742.116015] brcmf_cfg80211_scan: scan error (-52)
[  805.057267] brcmf_sdio_bus_rxctl: resumed on timeout
[  805.057279] brcmf_run_escan: error (-52)
[  805.057285] brcmf_cfg80211_scan: scan error (-52)
[  868.114532] brcmf_sdio_bus_rxctl: resumed on timeout
[  868.114543] brcmf_run_escan: error (-52)
[  868.114549] brcmf_cfg80211_scan: scan error (-52)
[  931.059708] brcmf_sdio_bus_rxctl: resumed on timeout
[  931.059720] brcmf_run_escan: error (-52)
[  931.059725] brcmf_cfg80211_scan: scan error (-52)
[  994.117058] brcmf_sdio_bus_rxctl: resumed on timeout
[  994.117070] brcmf_run_escan: error (-52)
[  994.117075] brcmf_cfg80211_scan: scan error (-52)
[ 1057.122323] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1057.122334] brcmf_run_escan: error (-52)
[ 1057.122341] brcmf_cfg80211_scan: scan error (-52)
[ 1120.095587] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1120.095599] brcmf_run_escan: error (-52)
[ 1120.095604] brcmf_cfg80211_scan: scan error (-52)
[ 1183.124854] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1183.124866] brcmf_run_escan: error (-52)
[ 1183.124873] brcmf_cfg80211_scan: scan error (-52)
[ 1246.066109] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1246.066121] brcmf_run_escan: error (-52)
[ 1246.066127] brcmf_cfg80211_scan: scan error (-52)
[ 1309.123377] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1309.123389] brcmf_run_escan: error (-52)
[ 1309.123395] brcmf_cfg80211_scan: scan error (-52)
[ 1372.108577] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1372.108588] brcmf_run_escan: error (-52)
[ 1372.108595] brcmf_cfg80211_scan: scan error (-52)
[ 1435.073911] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1435.073922] brcmf_run_escan: error (-52)
[ 1435.073928] brcmf_cfg80211_scan: scan error (-52)
[ 1498.071168] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1498.071180] brcmf_run_escan: error (-52)
[ 1498.071186] brcmf_cfg80211_scan: scan error (-52)
[ 1561.124436] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1561.124447] brcmf_run_escan: error (-52)
[ 1561.124454] brcmf_cfg80211_scan: scan error (-52)
[ 1606.895683] WARNING: driver brcmfmac_sdio did not remove its interrupt handler!
[ 1606.896072] IP: [<ffffffffc06b1d11>] brcmf_fil_bsscfg_data_set+0x21/0x150 [brcmfmac]
[ 1606.896163] Modules linked in: brcmfmac(-) brcmutil cfg80211 rtsx_usb_sdmmc rtsx_usb_ms memstick rtsx_usb input_leds joydev hid_multitouch hid_generic usbhid hid snd_soc_sst_broadwell snd_soc_sst_haswell_pcm nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp uas snd_soc_sst_ipc snd_soc_sst_dsp usb_storage kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_soc_rt286 snd_soc_rl6347a snd_hda_codec_hdmi snd_soc_core snd_compress serio_raw snd_hda_intel snd_hda_codec ac97_bus snd_pcm_dmaengine snd_hda_core snd_hwdep snd_pcm mei_me snd_seq_midi snd_seq_midi_event mei snd_rawmidi lpc_ich snd_seq snd_seq_device snd_timer snd 8250_fintek soundcore spi_pxa2xx_platform dw_dmac i2c_designware_platform 8250_dw snd_soc_sst_acpi
[ 1606.896655]  i2c_designware_core tpm_crb dw_dmac_core acpi_pad mac_hid parport_pc ppdev lp parport autofs4 mmc_block i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse drm ahci libahci wmi video sdhci_acpi sdhci fjes [last unloaded: brcmutil]
[ 1606.896943] RIP: 0010:[<ffffffffc06b1d11>]  [<ffffffffc06b1d11>] brcmf_fil_bsscfg_data_set+0x21/0x150 [brcmfmac]
[ 1606.897600]  [<ffffffffc06b56ed>] brcmf_p2p_set_discover_state+0x6d/0x90 [brcmfmac]
[ 1606.897648]  [<ffffffffc06b58fc>] brcmf_p2p_deinit_discovery.isra.7+0x3c/0x60 [brcmfmac]
[ 1606.897698]  [<ffffffffc06b839e>] brcmf_p2p_detach+0x2e/0x70 [brcmfmac]
[ 1606.897740]  [<ffffffffc06baa76>] brcmf_detach+0x56/0xe0 [brcmfmac]
[ 1606.897782]  [<ffffffffc06c56b2>] brcmf_sdio_remove+0x42/0x110 [brcmfmac]
[ 1606.897826]  [<ffffffffc06c6805>] brcmf_sdiod_remove+0x25/0xc0 [brcmfmac]
[ 1606.897869]  [<ffffffffc06c6949>] brcmf_ops_sdio_remove+0xa9/0x100 [brcmfmac]
[ 1606.898126]  [<ffffffffc06c8815>] brcmf_sdio_exit+0x45/0x50 [brcmfmac]
[ 1606.898169]  [<ffffffffc06ced4d>] brcmfmac_module_exit+0x15/0x2c8 [brcmfmac]
[ 1606.898485] RIP  [<ffffffffc06b1d11>] brcmf_fil_bsscfg_data_set+0x21/0x150 [brcmfmac]
[ 1606.918280] brcmf_sdio_dpc: failed backplane access over SDIO, halting operation
[ 1622.120100] brcmf_do_escan: error (-52)
[ 1622.120108] brcmf_cfg80211_scan: scan error (-52)
[ 1658.507269] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1658.507277] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1658.507280] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1658.516504] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1658.516516] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1658.516522] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1658.529074] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1658.529130] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1658.529138] brcmf_cfg80211_get_tx_power: error (-52)
[ 1658.529184] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1658.529189] brcmf_cfg80211_get_tx_power: error (-52)
[ 1658.529911] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1658.529921] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1658.529927] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1659.030628] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1659.130850] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1659.231108] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1659.331363] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1659.431692] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1659.531985] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1659.632258] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1659.732595] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1659.832916] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1659.933238] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1660.033477] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1660.033558] brcmf_cfg80211_set_power_mgmt: error (-52)
[ 1660.034127] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1660.034137] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1660.034143] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1660.134580] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1660.134632] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1660.134639] brcmf_cfg80211_get_tx_power: error (-52)
[ 1660.134680] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1660.134686] brcmf_cfg80211_get_tx_power: error (-52)
[ 1660.134756] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1660.134762] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1660.134768] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1660.638651] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1660.738896] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1660.839219] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1660.939478] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1661.039805] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1661.140070] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1661.240399] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1661.340643] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1661.440927] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1661.541261] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1661.641462] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1661.641542] brcmf_cfg80211_set_power_mgmt: error (-52)
[ 1661.642070] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1661.642078] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1661.642084] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1662.142955] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1662.143003] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1662.143008] brcmf_cfg80211_get_tx_power: error (-52)
[ 1662.143033] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1662.143036] brcmf_cfg80211_get_tx_power: error (-52)
[ 1662.143094] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1662.143097] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1662.143101] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1662.646652] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1662.746992] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1662.847236] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1662.947513] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1663.047839] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1663.148126] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1663.248314] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1663.348475] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1663.448686] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1663.548912] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1663.649053] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1663.649135] brcmf_cfg80211_set_power_mgmt: error (-52)
[ 1663.649630] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1663.649638] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1663.649643] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1664.650903] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1664.650953] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1664.650961] brcmf_cfg80211_get_tx_power: error (-52)
[ 1664.650999] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1664.651005] brcmf_cfg80211_get_tx_power: error (-52)
[ 1664.651075] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1664.651082] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1664.651088] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1665.154634] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1665.254964] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1665.355222] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1665.455549] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1665.555826] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1665.656153] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1665.756432] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1665.856761] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1665.957090] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1666.057312] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1666.157552] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1666.157637] brcmf_cfg80211_set_power_mgmt: error (-52)
[ 1666.158169] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1666.158178] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1666.158184] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1671.163113] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1671.163164] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1671.163171] brcmf_cfg80211_get_tx_power: error (-52)
[ 1671.163210] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1671.163216] brcmf_cfg80211_get_tx_power: error (-52)
[ 1671.163286] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1671.163293] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1671.163299] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1671.666752] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1671.766987] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1671.867216] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1671.967446] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1672.067672] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1672.167945] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1672.268305] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1672.368675] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1672.469055] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1672.569290] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1672.669430] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1672.669510] brcmf_cfg80211_set_power_mgmt: error (-52)
[ 1672.670071] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1672.670081] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1672.670087] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1682.680425] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1682.680470] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1682.680477] brcmf_cfg80211_get_tx_power: error (-52)
[ 1682.680512] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1682.680516] brcmf_cfg80211_get_tx_power: error (-52)
[ 1682.680570] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1682.680574] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1682.680577] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1683.182998] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1683.283200] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1683.383423] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1683.483660] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1683.583919] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1683.684174] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1683.784471] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1683.884682] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1683.984960] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1684.085213] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1684.185409] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1684.185491] brcmf_cfg80211_set_power_mgmt: error (-52)
[ 1684.186704] brcmf_do_escan: error (-52)
[ 1684.186713] brcmf_cfg80211_scan: scan error (-52)
[ 1684.186932] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1684.186941] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1684.186947] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1687.061967] brcmf_do_escan: error (-52)
[ 1687.061975] brcmf_cfg80211_scan: scan error (-52)
[ 1707.019397] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1707.019403] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1707.019406] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1707.031223] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1707.031234] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1707.031238] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1707.043812] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1707.043849] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1707.043855] brcmf_cfg80211_get_tx_power: error (-52)
[ 1707.043888] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1707.043892] brcmf_cfg80211_get_tx_power: error (-52)
[ 1707.043947] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1707.043952] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1707.043956] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1707.547495] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1707.647735] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1707.747976] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1707.848236] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1707.948518] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1708.048803] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1708.149015] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1708.249222] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1708.349536] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1708.449750] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1708.549880] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1708.549949] brcmf_cfg80211_set_power_mgmt: error (-52)
[ 1708.550449] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1708.550457] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1708.550463] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1718.555786] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1718.555816] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1718.555821] brcmf_cfg80211_get_tx_power: error (-52)
[ 1718.555857] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1718.555860] brcmf_cfg80211_get_tx_power: error (-52)
[ 1718.555900] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1718.555904] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1718.555908] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1719.059719] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1719.160106] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1719.260540] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1719.361028] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1719.461317] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1719.561625] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1719.661934] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1719.762176] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1719.862418] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1719.962673] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1720.062827] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1720.062868] brcmf_cfg80211_set_power_mgmt: error (-52)
[ 1720.063164] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1720.063168] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1720.063171] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1730.068258] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1730.068307] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1730.068314] brcmf_cfg80211_get_tx_power: error (-52)
[ 1730.068353] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1730.068358] brcmf_cfg80211_get_tx_power: error (-52)
[ 1730.068432] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1730.068439] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1730.068445] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1730.571959] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1730.672284] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1730.772612] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1730.872943] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1730.973217] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1731.073427] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1731.173651] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1731.273881] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1731.374319] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1731.474720] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1731.574865] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1731.574951] brcmf_cfg80211_set_power_mgmt: error (-52)
[ 1731.575370] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1731.575375] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1731.575379] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1732.067470] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1732.067481] brcmf_cfg80211_get_tx_power: error (-52)
[ 1732.071833] brcmf_do_escan: error (-52)
[ 1732.071844] brcmf_cfg80211_scan: scan error (-52)
[ 1735.063294] brcmf_do_escan: error (-52)
[ 1735.063303] brcmf_cfg80211_scan: scan error (-52)
[ 1753.575117] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1753.575122] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1753.575123] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1753.582595] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1753.582603] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1753.582607] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1753.598255] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1753.598346] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1753.598353] brcmf_cfg80211_get_tx_power: error (-52)
[ 1753.598416] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1753.598423] brcmf_cfg80211_get_tx_power: error (-52)
[ 1753.598574] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1753.598581] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1753.598585] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1754.100445] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1754.200694] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1754.300925] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1754.401179] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1754.501380] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1754.601585] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1754.701900] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1754.802136] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1754.902532] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1755.002961] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1755.103090] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1755.103134] brcmf_cfg80211_set_power_mgmt: error (-52)
[ 1755.103531] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1755.103536] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1755.103538] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1765.105034] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1765.105083] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1765.105090] brcmf_cfg80211_get_tx_power: error (-52)
[ 1765.105129] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1765.105135] brcmf_cfg80211_get_tx_power: error (-52)
[ 1765.105206] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1765.105212] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1765.105217] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1765.609093] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1765.709533] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1765.809874] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1765.910080] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1766.010298] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1766.110539] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1766.210715] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1766.310918] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1766.411079] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1766.511317] brcmf_cfg80211_change_iface: iface validation failed: err=-16
[ 1766.611442] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1766.611524] brcmf_cfg80211_set_power_mgmt: error (-52)
[ 1766.613590] _brcmf_set_multicast_list: Setting mcast_list failed, -52
[ 1766.613600] _brcmf_set_multicast_list: Setting allmulti failed, -52
[ 1766.613604] _brcmf_set_multicast_list: Setting BRCMF_C_SET_PROMISC failed, -52
[ 1772.185710] brcmf_proto_bcdc_query_dcmd: brcmf_proto_bcdc_msg failed w/status -5
[ 1772.185717] brcmf_cfg80211_get_tx_power: error (-52)
[ 1772.196790] brcmf_do_escan: error (-52)
[ 1772.196798] brcmf_cfg80211_scan: scan error (-52)
[ 1775.064161] brcmf_do_escan: error (-52)
[ 1775.064173] brcmf_cfg80211_scan: scan error (-52)
bradley@kangaroo:~$ 


```

---

### Post by bradleypariah on 2016-07-06
> **chili555 said:**
> Format the macaddr as in the existing file; that is 00:90:4c:cc:11:aa and not 00:90:4C:CC:11:AA, nor 00904ccc11aa, etc. Of course, substitute your details here.

I misread that the first time.  I changed the dashes to colons, but I left the upper-case letters as-is.  After changing the MAC address to all lower-case letters, I can now consistently scan for WiFi networks if I attempt to join a hidden one first.  To reiterate, upon boot, the WiFi icon doesn't find any WiFi networks, but if I click Connect to a Hidden Network, the scan begins.

All that said, I still cannot successfully connect to any network.  I have tried our corporate WiFi and a small router, both to no avail.  I re-ran the logs under these new conditions.  Thank you again for your help! :)

```
bradley@kangaroo:~$ dmesg | grep brcm
[    4.995717] brcmf_sdio_drivestrengthinit: No SDIO Drive strength init done for chip 4324 rev 5 pmurev 17
[    5.000009] usbcore: registered new interface driver brcmfmac
[    5.187514] brcmf_c_preinit_dcmds: Firmware version = wl0: Jul 17 2013 07:36:07 version 6.10.197.71 (r412987) FWID 01-882d2634
[    6.738582] brcmf_cfg80211_reg_notifier: not a ISO3166 code
[    7.014611] brcmf_add_if: ERROR: netdev:wlan0 already exists
[    7.014618] brcmf_add_if: ignore IF event
[    9.087063] brcmf_sdio_bus_rxctl: resumed on timeout
[    9.087075] brcmf_netdev_open: failed to bring up cfg80211
[    9.202938] brcmf_add_if: ERROR: netdev:wlan0 already exists
[    9.202947] brcmf_add_if: ignore IF event
[   11.647100] brcmf_sdio_bus_rxctl: resumed on timeout
[   11.651184] brcmf_add_if: ERROR: netdev:wlan0 already exists
[   11.651195] brcmf_add_if: ignore IF event
[   13.979140] brcmf_sdio_bus_rxctl: resumed on timeout
[   13.979151] brcmf_run_escan: error (-52)
[   13.979158] brcmf_cfg80211_scan: scan error (-52)
[   15.062676] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   15.062688] brcmf_fweh_event_worker: event handler failed (69)
[   15.062782] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   15.062788] brcmf_fweh_event_worker: event handler failed (69)
[   15.062895] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   15.062901] brcmf_fweh_event_worker: event handler failed (69)
[   15.063271] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   15.063276] brcmf_fweh_event_worker: event handler failed (69)
[   15.087033] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   15.087041] brcmf_fweh_event_worker: event handler failed (69)
[   15.087293] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   15.087300] brcmf_fweh_event_worker: event handler failed (69)
[   15.087389] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   15.087394] brcmf_fweh_event_worker: event handler failed (69)
[   15.087502] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   15.087505] brcmf_fweh_event_worker: event handler failed (69)
[   40.031435] brcmf_sdio_bus_rxctl: resumed on timeout
[   40.031447] brcmf_run_escan: error (-52)
[   40.031453] brcmf_cfg80211_scan: scan error (-52)
[   56.593511] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.593520] brcmf_fweh_event_worker: event handler failed (69)
[   56.593591] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.593595] brcmf_fweh_event_worker: event handler failed (69)
[   56.594441] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.594446] brcmf_fweh_event_worker: event handler failed (69)
[   56.594533] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.594536] brcmf_fweh_event_worker: event handler failed (69)
[   56.594777] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.594782] brcmf_fweh_event_worker: event handler failed (69)
[   56.595029] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.595033] brcmf_fweh_event_worker: event handler failed (69)
[   56.595272] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.595277] brcmf_fweh_event_worker: event handler failed (69)
[   56.595527] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.595533] brcmf_fweh_event_worker: event handler failed (69)
[   56.596672] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.596679] brcmf_fweh_event_worker: event handler failed (69)
[   56.596916] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.596921] brcmf_fweh_event_worker: event handler failed (69)
[   56.597166] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.597171] brcmf_fweh_event_worker: event handler failed (69)
[   56.597246] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.597249] brcmf_fweh_event_worker: event handler failed (69)
[   56.597497] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.597502] brcmf_fweh_event_worker: event handler failed (69)
[   56.597734] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.597739] brcmf_fweh_event_worker: event handler failed (69)
[   56.597975] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.597980] brcmf_fweh_event_worker: event handler failed (69)
[   56.598221] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.598225] brcmf_fweh_event_worker: event handler failed (69)
[   56.598309] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.598314] brcmf_fweh_event_worker: event handler failed (69)
[   56.598546] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.598550] brcmf_fweh_event_worker: event handler failed (69)
[   56.598804] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.598825] brcmf_fweh_event_worker: event handler failed (69)
[   56.598896] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.598900] brcmf_fweh_event_worker: event handler failed (69)
[   56.599138] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.599143] brcmf_fweh_event_worker: event handler failed (69)
[   56.599388] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.599407] brcmf_fweh_event_worker: event handler failed (69)
[   56.599479] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.599483] brcmf_fweh_event_worker: event handler failed (69)
[   56.600830] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.600857] brcmf_fweh_event_worker: event handler failed (69)
[   56.601114] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.601119] brcmf_fweh_event_worker: event handler failed (69)
[   56.601218] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.601222] brcmf_fweh_event_worker: event handler failed (69)
[   56.601316] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.601319] brcmf_fweh_event_worker: event handler failed (69)
[   56.601413] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.601417] brcmf_fweh_event_worker: event handler failed (69)
[   56.601511] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.601515] brcmf_fweh_event_worker: event handler failed (69)
[   56.601687] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.601709] brcmf_fweh_event_worker: event handler failed (69)
[   56.601794] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.601813] brcmf_fweh_event_worker: event handler failed (69)
[   56.601893] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.601911] brcmf_fweh_event_worker: event handler failed (69)
[   56.602005] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.602028] brcmf_fweh_event_worker: event handler failed (69)
[   56.602120] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.602124] brcmf_fweh_event_worker: event handler failed (69)
[   56.602221] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.602225] brcmf_fweh_event_worker: event handler failed (69)
[   56.602321] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.602325] brcmf_fweh_event_worker: event handler failed (69)
[   56.602420] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.602424] brcmf_fweh_event_worker: event handler failed (69)
[   56.602517] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.602536] brcmf_fweh_event_worker: event handler failed (69)
[   56.602617] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.602621] brcmf_fweh_event_worker: event handler failed (69)
[   56.602717] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.602737] brcmf_fweh_event_worker: event handler failed (69)
[   56.602818] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.602822] brcmf_fweh_event_worker: event handler failed (69)
[   56.602918] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.602938] brcmf_fweh_event_worker: event handler failed (69)
[   56.603019] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.603023] brcmf_fweh_event_worker: event handler failed (69)
[   56.603118] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.603122] brcmf_fweh_event_worker: event handler failed (69)
[   56.603219] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.603238] brcmf_fweh_event_worker: event handler failed (69)
[   56.603314] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.603318] brcmf_fweh_event_worker: event handler failed (69)
[   56.603405] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.603409] brcmf_fweh_event_worker: event handler failed (69)
[   56.603504] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.603508] brcmf_fweh_event_worker: event handler failed (69)
[   56.603598] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.603602] brcmf_fweh_event_worker: event handler failed (69)
[   56.608485] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.608516] brcmf_fweh_event_worker: event handler failed (69)
[   56.608621] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.608643] brcmf_fweh_event_worker: event handler failed (69)
[   56.608733] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.608754] brcmf_fweh_event_worker: event handler failed (69)
[   56.608841] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.608846] brcmf_fweh_event_worker: event handler failed (69)
[   56.608963] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.608985] brcmf_fweh_event_worker: event handler failed (69)
[   56.609071] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.609091] brcmf_fweh_event_worker: event handler failed (69)
[   56.609179] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.609202] brcmf_fweh_event_worker: event handler failed (69)
[   56.609290] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.609310] brcmf_fweh_event_worker: event handler failed (69)
[   56.609393] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.609415] brcmf_fweh_event_worker: event handler failed (69)
[   56.609502] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.609523] brcmf_fweh_event_worker: event handler failed (69)
[   56.609610] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.609631] brcmf_fweh_event_worker: event handler failed (69)
[   56.609716] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.609738] brcmf_fweh_event_worker: event handler failed (69)
[   56.609824] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.609828] brcmf_fweh_event_worker: event handler failed (69)
[   56.609929] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.609950] brcmf_fweh_event_worker: event handler failed (69)
[   56.610038] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.610060] brcmf_fweh_event_worker: event handler failed (69)
[   56.610150] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.610171] brcmf_fweh_event_worker: event handler failed (69)
[   56.610259] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.610280] brcmf_fweh_event_worker: event handler failed (69)
[   56.610535] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.610556] brcmf_fweh_event_worker: event handler failed (69)
[   56.610637] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.610658] brcmf_fweh_event_worker: event handler failed (69)
[   56.610743] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.610763] brcmf_fweh_event_worker: event handler failed (69)
[   56.610850] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.610870] brcmf_fweh_event_worker: event handler failed (69)
[   56.610954] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.610975] brcmf_fweh_event_worker: event handler failed (69)
[   56.611145] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.611150] brcmf_fweh_event_worker: event handler failed (69)
[   56.611253] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.611274] brcmf_fweh_event_worker: event handler failed (69)
[   56.611358] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.611379] brcmf_fweh_event_worker: event handler failed (69)
[   56.611469] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.611474] brcmf_fweh_event_worker: event handler failed (69)
[   56.611577] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.611597] brcmf_fweh_event_worker: event handler failed (69)
[   56.611716] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.611732] brcmf_fweh_event_worker: event handler failed (69)
[   56.611821] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.611841] brcmf_fweh_event_worker: event handler failed (69)
[   56.611924] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.611929] brcmf_fweh_event_worker: event handler failed (69)
[   56.612131] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   56.612137] brcmf_fweh_event_worker: event handler failed (69)
[   58.751815] brcmf_sdio_bus_rxctl: resumed on timeout
[   58.751826] brcmf_run_escan: error (-52)
[   58.751833] brcmf_cfg80211_scan: scan error (-52)
[   59.787751] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.787761] brcmf_fweh_event_worker: event handler failed (69)
[   59.787945] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.787951] brcmf_fweh_event_worker: event handler failed (69)
[   59.788035] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.788040] brcmf_fweh_event_worker: event handler failed (69)
[   59.796170] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.796176] brcmf_fweh_event_worker: event handler failed (69)
[   59.796303] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.796307] brcmf_fweh_event_worker: event handler failed (69)
[   59.823276] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.823285] brcmf_fweh_event_worker: event handler failed (69)
[   59.823395] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.823399] brcmf_fweh_event_worker: event handler failed (69)
[   59.823502] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.823505] brcmf_fweh_event_worker: event handler failed (69)
[   59.823610] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.823613] brcmf_fweh_event_worker: event handler failed (69)
[   59.823963] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.823970] brcmf_fweh_event_worker: event handler failed (69)
[   59.899395] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.899406] brcmf_fweh_event_worker: event handler failed (69)
[   59.947186] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[   59.947195] brcmf_fweh_event_worker: event handler failed (69)
[   70.056130] brcmf_cfg80211_escan: Connecting: status (3)
[   70.056140] brcmf_cfg80211_scan: scan error (-11)
[   71.057711] brcmf_cfg80211_escan: Connecting: status (3)
[   71.057720] brcmf_cfg80211_scan: scan error (-11)
[   72.058386] brcmf_cfg80211_escan: Connecting: status (3)
[   72.058396] brcmf_cfg80211_scan: scan error (-11)
[   73.060012] brcmf_cfg80211_escan: Connecting: status (3)
[   73.060021] brcmf_cfg80211_scan: scan error (-11)
[   74.061587] brcmf_cfg80211_escan: Connecting: status (3)
[   74.061599] brcmf_cfg80211_scan: scan error (-11)
[   75.063167] brcmf_cfg80211_escan: Connecting: status (3)
[   75.063176] brcmf_cfg80211_scan: scan error (-11)
[   76.064792] brcmf_cfg80211_escan: Connecting: status (3)
[   76.064808] brcmf_cfg80211_scan: scan error (-11)
[   77.066513] brcmf_cfg80211_escan: Connecting: status (3)
[   77.066526] brcmf_cfg80211_scan: scan error (-11)
[   78.068307] brcmf_cfg80211_escan: Connecting: status (3)
[   78.068318] brcmf_cfg80211_scan: scan error (-11)
[   79.069844] brcmf_cfg80211_escan: Connecting: status (3)
[   79.069853] brcmf_cfg80211_scan: scan error (-11)
[   80.070409] brcmf_cfg80211_escan: Connecting: status (3)
[   80.070417] brcmf_cfg80211_scan: scan error (-11)
[   81.072024] brcmf_cfg80211_escan: Connecting: status (3)
[   81.072033] brcmf_cfg80211_scan: scan error (-11)
[  107.243913] Modules linked in: rtsx_usb_ms memstick nls_iso8859_1 snd_soc_sst_broadwell intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_soc_sst_haswell_pcm coretemp snd_soc_sst_ipc kvm_intel snd_soc_sst_dsp kvm irqbypass crct10dif_pclmul crc32_pclmul aesni_intel hid_multitouch aes_x86_64 lrw gf128mul glue_helper brcmfmac ablk_helper cryptd brcmutil snd_soc_rt286 snd_hda_codec_hdmi input_leds joydev snd_soc_rl6347a cfg80211 snd_soc_core snd_hda_intel snd_hda_codec serio_raw snd_hda_core snd_hwdep snd_compress ac97_bus snd_pcm_dmaengine snd_seq_midi snd_seq_midi_event mei_me snd_pcm mei snd_rawmidi lpc_ich snd_seq snd_seq_device snd_timer snd 8250_fintek soundcore dw_dmac snd_soc_sst_acpi dw_dmac_core i2c_designware_platform i2c_designware_core 8250_dw spi_pxa2xx_platform acpi_pad tpm_crb mac_hid
[  109.348570] brcmf_sdio_bus_rxctl: resumed on timeout
[  109.407855] brcmf_cfg80211_reg_notifier: not a ISO3166 code
[  117.250002] brcmf_cfg80211_sched_scan_start: Scanning already: status (1)
[  117.268575] brcmf_escan_timeout: timer expired
[  150.101036] brcmf_escan_timeout: timer expired
[  150.101466] brcmf_cfg80211_sched_scan_start: Scanning already: status (1)
[  175.029556] brcmf_sdio_bus_rxctl: resumed on timeout
[  175.029567] brcmf_run_escan: error (-52)
[  175.029574] brcmf_cfg80211_scan: scan error (-52)
[  185.258413] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.258420] brcmf_fweh_event_worker: event handler failed (69)
[  185.258488] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.258491] brcmf_fweh_event_worker: event handler failed (69)
[  185.258696] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.258699] brcmf_fweh_event_worker: event handler failed (69)
[  185.258771] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.258775] brcmf_fweh_event_worker: event handler failed (69)
[  185.258985] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.258989] brcmf_fweh_event_worker: event handler failed (69)
[  185.259081] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.259084] brcmf_fweh_event_worker: event handler failed (69)
[  185.259311] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.259314] brcmf_fweh_event_worker: event handler failed (69)
[  185.259533] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.259537] brcmf_fweh_event_worker: event handler failed (69)
[  185.259634] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.259638] brcmf_fweh_event_worker: event handler failed (69)
[  185.259937] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.259941] brcmf_fweh_event_worker: event handler failed (69)
[  185.260122] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.260125] brcmf_fweh_event_worker: event handler failed (69)
[  185.260216] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.260219] brcmf_fweh_event_worker: event handler failed (69)
[  185.260310] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.260313] brcmf_fweh_event_worker: event handler failed (69)
[  185.260673] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.260678] brcmf_fweh_event_worker: event handler failed (69)
[  185.262139] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.262157] brcmf_fweh_event_worker: event handler failed (69)
[  185.264081] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.264101] brcmf_fweh_event_worker: event handler failed (69)
[  185.264361] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.264366] brcmf_fweh_event_worker: event handler failed (69)
[  185.264455] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.264459] brcmf_fweh_event_worker: event handler failed (69)
[  185.265274] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.265281] brcmf_fweh_event_worker: event handler failed (69)
[  185.265500] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.265504] brcmf_fweh_event_worker: event handler failed (69)
[  185.266117] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.266124] brcmf_fweh_event_worker: event handler failed (69)
[  185.266378] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.266384] brcmf_fweh_event_worker: event handler failed (69)
[  185.266461] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.266465] brcmf_fweh_event_worker: event handler failed (69)
[  185.266692] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.266695] brcmf_fweh_event_worker: event handler failed (69)
[  185.266785] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.266787] brcmf_fweh_event_worker: event handler failed (69)
[  185.266877] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.266880] brcmf_fweh_event_worker: event handler failed (69)
[  185.266980] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.266985] brcmf_fweh_event_worker: event handler failed (69)
[  185.267096] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.267101] brcmf_fweh_event_worker: event handler failed (69)
[  185.267192] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.267197] brcmf_fweh_event_worker: event handler failed (69)
[  185.267296] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.267301] brcmf_fweh_event_worker: event handler failed (69)
[  185.267388] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.267391] brcmf_fweh_event_worker: event handler failed (69)
[  185.267487] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.267492] brcmf_fweh_event_worker: event handler failed (69)
[  185.267589] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.267594] brcmf_fweh_event_worker: event handler failed (69)
[  185.267693] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.267698] brcmf_fweh_event_worker: event handler failed (69)
[  185.267799] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.267803] brcmf_fweh_event_worker: event handler failed (69)
[  185.267896] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.267900] brcmf_fweh_event_worker: event handler failed (69)
[  185.267990] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.267994] brcmf_fweh_event_worker: event handler failed (69)
[  185.268088] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.268092] brcmf_fweh_event_worker: event handler failed (69)
[  185.268187] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.268191] brcmf_fweh_event_worker: event handler failed (69)
[  185.268271] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.268275] brcmf_fweh_event_worker: event handler failed (69)
[  185.268360] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.268364] brcmf_fweh_event_worker: event handler failed (69)
[  185.268508] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.268513] brcmf_fweh_event_worker: event handler failed (69)
[  185.271207] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.271217] brcmf_fweh_event_worker: event handler failed (69)
[  185.271303] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.271308] brcmf_fweh_event_worker: event handler failed (69)
[  185.271496] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.271526] brcmf_fweh_event_worker: event handler failed (69)
[  185.271621] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.271644] brcmf_fweh_event_worker: event handler failed (69)
[  185.271733] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.271754] brcmf_fweh_event_worker: event handler failed (69)
[  185.271846] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.271866] brcmf_fweh_event_worker: event handler failed (69)
[  185.271952] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.271956] brcmf_fweh_event_worker: event handler failed (69)
[  185.272058] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.272079] brcmf_fweh_event_worker: event handler failed (69)
[  185.272151] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.272173] brcmf_fweh_event_worker: event handler failed (69)
[  185.272974] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.272999] brcmf_fweh_event_worker: event handler failed (69)
[  185.273089] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.273113] brcmf_fweh_event_worker: event handler failed (69)
[  185.273199] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.273223] brcmf_fweh_event_worker: event handler failed (69)
[  185.273636] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.273652] brcmf_fweh_event_worker: event handler failed (69)
[  185.273752] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.273773] brcmf_fweh_event_worker: event handler failed (69)
[  185.274003] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.274008] brcmf_fweh_event_worker: event handler failed (69)
[  185.274459] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.274483] brcmf_fweh_event_worker: event handler failed (69)
[  185.276880] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.276889] brcmf_fweh_event_worker: event handler failed (69)
[  185.276978] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.276982] brcmf_fweh_event_worker: event handler failed (69)
[  185.277080] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.277085] brcmf_fweh_event_worker: event handler failed (69)
[  185.277195] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.277199] brcmf_fweh_event_worker: event handler failed (69)
[  185.277918] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.277932] brcmf_fweh_event_worker: event handler failed (69)
[  185.278021] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.278025] brcmf_fweh_event_worker: event handler failed (69)
[  185.278163] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.278190] brcmf_fweh_event_worker: event handler failed (69)
[  185.278277] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.278300] brcmf_fweh_event_worker: event handler failed (69)
[  185.278392] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.278397] brcmf_fweh_event_worker: event handler failed (69)
[  185.278532] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.278538] brcmf_fweh_event_worker: event handler failed (69)
[  185.278676] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.278688] brcmf_fweh_event_worker: event handler failed (69)
[  185.278804] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.278809] brcmf_fweh_event_worker: event handler failed (69)
[  185.279155] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.279186] brcmf_fweh_event_worker: event handler failed (69)
[  185.279320] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.279326] brcmf_fweh_event_worker: event handler failed (69)
[  185.279425] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.279428] brcmf_fweh_event_worker: event handler failed (69)
[  185.279521] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.279523] brcmf_fweh_event_worker: event handler failed (69)
[  185.279614] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.279616] brcmf_fweh_event_worker: event handler failed (69)
[  185.279710] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.279713] brcmf_fweh_event_worker: event handler failed (69)
[  185.279804] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.279806] brcmf_fweh_event_worker: event handler failed (69)
[  185.279899] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.279901] brcmf_fweh_event_worker: event handler failed (69)
[  185.280054] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  185.280056] brcmf_fweh_event_worker: event handler failed (69)
[  202.269887] brcmf_sdio_bus_rxctl: resumed on timeout
[  202.269899] brcmf_run_escan: error (-52)
[  202.269905] brcmf_cfg80211_scan: scan error (-52)
[  203.310172] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.310180] brcmf_fweh_event_worker: event handler failed (69)
[  203.310358] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.310361] brcmf_fweh_event_worker: event handler failed (69)
[  203.310456] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.310459] brcmf_fweh_event_worker: event handler failed (69)
[  203.337480] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.337489] brcmf_fweh_event_worker: event handler failed (69)
[  203.337595] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.337598] brcmf_fweh_event_worker: event handler failed (69)
[  203.337693] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.337696] brcmf_fweh_event_worker: event handler failed (69)
[  203.337791] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.337794] brcmf_fweh_event_worker: event handler failed (69)
[  203.338138] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.338145] brcmf_fweh_event_worker: event handler failed (69)
[  203.445516] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.445525] brcmf_fweh_event_worker: event handler failed (69)
[  203.445746] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.445750] brcmf_fweh_event_worker: event handler failed (69)
[  203.446085] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.446092] brcmf_fweh_event_worker: event handler failed (69)
[  203.446217] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.446222] brcmf_fweh_event_worker: event handler failed (69)
[  203.446329] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.446333] brcmf_fweh_event_worker: event handler failed (69)
[  203.446437] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.446443] brcmf_fweh_event_worker: event handler failed (69)
[  203.473637] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.473665] brcmf_fweh_event_worker: event handler failed (69)
[  203.473901] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.473906] brcmf_fweh_event_worker: event handler failed (69)
[  203.474040] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.474045] brcmf_fweh_event_worker: event handler failed (69)
[  203.474155] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.474161] brcmf_fweh_event_worker: event handler failed (69)
[  203.474267] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.474272] brcmf_fweh_event_worker: event handler failed (69)
[  203.474388] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.474391] brcmf_fweh_event_worker: event handler failed (69)
[  203.474488] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.474491] brcmf_fweh_event_worker: event handler failed (69)
[  203.474599] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.474601] brcmf_fweh_event_worker: event handler failed (69)
[  203.501722] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  203.501731] brcmf_fweh_event_worker: event handler failed (69)
[  225.032480] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.032488] brcmf_fweh_event_worker: event handler failed (69)
[  225.032733] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.032737] brcmf_fweh_event_worker: event handler failed (69)
[  225.032824] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.032827] brcmf_fweh_event_worker: event handler failed (69)
[  225.033065] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.033068] brcmf_fweh_event_worker: event handler failed (69)
[  225.033164] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.033167] brcmf_fweh_event_worker: event handler failed (69)
[  225.033266] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.033269] brcmf_fweh_event_worker: event handler failed (69)
[  225.033368] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.033371] brcmf_fweh_event_worker: event handler failed (69)
[  225.033469] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.033472] brcmf_fweh_event_worker: event handler failed (69)
[  225.033558] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.033560] brcmf_fweh_event_worker: event handler failed (69)
[  225.033645] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.033648] brcmf_fweh_event_worker: event handler failed (69)
[  225.033733] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.033736] brcmf_fweh_event_worker: event handler failed (69)
[  225.033820] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.033823] brcmf_fweh_event_worker: event handler failed (69)
[  225.033906] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.033909] brcmf_fweh_event_worker: event handler failed (69)
[  225.033993] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.033996] brcmf_fweh_event_worker: event handler failed (69)
[  225.034082] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.034085] brcmf_fweh_event_worker: event handler failed (69)
[  225.034202] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.034225] brcmf_fweh_event_worker: event handler failed (69)
[  225.034308] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.034317] brcmf_fweh_event_worker: event handler failed (69)
[  225.034417] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.034423] brcmf_fweh_event_worker: event handler failed (69)
[  225.034517] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.034522] brcmf_fweh_event_worker: event handler failed (69)
[  225.034624] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.034630] brcmf_fweh_event_worker: event handler failed (69)
[  225.034738] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.034744] brcmf_fweh_event_worker: event handler failed (69)
[  225.034845] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.034848] brcmf_fweh_event_worker: event handler failed (69)
[  225.034935] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.034938] brcmf_fweh_event_worker: event handler failed (69)
[  225.035037] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.035040] brcmf_fweh_event_worker: event handler failed (69)
[  225.035135] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.035138] brcmf_fweh_event_worker: event handler failed (69)
[  225.035220] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.035225] brcmf_fweh_event_worker: event handler failed (69)
[  225.035309] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.035311] brcmf_fweh_event_worker: event handler failed (69)
[  225.035415] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.035418] brcmf_fweh_event_worker: event handler failed (69)
[  225.035512] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.035514] brcmf_fweh_event_worker: event handler failed (69)
[  225.035609] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.035614] brcmf_fweh_event_worker: event handler failed (69)
[  225.035738] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.035741] brcmf_fweh_event_worker: event handler failed (69)
[  225.035833] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.035836] brcmf_fweh_event_worker: event handler failed (69)
[  225.035928] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.035930] brcmf_fweh_event_worker: event handler failed (69)
[  225.036025] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.036028] brcmf_fweh_event_worker: event handler failed (69)
[  225.036125] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.036128] brcmf_fweh_event_worker: event handler failed (69)
[  225.036211] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.036213] brcmf_fweh_event_worker: event handler failed (69)
[  225.036294] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.036297] brcmf_fweh_event_worker: event handler failed (69)
[  225.036389] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.036391] brcmf_fweh_event_worker: event handler failed (69)
[  225.036484] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.036487] brcmf_fweh_event_worker: event handler failed (69)
[  225.036567] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.036570] brcmf_fweh_event_worker: event handler failed (69)
[  225.036662] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.036665] brcmf_fweh_event_worker: event handler failed (69)
[  225.036746] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.036748] brcmf_fweh_event_worker: event handler failed (69)
[  225.036841] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.036843] brcmf_fweh_event_worker: event handler failed (69)
[  225.036929] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.036931] brcmf_fweh_event_worker: event handler failed (69)
[  225.037024] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.037026] brcmf_fweh_event_worker: event handler failed (69)
[  225.037119] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.037121] brcmf_fweh_event_worker: event handler failed (69)
[  225.037203] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.037205] brcmf_fweh_event_worker: event handler failed (69)
[  225.037287] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.037290] brcmf_fweh_event_worker: event handler failed (69)
[  225.037396] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.037398] brcmf_fweh_event_worker: event handler failed (69)
[  225.037498] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.037501] brcmf_fweh_event_worker: event handler failed (69)
[  225.037586] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.037589] brcmf_fweh_event_worker: event handler failed (69)
[  225.037847] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.037850] brcmf_fweh_event_worker: event handler failed (69)
[  225.037938] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.037941] brcmf_fweh_event_worker: event handler failed (69)
[  225.038038] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.038041] brcmf_fweh_event_worker: event handler failed (69)
[  225.038184] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.038189] brcmf_fweh_event_worker: event handler failed (69)
[  225.038267] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.038282] brcmf_fweh_event_worker: event handler failed (69)
[  225.038382] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.038397] brcmf_fweh_event_worker: event handler failed (69)
[  225.038497] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.038503] brcmf_fweh_event_worker: event handler failed (69)
[  225.038607] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.038612] brcmf_fweh_event_worker: event handler failed (69)
[  225.038788] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  225.038795] brcmf_fweh_event_worker: event handler failed (69)
[  227.146339] brcmf_sdio_bus_rxctl: resumed on timeout
[  227.146354] brcmf_run_escan: error (-52)
[  227.146363] brcmf_cfg80211_scan: scan error (-52)
[  227.150052] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.150056] brcmf_fweh_event_worker: event handler failed (69)
[  227.150121] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.150123] brcmf_fweh_event_worker: event handler failed (69)
[  227.150472] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.150494] brcmf_fweh_event_worker: event handler failed (69)
[  227.150576] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.150582] brcmf_fweh_event_worker: event handler failed (69)
[  227.150840] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.150843] brcmf_fweh_event_worker: event handler failed (69)
[  227.150931] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.150934] brcmf_fweh_event_worker: event handler failed (69)
[  227.151027] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.151030] brcmf_fweh_event_worker: event handler failed (69)
[  227.151123] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.151126] brcmf_fweh_event_worker: event handler failed (69)
[  227.151220] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.151223] brcmf_fweh_event_worker: event handler failed (69)
[  227.151318] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.151321] brcmf_fweh_event_worker: event handler failed (69)
[  227.151415] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.151418] brcmf_fweh_event_worker: event handler failed (69)
[  227.151510] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.151513] brcmf_fweh_event_worker: event handler failed (69)
[  227.151606] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.151609] brcmf_fweh_event_worker: event handler failed (69)
[  227.151702] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.151705] brcmf_fweh_event_worker: event handler failed (69)
[  227.151800] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.151802] brcmf_fweh_event_worker: event handler failed (69)
[  227.151895] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.151898] brcmf_fweh_event_worker: event handler failed (69)
[  227.151997] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.152000] brcmf_fweh_event_worker: event handler failed (69)
[  227.152095] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.152097] brcmf_fweh_event_worker: event handler failed (69)
[  227.152191] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.152194] brcmf_fweh_event_worker: event handler failed (69)
[  227.152289] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.152292] brcmf_fweh_event_worker: event handler failed (69)
[  227.152378] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.152381] brcmf_fweh_event_worker: event handler failed (69)
[  227.152463] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.152466] brcmf_fweh_event_worker: event handler failed (69)
[  227.152561] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.152564] brcmf_fweh_event_worker: event handler failed (69)
[  227.152661] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.152664] brcmf_fweh_event_worker: event handler failed (69)
[  227.152760] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.152763] brcmf_fweh_event_worker: event handler failed (69)
[  227.152859] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.152862] brcmf_fweh_event_worker: event handler failed (69)
[  227.152956] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.152959] brcmf_fweh_event_worker: event handler failed (69)
[  227.153054] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.153057] brcmf_fweh_event_worker: event handler failed (69)
[  227.153150] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.153153] brcmf_fweh_event_worker: event handler failed (69)
[  227.153248] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.153251] brcmf_fweh_event_worker: event handler failed (69)
[  227.153349] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.153352] brcmf_fweh_event_worker: event handler failed (69)
[  227.153448] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.153451] brcmf_fweh_event_worker: event handler failed (69)
[  227.153532] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.153534] brcmf_fweh_event_worker: event handler failed (69)
[  227.153628] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.153631] brcmf_fweh_event_worker: event handler failed (69)
[  227.153723] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.153726] brcmf_fweh_event_worker: event handler failed (69)
[  227.153818] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.153821] brcmf_fweh_event_worker: event handler failed (69)
[  227.153903] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.153905] brcmf_fweh_event_worker: event handler failed (69)
[  227.153999] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.154001] brcmf_fweh_event_worker: event handler failed (69)
[  227.154095] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.154098] brcmf_fweh_event_worker: event handler failed (69)
[  227.154250] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.154266] brcmf_fweh_event_worker: event handler failed (69)
[  227.154368] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.154386] brcmf_fweh_event_worker: event handler failed (69)
[  227.154477] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.154492] brcmf_fweh_event_worker: event handler failed (69)
[  227.154585] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.154592] brcmf_fweh_event_worker: event handler failed (69)
[  227.154694] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.154700] brcmf_fweh_event_worker: event handler failed (69)
[  227.154807] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.154813] brcmf_fweh_event_worker: event handler failed (69)
[  227.154917] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.154923] brcmf_fweh_event_worker: event handler failed (69)
[  227.155026] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.155032] brcmf_fweh_event_worker: event handler failed (69)
[  227.155140] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.155146] brcmf_fweh_event_worker: event handler failed (69)
[  227.155253] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.155258] brcmf_fweh_event_worker: event handler failed (69)
[  227.155347] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.155352] brcmf_fweh_event_worker: event handler failed (69)
[  227.155445] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.155448] brcmf_fweh_event_worker: event handler failed (69)
[  227.155531] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.155534] brcmf_fweh_event_worker: event handler failed (69)
[  227.155618] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.155621] brcmf_fweh_event_worker: event handler failed (69)
[  227.155705] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.155708] brcmf_fweh_event_worker: event handler failed (69)
[  227.155790] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.155793] brcmf_fweh_event_worker: event handler failed (69)
[  227.155888] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.155891] brcmf_fweh_event_worker: event handler failed (69)
[  227.155987] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.155991] brcmf_fweh_event_worker: event handler failed (69)
[  227.156085] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.156088] brcmf_fweh_event_worker: event handler failed (69)
[  227.156170] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.156175] brcmf_fweh_event_worker: event handler failed (69)
[  227.156270] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.156273] brcmf_fweh_event_worker: event handler failed (69)
[  227.156366] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.156369] brcmf_fweh_event_worker: event handler failed (69)
[  227.156461] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.156465] brcmf_fweh_event_worker: event handler failed (69)
[  227.156558] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.156561] brcmf_fweh_event_worker: event handler failed (69)
[  227.156655] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  227.156658] brcmf_fweh_event_worker: event handler failed (69)
[  228.058243] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  228.058255] brcmf_fweh_event_worker: event handler failed (69)
[  228.058385] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  228.058391] brcmf_fweh_event_worker: event handler failed (69)
[  228.058501] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  228.058507] brcmf_fweh_event_worker: event handler failed (69)
[  228.082325] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  228.082334] brcmf_fweh_event_worker: event handler failed (69)
[  228.082450] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  228.082453] brcmf_fweh_event_worker: event handler failed (69)
[  228.082553] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  228.082556] brcmf_fweh_event_worker: event handler failed (69)
[  228.082653] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  228.082656] brcmf_fweh_event_worker: event handler failed (69)
[  253.050631] brcmf_sdio_bus_rxctl: resumed on timeout
[  253.050645] brcmf_run_escan: error (-52)
[  253.050654] brcmf_cfg80211_scan: scan error (-52)
[  286.071235] brcmf_sdio_bus_rxctl: resumed on timeout
[  286.071247] brcmf_run_escan: error (-52)
[  286.071253] brcmf_cfg80211_scan: scan error (-52)
[  329.055862] brcmf_sdio_bus_rxctl: resumed on timeout
[  329.055873] brcmf_run_escan: error (-52)
[  329.055880] brcmf_cfg80211_scan: scan error (-52)
[  366.035929] WARNING: driver brcmfmac_sdio did not remove its interrupt handler!
[  366.039230] brcmf_sdio_dpc: failed backplane access over SDIO, halting operation
[  366.612506] usbcore: deregistering interface driver brcmfmac
[  366.870785] brcmf_sdio_drivestrengthinit: No SDIO Drive strength init done for chip 4324 rev 5 pmurev 17
[  366.871176] usbcore: registered new interface driver brcmfmac
[  367.051826] brcmf_c_preinit_dcmds: Firmware version = wl0: Jul 17 2013 07:36:07 version 6.10.197.71 (r412987) FWID 01-882d2634
[  368.495953] brcmf_cfg80211_reg_notifier: not a ISO3166 code
[  368.748844] brcmf_add_if: ERROR: netdev:wlan0 already exists
[  368.748852] brcmf_add_if: ignore IF event
[  370.828489] brcmf_sdio_bus_rxctl: resumed on timeout
[  370.828501] brcmf_dongle_roam: roam_off error (-52)
[  370.828505] brcmf_netdev_open: failed to bring up cfg80211
[  370.968180] brcmf_add_if: ERROR: netdev:wlan0 already exists
[  370.968208] brcmf_add_if: ignore IF event
[  373.364395] brcmf_sdio_bus_rxctl: resumed on timeout
[  373.368063] brcmf_add_if: ERROR: netdev:wlan0 already exists
[  373.368070] brcmf_add_if: ignore IF event
[  375.732552] brcmf_sdio_bus_rxctl: resumed on timeout
[  375.732563] brcmf_run_escan: error (-52)
[  375.732570] brcmf_cfg80211_scan: scan error (-52)
[  377.088011] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  377.088034] brcmf_fweh_event_worker: event handler failed (69)
[  377.088153] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  377.088157] brcmf_fweh_event_worker: event handler failed (69)
[  377.088251] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  377.088255] brcmf_fweh_event_worker: event handler failed (69)
[  377.088341] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  377.088343] brcmf_fweh_event_worker: event handler failed (69)
[  377.088450] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  377.088455] brcmf_fweh_event_worker: event handler failed (69)
[  377.088546] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  377.088549] brcmf_fweh_event_worker: event handler failed (69)
[  377.088636] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  377.088639] brcmf_fweh_event_worker: event handler failed (69)
[  377.088727] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  377.088730] brcmf_fweh_event_worker: event handler failed (69)
[  402.040867] brcmf_sdio_bus_rxctl: resumed on timeout
[  402.040879] brcmf_run_escan: error (-52)
[  402.040886] brcmf_cfg80211_scan: scan error (-52)
[  415.733138] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.733146] brcmf_fweh_event_worker: event handler failed (69)
[  415.733409] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.733414] brcmf_fweh_event_worker: event handler failed (69)
[  415.733643] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.733647] brcmf_fweh_event_worker: event handler failed (69)
[  415.733897] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.733901] brcmf_fweh_event_worker: event handler failed (69)
[  415.734166] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.734169] brcmf_fweh_event_worker: event handler failed (69)
[  415.734284] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.734287] brcmf_fweh_event_worker: event handler failed (69)
[  415.734574] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.734578] brcmf_fweh_event_worker: event handler failed (69)
[  415.734847] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.734851] brcmf_fweh_event_worker: event handler failed (69)
[  415.735124] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.735128] brcmf_fweh_event_worker: event handler failed (69)
[  415.735350] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.735354] brcmf_fweh_event_worker: event handler failed (69)
[  415.735505] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.735509] brcmf_fweh_event_worker: event handler failed (69)
[  415.735643] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.735647] brcmf_fweh_event_worker: event handler failed (69)
[  415.735736] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.735739] brcmf_fweh_event_worker: event handler failed (69)
[  415.735827] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.735830] brcmf_fweh_event_worker: event handler failed (69)
[  415.735927] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.735929] brcmf_fweh_event_worker: event handler failed (69)
[  415.736014] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736016] brcmf_fweh_event_worker: event handler failed (69)
[  415.736095] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736096] brcmf_fweh_event_worker: event handler failed (69)
[  415.736178] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736180] brcmf_fweh_event_worker: event handler failed (69)
[  415.736262] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736264] brcmf_fweh_event_worker: event handler failed (69)
[  415.736349] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736351] brcmf_fweh_event_worker: event handler failed (69)
[  415.736433] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736435] brcmf_fweh_event_worker: event handler failed (69)
[  415.736519] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736521] brcmf_fweh_event_worker: event handler failed (69)
[  415.736605] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736607] brcmf_fweh_event_worker: event handler failed (69)
[  415.736700] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736702] brcmf_fweh_event_worker: event handler failed (69)
[  415.736777] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736779] brcmf_fweh_event_worker: event handler failed (69)
[  415.736860] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736861] brcmf_fweh_event_worker: event handler failed (69)
[  415.736949] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.736951] brcmf_fweh_event_worker: event handler failed (69)
[  415.739807] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.739835] brcmf_fweh_event_worker: event handler failed (69)
[  415.740763] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.740812] brcmf_fweh_event_worker: event handler failed (69)
[  415.740911] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.740916] brcmf_fweh_event_worker: event handler failed (69)
[  415.741042] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.741062] brcmf_fweh_event_worker: event handler failed (69)
[  415.741921] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.741942] brcmf_fweh_event_worker: event handler failed (69)
[  415.742035] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.742040] brcmf_fweh_event_worker: event handler failed (69)
[  415.742131] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.742135] brcmf_fweh_event_worker: event handler failed (69)
[  415.742225] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.742229] brcmf_fweh_event_worker: event handler failed (69)
[  415.742313] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.742317] brcmf_fweh_event_worker: event handler failed (69)
[  415.742400] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.742404] brcmf_fweh_event_worker: event handler failed (69)
[  415.742487] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.742491] brcmf_fweh_event_worker: event handler failed (69)
[  415.742579] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.742583] brcmf_fweh_event_worker: event handler failed (69)
[  415.742675] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.742677] brcmf_fweh_event_worker: event handler failed (69)
[  415.742777] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.742780] brcmf_fweh_event_worker: event handler failed (69)
[  415.742868] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.742870] brcmf_fweh_event_worker: event handler failed (69)
[  415.742958] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.742960] brcmf_fweh_event_worker: event handler failed (69)
[  415.743046] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.743048] brcmf_fweh_event_worker: event handler failed (69)
[  415.743134] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.743136] brcmf_fweh_event_worker: event handler failed (69)
[  415.743224] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.743226] brcmf_fweh_event_worker: event handler failed (69)
[  415.743312] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.743314] brcmf_fweh_event_worker: event handler failed (69)
[  415.743417] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.743419] brcmf_fweh_event_worker: event handler failed (69)
[  415.743496] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.743498] brcmf_fweh_event_worker: event handler failed (69)
[  415.743600] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.743604] brcmf_fweh_event_worker: event handler failed (69)
[  415.743690] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.743692] brcmf_fweh_event_worker: event handler failed (69)
[  415.743786] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.743790] brcmf_fweh_event_worker: event handler failed (69)
[  415.743886] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.743888] brcmf_fweh_event_worker: event handler failed (69)
[  415.743986] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.743990] brcmf_fweh_event_worker: event handler failed (69)
[  415.744078] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.744082] brcmf_fweh_event_worker: event handler failed (69)
[  415.744365] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.744370] brcmf_fweh_event_worker: event handler failed (69)
[  415.744465] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  415.744469] brcmf_fweh_event_worker: event handler failed (69)
[  417.833186] brcmf_sdio_bus_rxctl: resumed on timeout
[  417.833198] brcmf_run_escan: error (-52)
[  417.833205] brcmf_cfg80211_scan: scan error (-52)
[  418.873539] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  418.873551] brcmf_fweh_event_worker: event handler failed (69)
[  418.873734] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  418.873739] brcmf_fweh_event_worker: event handler failed (69)
[  418.874388] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  418.874395] brcmf_fweh_event_worker: event handler failed (69)
[  418.874514] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  418.874520] brcmf_fweh_event_worker: event handler failed (69)
[  418.900137] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  418.900144] brcmf_fweh_event_worker: event handler failed (69)
[  418.900233] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  418.900237] brcmf_fweh_event_worker: event handler failed (69)
[  418.900332] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  418.900335] brcmf_fweh_event_worker: event handler failed (69)
[  418.900432] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  418.900436] brcmf_fweh_event_worker: event handler failed (69)
[  418.900526] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  418.900529] brcmf_fweh_event_worker: event handler failed (69)
[  418.900619] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  418.900622] brcmf_fweh_event_worker: event handler failed (69)
[  418.900713] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  418.900715] brcmf_fweh_event_worker: event handler failed (69)
[  425.889313] brcmf_sdio_bus_rxctl: resumed on timeout
[  425.889324] brcmf_run_escan: error (-52)
[  425.889331] brcmf_cfg80211_scan: scan error (-52)
[  426.929591] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  426.929603] brcmf_fweh_event_worker: event handler failed (69)
[  426.929720] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  426.929726] brcmf_fweh_event_worker: event handler failed (69)
[  426.929839] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  426.929845] brcmf_fweh_event_worker: event handler failed (69)
[  426.956781] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  426.956790] brcmf_fweh_event_worker: event handler failed (69)
[  426.956888] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  426.956891] brcmf_fweh_event_worker: event handler failed (69)
[  426.956986] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  426.956989] brcmf_fweh_event_worker: event handler failed (69)
[  427.088686] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  427.088693] brcmf_fweh_event_worker: event handler failed (69)
[  427.088909] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  427.088912] brcmf_fweh_event_worker: event handler failed (69)
[  427.089004] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  427.089007] brcmf_fweh_event_worker: event handler failed (69)
[  427.089090] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  427.089092] brcmf_fweh_event_worker: event handler failed (69)
[  435.604957] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.604966] brcmf_fweh_event_worker: event handler failed (69)
[  435.605188] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.605193] brcmf_fweh_event_worker: event handler failed (69)
[  435.605831] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.605837] brcmf_fweh_event_worker: event handler failed (69)
[  435.606060] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.606064] brcmf_fweh_event_worker: event handler failed (69)
[  435.606294] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.606299] brcmf_fweh_event_worker: event handler failed (69)
[  435.606530] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.606535] brcmf_fweh_event_worker: event handler failed (69)
[  435.606697] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.606702] brcmf_fweh_event_worker: event handler failed (69)
[  435.607048] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.607053] brcmf_fweh_event_worker: event handler failed (69)
[  435.607299] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.607304] brcmf_fweh_event_worker: event handler failed (69)
[  435.607404] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.607409] brcmf_fweh_event_worker: event handler failed (69)
[  435.607948] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.607965] brcmf_fweh_event_worker: event handler failed (69)
[  435.608120] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.608128] brcmf_fweh_event_worker: event handler failed (69)
[  435.608445] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.608452] brcmf_fweh_event_worker: event handler failed (69)
[  435.611548] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.611558] brcmf_fweh_event_worker: event handler failed (69)
[  435.611647] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.611652] brcmf_fweh_event_worker: event handler failed (69)
[  435.611764] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.611769] brcmf_fweh_event_worker: event handler failed (69)
[  435.611877] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.611882] brcmf_fweh_event_worker: event handler failed (69)
[  435.611998] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.612021] brcmf_fweh_event_worker: event handler failed (69)
[  435.612135] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.612142] brcmf_fweh_event_worker: event handler failed (69)
[  435.612235] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.612238] brcmf_fweh_event_worker: event handler failed (69)
[  435.612328] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.612331] brcmf_fweh_event_worker: event handler failed (69)
[  435.612422] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.612425] brcmf_fweh_event_worker: event handler failed (69)
[  435.612514] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.612517] brcmf_fweh_event_worker: event handler failed (69)
[  435.612611] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.612614] brcmf_fweh_event_worker: event handler failed (69)
[  435.612705] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.612708] brcmf_fweh_event_worker: event handler failed (69)
[  435.612800] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.612802] brcmf_fweh_event_worker: event handler failed (69)
[  435.612893] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.612895] brcmf_fweh_event_worker: event handler failed (69)
[  435.612988] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.612991] brcmf_fweh_event_worker: event handler failed (69)
[  435.613081] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.613084] brcmf_fweh_event_worker: event handler failed (69)
[  435.613178] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.613180] brcmf_fweh_event_worker: event handler failed (69)
[  435.613270] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.613272] brcmf_fweh_event_worker: event handler failed (69)
[  435.613417] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.613430] brcmf_fweh_event_worker: event handler failed (69)
[  435.613515] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.613521] brcmf_fweh_event_worker: event handler failed (69)
[  435.613813] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.613817] brcmf_fweh_event_worker: event handler failed (69)
[  435.613909] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.613914] brcmf_fweh_event_worker: event handler failed (69)
[  435.613992] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.613998] brcmf_fweh_event_worker: event handler failed (69)
[  435.614089] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.614091] brcmf_fweh_event_worker: event handler failed (69)
[  435.614171] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.614174] brcmf_fweh_event_worker: event handler failed (69)
[  435.614265] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.614268] brcmf_fweh_event_worker: event handler failed (69)
[  435.614360] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.614363] brcmf_fweh_event_worker: event handler failed (69)
[  435.614455] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.614458] brcmf_fweh_event_worker: event handler failed (69)
[  435.614538] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.614541] brcmf_fweh_event_worker: event handler failed (69)
[  435.614632] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.614634] brcmf_fweh_event_worker: event handler failed (69)
[  435.614717] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.614720] brcmf_fweh_event_worker: event handler failed (69)
[  435.614811] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.614816] brcmf_fweh_event_worker: event handler failed (69)
[  435.614894] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.614898] brcmf_fweh_event_worker: event handler failed (69)
[  435.614990] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.614993] brcmf_fweh_event_worker: event handler failed (69)
[  435.615084] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.615087] brcmf_fweh_event_worker: event handler failed (69)
[  435.615178] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.615180] brcmf_fweh_event_worker: event handler failed (69)
[  435.615262] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.615265] brcmf_fweh_event_worker: event handler failed (69)
[  435.615357] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.615359] brcmf_fweh_event_worker: event handler failed (69)
[  435.615447] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.615449] brcmf_fweh_event_worker: event handler failed (69)
[  435.615538] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.615541] brcmf_fweh_event_worker: event handler failed (69)
[  435.615633] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.615635] brcmf_fweh_event_worker: event handler failed (69)
[  435.615724] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.615726] brcmf_fweh_event_worker: event handler failed (69)
[  435.615816] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.615818] brcmf_fweh_event_worker: event handler failed (69)
[  435.615907] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.615910] brcmf_fweh_event_worker: event handler failed (69)
[  435.616151] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.616153] brcmf_fweh_event_worker: event handler failed (69)
[  435.616242] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.616245] brcmf_fweh_event_worker: event handler failed (69)
[  435.616334] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.616336] brcmf_fweh_event_worker: event handler failed (69)
[  435.616427] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.616432] brcmf_fweh_event_worker: event handler failed (69)
[  435.616519] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.616521] brcmf_fweh_event_worker: event handler failed (69)
[  435.616610] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.616613] brcmf_fweh_event_worker: event handler failed (69)
[  435.616690] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.616693] brcmf_fweh_event_worker: event handler failed (69)
[  435.616784] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.616786] brcmf_fweh_event_worker: event handler failed (69)
[  435.616875] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.616878] brcmf_fweh_event_worker: event handler failed (69)
[  435.617026] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[  435.617029] brcmf_fweh_event_worker: event handler failed (69)
[  437.729501] brcmf_sdio_bus_rxctl: resumed on timeout
[  437.729513] brcmf_run_escan: error (-52)
[  437.729519] brcmf_cfg80211_scan: scan error (-52)
[  441.041458] brcmf_sdio_bus_rxctl: resumed on timeout
[  441.041489] brcmf_run_escan: error (-52)
[  441.041500] brcmf_cfg80211_scan: scan error (-52)
[  464.057882] brcmf_sdio_bus_rxctl: resumed on timeout
[  464.057894] brcmf_run_escan: error (-52)
[  464.057900] brcmf_cfg80211_scan: scan error (-52)
bradley@kangaroo:~$ 


```

---

### Post by chili555 on 2016-07-06
> brcmf_cfg80211_reg_notifier: not a ISO3166 codeLet's try to fix that first.

I recommend that your regulatory domain be set explicitly. Check yours:

   ```
 sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
gksudo gedit /etc/default/crda
```

Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Unload and reload the driver:```
sudo modprobe -r brcmfmac && sudo modprobe brcmfmac
```Restart NM:```
sudo service network-manager restart
```Any improvement? If not, let's see:```
dmesg | grep brcm
```Post messages after the last ones above; that is, after this:> [  [COLOR="#FF0000"]464.057900[/COLOR]] brcmf_cfg80211_scan: scan error (-52)For me, at least, these SDIO devices are uncharted territory. I am willing to try until there is nothing left to try, but I have little experience to draw on.

---

### Post by bradleypariah on 2016-07-06
Seemingly no change in behavior.

```
[  464.057900] brcmf_cfg80211_scan: scan error (-52)
[  497.042339] brcmf_sdio_bus_rxctl: resumed on timeout
[  497.042354] brcmf_run_escan: error (-52)
[  497.042361] brcmf_cfg80211_scan: scan error (-52)
[  540.047021] brcmf_sdio_bus_rxctl: resumed on timeout
[  540.047033] brcmf_run_escan: error (-52)
[  540.047039] brcmf_cfg80211_scan: scan error (-52)
[  593.095817] brcmf_sdio_bus_rxctl: resumed on timeout
[  593.095831] brcmf_run_escan: error (-52)
[  593.095837] brcmf_cfg80211_scan: scan error (-52)
[  656.092756] brcmf_sdio_bus_rxctl: resumed on timeout
[  656.092768] brcmf_run_escan: error (-52)
[  656.092774] brcmf_cfg80211_scan: scan error (-52)
[  719.085704] brcmf_sdio_bus_rxctl: resumed on timeout
[  719.085715] brcmf_run_escan: error (-52)
[  719.085721] brcmf_cfg80211_scan: scan error (-52)
[  782.094647] brcmf_sdio_bus_rxctl: resumed on timeout
[  782.094658] brcmf_run_escan: error (-52)
[  782.094665] brcmf_cfg80211_scan: scan error (-52)
[  845.107595] brcmf_sdio_bus_rxctl: resumed on timeout
[  845.107606] brcmf_run_escan: error (-52)
[  845.107612] brcmf_cfg80211_scan: scan error (-52)
[  908.108532] brcmf_sdio_bus_rxctl: resumed on timeout
[  908.108544] brcmf_run_escan: error (-52)
[  908.108550] brcmf_cfg80211_scan: scan error (-52)
[  971.109479] brcmf_sdio_bus_rxctl: resumed on timeout
[  971.109490] brcmf_run_escan: error (-52)
[  971.109497] brcmf_cfg80211_scan: scan error (-52)
[ 1034.110425] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1034.110436] brcmf_run_escan: error (-52)
[ 1034.110443] brcmf_cfg80211_scan: scan error (-52)
[ 1097.111371] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1097.111383] brcmf_run_escan: error (-52)
[ 1097.111390] brcmf_cfg80211_scan: scan error (-52)
[ 1160.112309] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1160.112320] brcmf_run_escan: error (-52)
[ 1160.112326] brcmf_cfg80211_scan: scan error (-52)
[ 1223.065254] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1223.065268] brcmf_run_escan: error (-52)
[ 1223.065274] brcmf_cfg80211_scan: scan error (-52)
[ 1286.114195] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1286.114206] brcmf_run_escan: error (-52)
[ 1286.114212] brcmf_cfg80211_scan: scan error (-52)
[ 1349.107141] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1349.107155] brcmf_run_escan: error (-52)
[ 1349.107161] brcmf_cfg80211_scan: scan error (-52)
[ 1412.116082] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1412.116094] brcmf_run_escan: error (-52)
[ 1412.116101] brcmf_cfg80211_scan: scan error (-52)
[ 1475.101038] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1475.101050] brcmf_run_escan: error (-52)
[ 1475.101056] brcmf_cfg80211_scan: scan error (-52)
[ 1538.085969] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1538.085980] brcmf_run_escan: error (-52)
[ 1538.085987] brcmf_cfg80211_scan: scan error (-52)
[ 1601.110914] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1601.110926] brcmf_run_escan: error (-52)
[ 1601.110932] brcmf_cfg80211_scan: scan error (-52)
[ 1664.119856] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1664.119867] brcmf_run_escan: error (-52)
[ 1664.119873] brcmf_cfg80211_scan: scan error (-52)
[ 1727.096805] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1727.096818] brcmf_run_escan: error (-52)
[ 1727.096824] brcmf_cfg80211_scan: scan error (-52)
[ 1790.121746] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1790.121757] brcmf_run_escan: error (-52)
[ 1790.121763] brcmf_cfg80211_scan: scan error (-52)
[ 1853.106692] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1853.106703] brcmf_run_escan: error (-52)
[ 1853.106709] brcmf_cfg80211_scan: scan error (-52)
[ 1916.123637] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1916.123648] brcmf_run_escan: error (-52)
[ 1916.123654] brcmf_cfg80211_scan: scan error (-52)
[ 1979.124581] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1979.124594] brcmf_run_escan: error (-52)
[ 1979.124601] brcmf_cfg80211_scan: scan error (-52)
[ 2042.125526] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2042.125537] brcmf_run_escan: error (-52)
[ 2042.125544] brcmf_cfg80211_scan: scan error (-52)
[ 2105.126471] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2105.126482] brcmf_run_escan: error (-52)
[ 2105.126488] brcmf_cfg80211_scan: scan error (-52)
[ 2168.131411] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2168.131422] brcmf_run_escan: error (-52)
[ 2168.131428] brcmf_cfg80211_scan: scan error (-52)
[ 2231.132357] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2231.132371] brcmf_run_escan: error (-52)
[ 2231.132377] brcmf_cfg80211_scan: scan error (-52)
[ 2294.129299] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2294.129312] brcmf_run_escan: error (-52)
[ 2294.129318] brcmf_cfg80211_scan: scan error (-52)
[ 2357.130247] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2357.130258] brcmf_run_escan: error (-52)
[ 2357.130264] brcmf_cfg80211_scan: scan error (-52)
[ 2420.079182] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2420.079193] brcmf_run_escan: error (-52)
[ 2420.079200] brcmf_cfg80211_scan: scan error (-52)
[ 2483.100138] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2483.100149] brcmf_run_escan: error (-52)
[ 2483.100155] brcmf_cfg80211_scan: scan error (-52)
[ 2546.133072] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2546.133083] brcmf_run_escan: error (-52)
[ 2546.133089] brcmf_cfg80211_scan: scan error (-52)
[ 2564.601150] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.601174] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.601347] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.601359] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.601477] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.601483] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.601674] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.601682] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.601766] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.601770] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.601868] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.601870] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.601962] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.601965] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.602055] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.602057] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.602154] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.602157] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.602248] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.602251] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.602346] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.602349] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.602439] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.602442] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.602523] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.602526] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.602606] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.602609] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.602688] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.602691] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.602779] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.602782] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.603012] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.603015] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.603108] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.603111] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.603203] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.603206] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.603298] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.603301] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.603393] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.603396] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.603488] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.603491] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.603585] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.603587] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.603683] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.603686] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.603778] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.603781] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.603875] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.603878] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.603958] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.603961] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.604041] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.604044] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.604137] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.604139] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.604220] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.604223] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.604315] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.604318] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.604410] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.604412] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.604504] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.604507] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.604588] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.604591] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.604683] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.604686] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.604778] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.604781] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.604873] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.604876] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.604968] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.604971] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.605063] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.605066] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.605147] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.605150] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.605260] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.605291] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.605374] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.605392] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.605656] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.605662] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.605769] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.605774] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.605879] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.605884] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.605994] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.606000] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.606092] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.606097] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.606179] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.606182] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.606272] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.606275] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.606371] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.606374] brcmf_fweh_event_worker: event handler failed (69)
[ 2564.606528] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2564.606531] brcmf_fweh_event_worker: event handler failed (69)
[ 2609.066024] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2609.066035] brcmf_run_escan: error (-52)
[ 2609.066042] brcmf_cfg80211_scan: scan error (-52)
[ 2653.213480] WARNING: driver brcmfmac_sdio did not remove its interrupt handler!
[ 2653.216972] brcmf_sdio_dpc: failed backplane access over SDIO, halting operation
[ 2653.790608] usbcore: deregistering interface driver brcmfmac
[ 2654.053045] brcmf_sdio_drivestrengthinit: No SDIO Drive strength init done for chip 4324 rev 5 pmurev 17
[ 2654.053463] usbcore: registered new interface driver brcmfmac
[ 2654.258495] brcmf_c_preinit_dcmds: Firmware version = wl0: Jul 17 2013 07:36:07 version 6.10.197.71 (r412987) FWID 01-882d2634
[ 2655.762747] brcmf_cfg80211_reg_notifier: not a ISO3166 code
[ 2658.030712] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2659.094795] brcmf_add_if: ERROR: netdev:wlan0 already exists
[ 2659.094805] brcmf_add_if: ignore IF event
[ 2659.374540] brcmf_cfg80211_reg_notifier: not a ISO3166 code
[ 2659.698661] brcmf_add_if: ERROR: netdev:wlan0 already exists
[ 2659.698671] brcmf_add_if: ignore IF event
[ 2662.082820] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2662.082831] brcmf_run_escan: error (-52)
[ 2662.082838] brcmf_cfg80211_scan: scan error (-52)
[ 2663.102880] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2663.102890] brcmf_fweh_event_worker: event handler failed (69)
[ 2663.130363] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2663.130371] brcmf_fweh_event_worker: event handler failed (69)
[ 2663.130495] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2663.130498] brcmf_fweh_event_worker: event handler failed (69)
[ 2663.130604] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2663.130608] brcmf_fweh_event_worker: event handler failed (69)
[ 2663.130704] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2663.130709] brcmf_fweh_event_worker: event handler failed (69)
[ 2663.130848] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2663.130854] brcmf_fweh_event_worker: event handler failed (69)
[ 2663.130979] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2663.130986] brcmf_fweh_event_worker: event handler failed (69)
[ 2663.131108] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2663.131113] brcmf_fweh_event_worker: event handler failed (69)
[ 2663.178558] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2663.178566] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.050964] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.050973] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.051075] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.051085] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.051170] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.051173] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.051271] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.051274] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.051369] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.051372] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.051468] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.051471] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.051563] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.051566] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.051658] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.051661] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.051754] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.051757] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.051849] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.051851] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.051944] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.051947] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.052040] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.052043] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.052143] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.052146] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.052239] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.052241] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.052331] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.052333] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.052424] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.052426] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.052516] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.052518] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.052611] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.052614] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.052705] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.052708] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.052797] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.052800] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.052888] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.052891] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.052984] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.052986] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.053077] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.053080] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.053183] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.053185] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.053265] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.053267] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.053362] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.053364] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.053452] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.053455] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.053547] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.053549] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.053625] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.053628] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.053706] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.053708] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.053785] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.053788] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.053875] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.053878] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.053956] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.053959] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.054047] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.054050] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.054141] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.054143] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.054229] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.054231] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.054324] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.054327] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.054413] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.054415] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.054502] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.054504] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.054589] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.054592] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.054678] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.054680] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.054784] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.054798] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.055345] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.055355] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.055435] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.055438] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.055527] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.055529] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.055617] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.055621] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.055707] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.055710] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.055799] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.055802] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.055891] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.055895] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.055985] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.055988] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.056076] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.056078] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.056168] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.056170] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.056267] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.056269] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.056355] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.056357] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.056444] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.056446] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.056532] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.056534] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.056620] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.056622] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.056711] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.056713] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.056800] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.056802] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.056889] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.056891] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.056977] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.056980] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.927109] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.927117] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.954239] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.954247] brcmf_fweh_event_worker: event handler failed (69)
[ 2665.954355] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2665.954360] brcmf_fweh_event_worker: event handler failed (69)
[ 2666.014927] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2666.014939] brcmf_fweh_event_worker: event handler failed (69)
[ 2666.015043] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2666.015067] brcmf_fweh_event_worker: event handler failed (69)
[ 2666.015218] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2666.015228] brcmf_fweh_event_worker: event handler failed (69)
[ 2666.015314] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2666.015318] brcmf_fweh_event_worker: event handler failed (69)
[ 2666.042522] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2666.042533] brcmf_fweh_event_worker: event handler failed (69)
[ 2666.042634] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2666.042641] brcmf_fweh_event_worker: event handler failed (69)
[ 2666.042847] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2666.042854] brcmf_fweh_event_worker: event handler failed (69)
[ 2666.042951] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2666.042956] brcmf_fweh_event_worker: event handler failed (69)
[ 2668.142901] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2668.142912] brcmf_run_escan: error (-52)
[ 2668.142918] brcmf_cfg80211_scan: scan error (-52)
[ 2669.102548] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.102560] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.103543] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.103547] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.103623] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.103626] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.127145] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.127165] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.127239] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.127242] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.127323] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.127324] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.127409] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.127410] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.178539] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.178552] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.178692] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.178695] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.202221] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.202226] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.226442] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.226454] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.226670] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.226673] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.226752] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.226800] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.254607] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.254617] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.254788] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.254805] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.255216] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.255221] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.255389] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.255392] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.255481] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.255484] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.255570] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.255573] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.255668] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.255671] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.255765] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.255768] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.255850] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.255853] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.255955] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.255957] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.256052] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.256054] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.282741] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.282753] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.282934] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.282939] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.283041] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.283046] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.283146] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.283151] brcmf_fweh_event_worker: event handler failed (69)
[ 2669.283249] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2669.283254] brcmf_fweh_event_worker: event handler failed (69)
[ 2694.087296] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2694.087307] brcmf_run_escan: error (-52)
[ 2694.087313] brcmf_cfg80211_scan: scan error (-52)
[ 2708.202506] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.202514] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.202719] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.202723] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.202942] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.202946] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.203210] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.203214] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.203331] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.203335] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.204095] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.204100] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.204289] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.204293] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.204409] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.204412] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.204638] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.204643] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.205056] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.205060] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.205705] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.205711] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.206134] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.206139] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.206379] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.206383] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.206475] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.206478] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.206563] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.206566] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.206663] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.206667] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.206760] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.206764] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.206857] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.206861] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.206956] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.206959] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.207061] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.207064] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.207166] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.207170] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.207267] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.207270] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.209078] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.209085] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.209189] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.209194] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.209287] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.209291] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.209389] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.209392] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.209487] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.209491] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.209585] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.209602] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.209687] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.209690] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.209793] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.209797] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.209880] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.209884] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.209991] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.210013] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.210102] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.210105] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.210200] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.210204] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.210943] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.210950] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.211047] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.211050] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.211146] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.211150] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.211245] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.211249] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.211395] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.211399] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.211795] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.211800] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.215727] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.215734] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.215822] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.215826] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.215917] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.215921] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.216018] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.216022] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.216115] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.216119] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.216215] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.216219] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.216329] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.216333] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.216434] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.216438] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.216541] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.216545] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.216643] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.216647] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.216748] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.216752] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.216851] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.216855] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.216950] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.216954] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.217068] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.217072] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.217208] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.217214] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.217317] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.217321] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.217417] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.217421] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.217511] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.217515] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.217608] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.217612] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.217704] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.217709] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.217799] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.217804] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.217911] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.217915] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.218004] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.218008] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.218098] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.218102] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.218198] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.218203] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.218300] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.218304] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.218400] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.218404] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.218498] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.218502] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.218599] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.218603] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.218695] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.218699] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.218792] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.218797] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.218889] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.218894] brcmf_fweh_event_worker: event handler failed (69)
[ 2708.218978] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2708.218983] brcmf_fweh_event_worker: event handler failed (69)
[ 2710.367414] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2710.367421] brcmf_run_escan: error (-52)
[ 2710.367425] brcmf_cfg80211_scan: scan error (-52)
[ 2711.403753] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2711.403779] brcmf_fweh_event_worker: event handler failed (69)
[ 2711.403885] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2711.403892] brcmf_fweh_event_worker: event handler failed (69)
[ 2711.403983] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2711.403987] brcmf_fweh_event_worker: event handler failed (69)
[ 2711.404088] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2711.404091] brcmf_fweh_event_worker: event handler failed (69)
[ 2711.407121] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2711.407126] brcmf_fweh_event_worker: event handler failed (69)
[ 2711.431158] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2711.431167] brcmf_fweh_event_worker: event handler failed (69)
[ 2711.431602] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2711.431606] brcmf_fweh_event_worker: event handler failed (69)
[ 2711.431708] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2711.431711] brcmf_fweh_event_worker: event handler failed (69)
[ 2711.459091] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2711.459099] brcmf_fweh_event_worker: event handler failed (69)
[ 2711.507611] brcmf_cfg80211_escan_handler: scan not ready, bssidx=0
[ 2711.507623] brcmf_fweh_event_worker: event handler failed (69)
[ 2721.611711] brcmf_cfg80211_escan: Connecting: status (3)
[ 2721.611725] brcmf_cfg80211_scan: scan error (-11)
[ 2722.613337] brcmf_cfg80211_escan: Connecting: status (3)
[ 2722.613351] brcmf_cfg80211_scan: scan error (-11)
[ 2723.614981] brcmf_cfg80211_escan: Connecting: status (3)
[ 2723.614991] brcmf_cfg80211_scan: scan error (-11)
[ 2724.616539] brcmf_cfg80211_escan: Connecting: status (3)
[ 2724.616548] brcmf_cfg80211_scan: scan error (-11)
[ 2725.618096] brcmf_cfg80211_escan: Connecting: status (3)
[ 2725.618105] brcmf_cfg80211_scan: scan error (-11)
[ 2726.619136] brcmf_cfg80211_escan: Connecting: status (3)
[ 2726.619145] brcmf_cfg80211_scan: scan error (-11)
[ 2727.620690] brcmf_cfg80211_escan: Connecting: status (3)
[ 2727.620699] brcmf_cfg80211_scan: scan error (-11)
[ 2728.622246] brcmf_cfg80211_escan: Connecting: status (3)
[ 2728.622256] brcmf_cfg80211_scan: scan error (-11)
[ 2729.623851] brcmf_cfg80211_escan: Connecting: status (3)
[ 2729.623860] brcmf_cfg80211_scan: scan error (-11)
[ 2730.625406] brcmf_cfg80211_escan: Connecting: status (3)
[ 2730.625415] brcmf_cfg80211_scan: scan error (-11)
[ 2731.626957] brcmf_cfg80211_escan: Connecting: status (3)
[ 2731.626967] brcmf_cfg80211_scan: scan error (-11)
[ 2732.628024] brcmf_cfg80211_escan: Connecting: status (3)
[ 2732.628036] brcmf_cfg80211_scan: scan error (-11)
[ 2758.263819] Modules linked in: brcmfmac brcmutil cfg80211 rtsx_usb_ms memstick nls_iso8859_1 snd_soc_sst_broadwell intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_soc_sst_haswell_pcm coretemp snd_soc_sst_ipc kvm_intel snd_soc_sst_dsp kvm irqbypass crct10dif_pclmul crc32_pclmul aesni_intel hid_multitouch aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_soc_rt286 snd_hda_codec_hdmi input_leds joydev snd_soc_rl6347a snd_soc_core snd_hda_intel snd_hda_codec serio_raw snd_hda_core snd_hwdep snd_compress ac97_bus snd_pcm_dmaengine snd_seq_midi snd_seq_midi_event mei_me snd_pcm mei snd_rawmidi lpc_ich snd_seq snd_seq_device snd_timer snd 8250_fintek soundcore dw_dmac snd_soc_sst_acpi dw_dmac_core i2c_designware_platform i2c_designware_core 8250_dw spi_pxa2xx_platform acpi_pad tpm_crb mac_hid
[ 2758.263911]  parport_pc ppdev lp parport autofs4 hid_generic uas usbhid hid usb_storage rtsx_usb_sdmmc rtsx_usb mmc_block i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm psmouse ahci libahci wmi video sdhci_acpi sdhci fjes [last unloaded: brcmutil]
[ 2758.439844] brcmf_cfg80211_reg_notifier: not a ISO3166 code
[ 2766.492378] brcmf_sdio_bus_rxctl: resumed on timeout
[ 2776.629090] brcmf_cfg80211_escan: Connecting: status (3)
[ 2776.629101] brcmf_cfg80211_scan: scan error (-11)
[ 2777.630695] brcmf_cfg80211_escan: Connecting: status (3)
[ 2777.630724] brcmf_cfg80211_scan: scan error (-11)
[ 2778.632470] brcmf_cfg80211_escan: Connecting: status (3)
[ 2778.632481] brcmf_cfg80211_scan: scan error (-11)
[ 2779.634127] brcmf_cfg80211_escan: Connecting: status (3)
[ 2779.634136] brcmf_cfg80211_scan: scan error (-11)
[ 2780.635726] brcmf_cfg80211_escan: Connecting: status (3)
[ 2780.635739] brcmf_cfg80211_scan: scan error (-11)
[ 2781.637390] brcmf_cfg80211_escan: Connecting: status (3)
[ 2781.637399] brcmf_cfg80211_scan: scan error (-11)
[ 2782.639156] brcmf_cfg80211_escan: Connecting: status (3)
[ 2782.639173] brcmf_cfg80211_scan: scan error (-11)
[ 2783.640794] brcmf_cfg80211_escan: Connecting: status (3)
[ 2783.640807] brcmf_cfg80211_scan: scan error (-11)
[ 2784.642460] brcmf_cfg80211_escan: Connecting: status (3)
[ 2784.642471] brcmf_cfg80211_scan: scan error (-11)
[ 2785.644148] brcmf_cfg80211_escan: Connecting: status (3)
[ 2785.644160] brcmf_cfg80211_scan: scan error (-11)
[ 2786.645103] brcmf_cfg80211_escan: Connecting: status (3)
[ 2786.645124] brcmf_cfg80211_scan: scan error (-11)
[ 2787.646794] brcmf_cfg80211_escan: Connecting: status (3)
[ 2787.646803] brcmf_cfg80211_scan: scan error (-11)
[ 2788.648496] brcmf_cfg80211_escan: Connecting: status (3)
[ 2788.648519] brcmf_cfg80211_scan: scan error (-11)
[ 2789.650418] brcmf_cfg80211_escan: Connecting: status (3)
[ 2789.650428] brcmf_cfg80211_scan: scan error (-11)
[ 2790.540907] brcmf_cfg80211_reg_notifier: not a ISO3166 code
bradley@kangaroo:~$ 

```

---

### Post by jeremy31 on 2016-07-06
When you edited the file did you see some strange characters at the beginning of the file?
```
\00\00\00#Sample variables file for BCM94324A1 iPA+iLNA FCBGA REF board
```

See if it helps to delete the ```
\00\00\00
``` or just delete the entire line as it is just a comment.  If that doesn't help post result for ```
ls /sys/firmware/efi/efivars | grep nvram
``` as the firmware file might be already present and justs needed to get moved and renamed

---

### Post by chili555 on 2016-07-06
Jeremy-

His dmesg says:> brcmf_sdio_drivestrengthinit: No SDIO Drive strength init done for [COLOR="#FF0000"]chip 4324[/COLOR] rev 5 pmurev 17However, the txt file we downloaded says:> devid=0x4374
boardtype=0x5f0
boardrev=0x1200
boardflags=0x201
I suggest that our OP change the file to read:> devid=0x[COLOR="#FF0000"]4324[/COLOR]
boardtype=0x5f0
boardrev=0x1200
boardflags=0x201
I'm not quite sure what else to try.

---

### Post by jeremy31 on 2016-07-06
> **chili555 said:**
> Jeremy-

His dmesg says:However, the txt file we downloaded says:I suggest that our OP change the file to read:I'm not quite sure what else to try.

I hope the nvram file can be found as that should work without changing anything.  If I remember correctly the macaddress setting didn't need to be changed as the one in the file is just a backup and the actual MAC is hard coded into the card

[https://wireless.wiki.kernel.org/en/users/drivers/brcm80211#firmware_installation1](https://wireless.wiki.kernel.org/en/users/drivers/brcm80211#firmware_installation1) under nvram from EFI but some users don't have this file but I hope bradley does

---

### Post by chili555 on 2016-07-06
Thanks. The more I learn about Broadcoms, the less I know, it seems.

---

### Post by bradleypariah on 2016-07-07
> **jeremy31 said:**
> When you edited the file did you see some strange characters at the beginning of the file?

Yes, and I deleted the extra characters as you suggested.  No change.

Here is that list output:

```
nvram-74b00bd9-805a-4d61-b51f-43268123d113
```

---

### Post by chili555 on 2016-07-07
I believe Jeremy and I will be interested to see:```
cat /sys/firmware/efi/efivars/nvram-74b00bd9-805a-4d61-b51f-43268123d113  
```Thanks.

---

### Post by jeremy31 on 2016-07-08
That would be nice to see, feel welcome to change what is after macaddress

---

### Post by bradleypariah on 2016-07-11
Note - this was run when my USB D-Link was plugged in.  I needed internet to download a couple things.

```
bradley@kangaroo:~$ cat /sys/firmware/efi/efivars/nvram-74b00bd9-805a-4d61-b51f-43268123d113
#---------------------------------------------------------------------------------------------------------------------
# NVRAM file for BCM94324B4 iPA+iLNA FCBGA NGFF_1630 board
# Release Version: ffox77h462nvram-v02
#---------------------------------------------------------------------------------------------------------------------
devid=0x4374
boardtype=0x5f0
boardrev=0x1200
boardflags=0x201
boardflags2=0x00800000
macaddr=aa:bb:cc:dd:ee:ff
sromrev=9
#On board crystal frequency in KHz
xtalfreq=37400
ag0=0x2
ag1=0x2
ag2=0xff
ag3=0xff
txchain=0x3
rxchain=0x3
aa2g=3
aa5g=3
#[NVRAM ONLY]
ccode=ALL
regrev=0
nocrc=1
ledbh0=0xff
ledbh1=0xff
ledbh2=0xff
ledbh3=0xff
leddc=0xffff
pa2gw0a0=0xFFa6   
pa2gw1a0=0x134a   
pa2gw2a0=0xFEcd   
pa2gw0a1=0xFFd5   
pa2gw1a1=0x1647   
pa2gw2a1=0xFEd9   
maxp2ga0=70
maxp2ga1=70
maxp5ga0=68
maxp5ga1=68
maxp5gha0=68
maxp5gha1=68
maxp5gla0=68
maxp5gla1=68
pa0itssit=62
pa1itssit=62
antswctl2g=0x9
antswctl5g=0xa
antswitch=0x0
subband5gver=0
pa5gw0a0=0xffaf   
pa5gw1a0=0x11ed   
pa5gw2a0=0xfee3   
pa5gw0a1=0xffBb   
pa5gw1a1=0x12f7   
pa5gw2a1=0xfee5   
pa5glw0a0=0xFFb0   
pa5glw1a0=0x127d   
pa5glw2a0=0xFEdb   
pa5glw0a1=0xFF97   
pa5glw1a1=0x1121    
pa5glw2a1=0xFebd   
pa5ghw0a0=0xffaf   
pa5ghw1a0=0x116a   
pa5ghw2a0=0xfee9   
pa5ghw0a1=0xffb6   
pa5ghw1a1=0x126f   
pa5ghw2a1=0xfee4   
extpagain2g=2
extpagain5g=2
pdetrange2g=2
pdetrange5g=2
triso2g=4
triso5g=5
tssipos2g=1
tssipos5g=1
cckbw202gpo=0x0
cckbw20ul2gpo=0x0
legofdmbw202gpo=0x33311111
legofdmbw20ul2gpo=0x33311111
mcsbw202gpo=0x55533333
mcsbw20ul2gpo=0x55533333
mcsbw402gpo=0x55533333
legofdmbw205glpo=0x22200000
legofdmbw20ul5glpo=0x22200000
legofdmbw205gmpo=0x22200000
legofdmbw20ul5gmpo=0x22200000
legofdmbw205ghpo=0x22200000
legofdmbw20ul5ghpo=0x22200000
mcsbw205glpo=0x44422222
mcsbw20ul5glpo=0x44422222
mcsbw405glpo=0x44422222
mcsbw205gmpo=0x44422222
mcsbw20ul5gmpo=0x44422222
mcsbw405gmpo=0x44422222
mcsbw205ghpo=0x44422222
mcsbw20ul5ghpo=0x44422222
mcsbw405ghpo=0x44422222
mcs32po=0x5555
legofdm40dupp=0x2222
itt2ga0=0x20
itt5ga0=0x3e
itt2ga1=0x20
itt5ga1=0x3e
tempthresh=120
usbepnum=0x2
muxenab=0x0
noisecaloffset=14
noisecaloffset5g=14
rssicorrnorm_core0=0x2004
rssicorrnorm_core1=0x2004
rssicorrnorm_core0_5g1=0x2203
rssicorrnorm_core0_5g2=0x1f03
rssicorrnorm_core0_5g3=0x1903
rssicorrnorm_core1_5g1=0x2a03
rssicorrnorm_core1_5g2=0x2303
rssicorrnorm_core1_5g3=0x1d03
triso5g_l_c0=5
triso5g_l_c1=5
triso5g_m_c0=5
triso5g_m_c1=5
triso5g_h_c0=5
triso5g_h_c1=5
#for mfgc
otpimagesize=232
btc_params95=9
#Out-of-band GPIO wakeup
sd_gpout=0
sd_gpval=1
sd_gpdc=0
bradley@kangaroo:~$


```

---

### Post by jeremy31 on 2016-07-11
```
sudo cp /sys/firmware/efi/efivars/nvram-74b00bd9-805a-4d61-b51f-43268123d113 /lib/firmware/brcm/brcmfmac43241b4-sdio.txt
```
Reboot

---

### Post by bradleypariah on 2016-07-14
No change, I'm afraid.  :(

---

### Post by jeremy31 on 2016-07-15
Please run the wireless script again and post the new results

---

### Post by bradleypariah on 2016-07-15
I'm sorry if I'm being ignorant, but I don't know which script you're suggesting I run again.  There's been so many so far.

---

### Post by jeremy31 on 2016-07-16
See the wireless script link in my signature

---

### Post by bradleypariah on 2016-08-01
Sorry for the delay, I hope you're still out there.  I have been out of town.

```


########## wireless info START ##########

Report from: 01 Aug 2016 07:20 PDT -0700

Booted last: 01 Aug 2016 00:00 PDT -0700

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-28-generic #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 1477:1007  
Bus 001 Device 004: ID 04f2:0963 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0424:2137 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              737280  3 rt2x00lib,rt2x00usb,rt2800lib
crc_ccitt              16384  1 rt2800lib
brcmfmac              290816  0
brcmutil               16384  1 brcmfmac
cfg80211              565248  3 brcmfmac,mac80211,rt2x00lib
snd_soc_rt286          36864  1 snd_soc_sst_broadwell
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_soc_core          212992  3 snd_soc_sst_haswell_pcm,snd_soc_sst_broadwell,snd_soc_rt286
snd_pcm               106496  8 snd_soc_core,snd_hda_codec_hdmi,snd_soc_sst_haswell_pcm,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3679 errors:0 dropped:3679 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1305299 (1.3 MB)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=31 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       710     1  0 06:51 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corp.
GENERAL.PRODUCT:                        BCM43241 WLAN card
GENERAL.DRIVER:                         brcmfmac_sdio
GENERAL.DRIVER-VERSION:                 6.10.197.71
GENERAL.FIRMWARE-VERSION:               01-882d2634
GENERAL.HWADDR:                         <MAC 'wlan0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/INT3436:00/mmc_host/mmc0/mmc0:0001/mmc0:0001:1/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b54c8a70-61f2-47d0-bdb4-d2490fac3fa7 | Liteshow4 1

SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
Liteshow4            <MAC 'Liteshow4' [AC4]>  Infra  4     2427 MHz  54 Mbit/s  99      &#9602;&#9604;&#9606;&#9608;  WPA2         no        


##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Liteshow4]] (600 root)
[connection] id=Liteshow4 | type=wifi | permissions=user:bradley:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Liteshow4
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/JBSMONDO-43270]] (600 root)
[connection] id=JBSMONDO-43270 | type=wifi | permissions=user:bradley:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=JBSMONDO-43270
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Liteshow4 1]] (600 root)
[connection] id=Liteshow4 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF1]> | mac-address-blacklist= | ssid=Liteshow4
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      7   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      7   APs on   Frequency:2.462 GHz (Channel 11)
      2   APs on   Frequency:5.18 GHz (Channel 36)
      4   APs on   Frequency:5.22 GHz (Channel 44)
      3   APs on   Frequency:5.24 GHz (Channel 48)
      1   APs on   Frequency:5.745 GHz (Channel 149)
      6   APs on   Frequency:5.785 GHz (Channel 157)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Liteshow4' [AC4]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Liteshow4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 276ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CD175F3067617C23A4A79F3
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     FADD78F4B0B6C8F4DDFA8E5
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 

[rt2800lib]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 

[rt2x00lib]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[brcmfmac]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4354-sdio.txt
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.txt
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.txt
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.txt
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.txt
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.txt
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.txt
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.txt
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.txt
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.txt
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b5-sdio.txt
firmware:       brcm/brcmfmac43241b5-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.txt
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.txt
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.txt
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac4371-pcie.txt
firmware:       brcm/brcmfmac4371-pcie.bin
firmware:       brcm/brcmfmac4366b-pcie.txt
firmware:       brcm/brcmfmac4366b-pcie.bin
firmware:       brcm/brcmfmac4365b-pcie.txt
firmware:       brcm/brcmfmac4365b-pcie.bin
firmware:       brcm/brcmfmac4358-pcie.txt
firmware:       brcm/brcmfmac4358-pcie.bin
firmware:       brcm/brcmfmac43570-pcie.txt
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.txt
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac4350-pcie.txt
firmware:       brcm/brcmfmac4350-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.txt
firmware:       brcm/brcmfmac43602-pcie.bin
srcversion:     394D104EE5D4CED7AA9D01D
depends:        brcmutil,cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           txglomsz:maximum tx packet chain size [SDIO] (int)
parm:           feature_disable:Disable features (int)
parm:           alternative_fw_path:string
parm:           debug:level of debug output (int)
parm:           p2pon:enable legacy p2p management functionality (int)
parm:           fcmode:mode of firmware signalled flow control (int)
parm:           roamoff:do not use internal roaming engine (int)

[brcmutil]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 

[cfg80211]
filename:       /lib/modules/4.4.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800usb]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

grep: /sys/module/brcmfmac/parameters/alternative_fw_path: Permission denied
grep: /sys/module/brcmfmac/parameters/debug: Permission denied
grep: /sys/module/brcmfmac/parameters/fcmode: Permission denied
grep: /sys/module/brcmfmac/parameters/roamoff: Permission denied
[brcmfmac]

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 1784.059407] brcmf_fweh_event_worker: event handler failed (69) (repeated 44 times)
[ 1788.185391] brcmf_sdio_bus_rxctl: resumed on timeout
[ 1788.185402] brcmf_run_escan: error (-52)
[ 1791.256832] brcmf_fweh_event_worker: event handler failed (69) (repeated 5 times)

########## wireless info END ############


```

---

### Post by jeremy31 on 2016-08-01
Can you post the result of ```
cat /bus/platform/drivers/sdhci-acpi/INT33BB:00/power/control
```

---

### Post by bradleypariah on 2016-08-01
```
cat: '/bus/platform/drivers/sdhci-acpi/INT33BB:00/power/control': No such file or directory
```

---

### Post by jeremy31 on 2016-08-01
How about ```
ls /bus/platform/drivers/sdhci-acpi/
```

---

### Post by bradleypariah on 2016-08-02
```
ls: cannot access '/bus/platform/drivers/sdhci-acpi/': No such file or directory
```

---

### Post by jeremy31 on 2016-08-02
See if there is something at ```
ls /sys/bus/acpi/drivers/sdhci-acpi/
```

---

### Post by bradleypariah on 2016-08-03
```
ls: cannot access '/sys/bus/acpi/drivers/sdhci-acpi/': No such file or directory
```

---

### Post by jeremy31 on 2016-08-03
```
ls /sys/bus/platform/drivers/sdhci-acpi/
```
And if it shows ```
INT33BB:00
``` as a directory then do 
```
cat sys/bus/platform/drivers/sdhci-acpi/INT33BB:00/power/control
``` and post the output

---

### Post by bradleypariah on 2016-08-04
Output of your code showed
```
bind  INT3436:00  module  uevent  unbind
```

Output of 
```
cat sys/bus/platform/drivers/sdhci-acpi/INT3436:00/power/control
```

says
```
cat: 'sys/bus/platform/drivers/sdhci-acpi/INT3436:00/power/control': No such file or directory
```

BTW - The WiFi manager has a new behavior.  It randomly gives me the "WiFi networks available" popup, and it my network is listed, but entering the password just leads to a failed attempt to connect.

---

### Post by jeremy31 on 2016-08-04
Try ```
cat /sys/bus/platform/drivers/sdhci-acpi/INT3436:00/power/control
```
Or use the file explorer to go to /sys/bus/platform/drivers/sdhci-acpi/INT3436:00 and see if the power folder is there with a control file

---

### Post by bradleypariah on 2016-08-05
```
on
```

---


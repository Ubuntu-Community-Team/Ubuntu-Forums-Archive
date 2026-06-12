---
title: "Broadcom wireless 14.04 - 4.4 kernel"
date: 2017-06-08
forum: Networking &amp; Wireless
---

### Post by nvidiot2 on 2017-06-08
Hi everyone,

I've got a Broadcom wireless card that I can't seem to get working.

iwconfig does not show the adapter. When I type 'sudo modprobe wl' I get the following errors in dmesg
```

[ 2869.159430] wl: Unknown symbol cfg80211_inform_bss_frame_data (err 0)
[ 2869.159492] wl: Unknown symbol cfg80211_scan_done (err 0)
[ 2869.159561] wl: Unknown symbol cfg80211_disconnected (err 0)
[ 2869.159595] wl: Unknown symbol wiphy_new_nm (err 0)
[ 2869.159621] wl: Unknown symbol wiphy_register (err 0)
[ 2869.159642] wl: Unknown symbol cfg80211_put_bss (err 0)
[ 2869.159656] wl: Unknown symbol cfg80211_roamed (err 0)
[ 2869.159676] wl: Unknown symbol cfg80211_gtk_rekey_notify (err 0)
[ 2869.159698] wl: Unknown symbol cfg80211_ibss_joined (err 0)
[ 2869.159722] wl: Unknown symbol cfg80211_michael_mic_failure (err 0)
[ 2869.159735] wl: Unknown symbol cfg80211_connect_result (err 0)
[ 2869.159764] wl: Unknown symbol wiphy_unregister (err 0)
[ 2869.159788] wl: Unknown symbol cfg80211_get_bss (err 0)
[ 2869.159810] wl: Unknown symbol __ieee80211_get_channel (err 0)
[ 2869.159851] wl: Unknown symbol ieee80211_channel_to_frequency (err 0)
[ 2869.159871] wl: Unknown symbol cfg80211_report_wowlan_wakeup (err 0)
[ 2869.159889] wl: Unknown symbol cfg80211_inform_bss_data (err 0)
[ 2869.159904] wl: Unknown symbol ieee80211_frequency_to_channel (err 0)
[ 2869.159928] wl: Unknown symbol wiphy_free (err 0)

```

I've reinstalled bcmwl-kernel-source several times, even trying more recent versions. They all give the same errors in dmesg.
Tested versions (aside from the one that apt installs by default)
```

bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu11_amd64.deb     
bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu1-2.1_amd64.deb
bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu8_amd64.deb      
bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu2_amd64.deb
bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu1-1.1_amd64.deb

```

Kernel version:
4.4.0-78-generic #99~14.04.2-Ubuntu SMP Thu Apr 27 18:49:46 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
Ubuntu version:
14.04.5 LTS

lspci output:
```

03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Dell Device [1028:0014]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 10
    Region 0: Memory at f7c00000 (64-bit, non-prefetchable) [size=16K]

```

---

### Post by chili555 on 2017-06-08
Please show us:```
sudo dkms status
uname -r
```Thanks.

---

### Post by nvidiot2 on 2017-06-18
sudo dkms status
```
bbswitch, 0.7, 3.13.0-119-generic, x86_64: installed
bbswitch, 0.7, 4.4.0-72-generic, x86_64: installed
bbswitch, 0.7, 4.4.0-78-generic, x86_64: installed
bcmwl, 6.30.223.248+bdcom, 3.13.0-119-generic, x86_64: installed
bcmwl, 6.30.223.248+bdcom, 4.4.0-78-generic, x86_64: installed
nvidia-340, 340.102, 3.13.0-119-generic, x86_64: installed
nvidia-340, 340.102, 4.4.0-72-generic, x86_64: installed
nvidia-340, 340.102, 4.4.0-78-generic, x86_64: installed
virtualbox, 4.3.36, 3.13.0-119-generic, x86_64: installed
virtualbox, 4.3.36, 4.4.0-72-generic, x86_64: installed
virtualbox, 4.3.36, 4.4.0-78-generic, x86_64: installed

```

uname -r
```
4.4.0-78-generic
```

---

### Post by praseodym on 2017-06-18
The 248 driver is too old and buggy, try a newer one:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-3_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-3_all.deb 
```

---

### Post by nvidiot2 on 2017-06-20
The [COLOR=#000000][FONT=&amp]broadcom-sta-dkms_6.30.223.271-3_all.deb driver gives the same errors :(
[/FONT][/COLOR]

---

### Post by jeremy31 on 2017-06-20
Post results for ```
modinfo cfg80211
```

---

### Post by nvidiot2 on 2017-06-22
```
modinfo: ERROR: Module cfg80211 not found.
```

---


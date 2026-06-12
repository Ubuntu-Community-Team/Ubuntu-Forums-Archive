---
title: "Wi-fi hard blocked in ubuntu 16.04 on HP laptop. Hardware key doesn't work"
date: 2017-02-20
forum: Networking &amp; Wireless
---

### Post by xprienzo on 2017-02-20
Hi,

I recently installed ubuntu 16.04 on my system and found that wi-fi was not working at all because of a hard block. A quick google search showed that this was a common problem with Ralink RT3290 and tried whatever I could find. Unfortunately nothing works for me. Using wireless is important for me because I have no wired connection and have to use phone hotspots for internet connection. Any help will be appreciated ^^

---

### Post by chili555 on 2017-02-20
What does this tell us?```
rfkill list all
```

---

### Post by xprienzo on 2017-02-20
```
$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

Also sudo rfkill unblock all doesn't work.

---

### Post by chili555 on 2017-02-20
May we see:```
lsmod | grep -e hp -e wmi
```What exact model HP is this?

---

### Post by xprienzo on 2017-02-20
```
snd_rawmidi            32768  1 snd_seq_midisnd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
hp_wireless            16384  0
shpchp                 36864  0
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau
```

It's a HP 15-r022TX.

---

### Post by chili555 on 2017-02-21
Let's try a couple of things. First:```
sudo modprobe -r hp-wireless
```Now, is your wireless key working?

If not, try:```
sudo modprobe hp-wmi
```Is the wireless key working now?

If one of these helps, we can write a few lines in the system to make it permanent.

You might also try pressing the wireless key during boot, as the BIOS splash screen is displayed, to see if you then boot up not hard blocked. It may be similar to this: [http://support.hp.com/doc-images/774/c05350724.jpg](http://support.hp.com/doc-images/774/c05350724.jpg)

---

### Post by xprienzo on 2017-02-21
They both did work and now rfkill list all shows this
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

Unfortunately it still showed wifi to be disabled on the interface, I guess it'd need a restart to fix that.

Edit: I'm running on UEFI so there is no splash screen.

Edit 2: Apparently it won't activate because the firmware is missing.

[IMG]http://i67.tinypic.com/1zwfb7t.png[/IMG]

---

### Post by chili555 on 2017-02-21
Let's fix the rfkill problem first:```
sudo -i
echo hp-wmi  >>  /etc/modules
echo "blacklist hp-wireless"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if the wireless is hard blocked and, if so, the wireless key works as expected.>  Apparently it won't activate because the firmware is missing.Let's see:```
dmesg | grep -i rt2
lsusb
lspci -nnk | grep 0280 -A2
```

---

### Post by xprienzo on 2017-02-21
> **chili555 said:**
> 
Reboot and tell us if the wireless is hard blocked and, if so, the wireless key works as expected.
Yeah, It did work and it was not hard blocked later.

The latter:
```
xprienzo@xprienzo-HP-15-Notebook-PC:~$ dmesg | grep -i rt2[   12.097759] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   12.105836] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   13.560706] rt2800pci 0000:0a:00.0 wlo1: renamed from wlan0
[   34.885470] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   35.165620] rt2800pci 0000:0a:00.0: Direct firmware load for rt3290.bin failed with error -2
[   35.165628] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware
xprienzo@xprienzo-HP-15-Notebook-PC:~$ lsusb
Bus 001 Device 003: ID 04f2:b40e Chicony Electronics Co., Ltd HP Truevision HD camera
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 002 Device 004: ID 22b8:2e24 Motorola PCS 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
xprienzo@xprienzo-HP-15-Notebook-PC:~$ lspci -nnk | grep 0280 -A2
0a:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	DeviceName:  
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]

```

---

### Post by chili555 on 2017-02-22
Let's update your firmware and see if we can get the wireless going;

```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.163_all.deb
sudo dpkg -i linux-firmware*.deb 
```
Reboot and tell us if your wireless is working.

---

### Post by xprienzo on 2017-02-22
TY, it is working now!

---

### Post by chili555 on 2017-02-22
Awesome! Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

NOTE TO SEARCHERS: I am not at all sure that the fix is always to unload hp-wireless and load hp-wmi. Try it temporarily as in post #6  above before you start writing changes to the system. Not every fix applies to every system all the time!

---


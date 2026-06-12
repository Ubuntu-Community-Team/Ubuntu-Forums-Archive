---
title: "Ralink RT5390 driver problems, Lubuntu 15.04"
date: 2015-10-13
forum: Networking &amp; Wireless
---

### Post by zach.galovits on 2015-10-13
Hello all,

Forewarning, I am fairly new at using Linux OSes. I apologize in advance if I ask questions that may seem like a no-brainer.

I've just installed Lubuntu 15.04 after I accidentally erased some of my Windows 10 files and was forced to format the entire hard drive. There was a few bumps that I managed to work through. Now, I've run into one that I have no clue how to fix. The wireless card I have is just a cheap C-Net CWP-906E that uses the Ralink RT5390 Chip-set. I need to set up the driver to associate with it, but as I said before, I'm new to all this and have no idea what I'm doing when it comes to this. I've attached the wireless-info file for reference. If anything else is needed, just let me know.

[ATTACH]264929[/ATTACH]

EDIT: Yes, I have seen all teh posts regarding similar problems, but NONE of the solutions have worked.

Edit #2: I did some more digging. When I tried reinstalling altogether and starting from scratch, during the initialization of the install, it fails to load the module for some. I do not remember the error off the top of my head.

---

### Post by chili555 on 2015-10-13
> The wireless card I have is just a cheap C-Net CWP-906E that uses the Ralink RT5390 Chip-set. I need to set up the driver to associate with it, In Ubuntu 15.04, the driver the card should use is rt2800pci. You have it blacklisted!> blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090staWhy? Did it not work or sort of work or what?

If you load it, what happens?```
sudo modprobe rt2800pci
iwconfig
sudo iwlist wlan0 scan
```

---

### Post by zach.galovits on 2015-10-13
Okay. So, I've just started over from scratch. It's not working at all no matter what. When I try to load it, this is what I get.

```

zach@zach-desktop:~$ sudo modprobe rt2800pci
[sudo] password for zach:
zach@zach-desktop:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

zach@zach-desktop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

```

I've added the new wireless info with the fresh install  also.

---

### Post by chili555 on 2015-10-13
> [   15.020386] ieee80211 phy0: rt2800_init_eeprom: Error - Invalid RF chipset 0x5314 detected
[   15.020387] ieee80211 phy0: rt2x00lib_probe_dev: Error - Failed to allocate deviceAn alarming error...I am Googling and suggest you do so as well.

I will return with a proposed solution, hopefully.

---

### Post by zach.galovits on 2015-10-14
I spent most of last night and much of this morning searching for answers on those two errors. I've come up pretty much empty. Maybe you've had better luck?

---

### Post by chili555 on 2015-10-15
I suggest we try building a more recent version of the driver. With a temporary working internet connection by ethernet or whatever means possible:```
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.1.1/backports-4.1.1-1.tar.gz
tar -zxvf backports*
cd backports-4.1.1-1
make defconfig-wifi
make
sudo make install
```Reboot and tell us if it's working. In any event, please post:```
dmesg | grep rt2
```

---

### Post by zach.galovits on 2015-10-15
Well, I rebuilt the driver per your instructions, but it still isn't working.

Dmesg shows this output:

```

[    8.017876] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[    8.021694] ieee80211 phy0: rt2800_init_eeprom: Error - Invalid RF chipset 0x5314 detected
[    8.021733] ieee80211 phy0: rt2x00lib_probe_dev: Error - Failed to allocate device
[   36.584788] Modules linked in: nls_utf8 udf crc_itu_t binfmt_misc intel_rapl iosf_mbi x86_pkg_temp_thermal intel_powerclamp coretemp nvidia(POE) snd_hda_codec_hdmi snd_hda_codec_realtek kvm_intel joydev snd_hda_codec_generic kvm snd_hda_intel snd_hda_controller crct10dif_pclmul snd_hda_codec crc32_pclmul snd_hwdep ghash_clmulni_intel hid_generic usbhid drm snd_pcm hid rt2800pci(OE) aesni_intel rt2800mmio(OE) rt2800lib(OE) rt2x00pci(OE) rt2x00mmio(OE) rt2x00lib(OE) mxm_wmi mac80211(OE) cfg80211(OE) compat(OE) eeprom_93cx6 crc_ccitt aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq serio_raw snd_seq_device snd_timer lpc_ich mei_me wmi mei snd 8250_fintek nuvoton_cir rc_core soc_button_array shpchp soundcore video mac_hid parport_pc ppdev lp parport

```

---

### Post by chili555 on 2015-10-15
Aside from a replacement device, I regret I have no other suggestions.

---

### Post by zach.galovits on 2015-10-15
Well, unfortunately, a replacement device just isn't plausible right now. Thanks for the help.

---


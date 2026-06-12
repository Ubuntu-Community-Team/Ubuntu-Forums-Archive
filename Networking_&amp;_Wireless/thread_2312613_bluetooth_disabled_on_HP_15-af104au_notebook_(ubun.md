---
title: "bluetooth disabled on HP 15-af104au notebook (ubuntu 15.10)"
date: 2016-02-05
forum: Networking &amp; Wireless
---

### Post by dalekky on 2016-02-05
I need some help getting this bluetooth to work.
This is a brand new laptop with fresh install of Wily. There is definitely bluetooth device inside the laptop.
I can't figure out how to get it enabled. Somehow after hours of Googling and trying suggestions it seemed to come on at random after a reboot and was working, but this morning when I booted up it was disabled again and won't come back on. I have no idea how it managed to come on last night.

Here are some details:

output from lsusb
```

Bus 004 Device 003: ID 04f2:b509 Chicony Electronics Co., Ltd 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

output from lspci

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1566
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.5 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1537
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 39)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
02:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)

```

rfkill list

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

hciconfig -a

```
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 60:6D:C7:DD:5B:F8  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING 
    RX bytes:903 acl:0 sco:0 events:38 errors:0
    TX bytes:392 acl:0 sco:0 commands:38 errors:0
    Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'BCM43142A'
    Class: 0x000000
    Service Classes: Unspecified
    Device Class: Miscellaneous, 
    HCI Version: 4.0 (0x6)  Revision: 0x0
    LMP Version: 4.0 (0x6)  Subversion: 0x210b
    Manufacturer: Broadcom Corporation (15)

```

hcitool dev

```
Devices:
    hci0    60:6D:C7:DD:5B:F8
```

If there is anything else I can post which might help, please let me know and I will post it asap.

---

### Post by jeremy31 on 2016-02-05
Post ```
dmesg | egrep -i 'blue|firm'; rfkill list all
```

Are you also using Windows?

---

### Post by dalekky on 2016-02-05
I just did a "sudo modprode -r btusb" followed by a "sudo modprobe btusb" and the bluetooth indicator magically appeared at top of screen and bluetooth became enabled again.
I shut down the computer. Completely powered off. Then restarted and bluetooth was still enabled.

I have no idea why this seemed to work. Can anyone explain?

Jeremy... Bluetooth magically started working again, but here is the output of the command you asked. Also I am not running Windows. This laptop came with Windows 10 factory installed, but I never gave it a chance to launch. I went direct to BIOS on first boot after I bought it to enable me to boot from Ubuntu installer USB stick. So it's never had Windows run on it since I've owned it. ;)
```

[    0.333012] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.337968] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.338807] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.489952] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    1.935073] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    2.045419] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
[   11.022405] Bluetooth: Core ver 2.20
[   11.022433] Bluetooth: HCI device and connection manager initialized
[   11.022441] Bluetooth: HCI socket layer initialized
[   11.022446] Bluetooth: L2CAP socket layer initialized
[   11.022455] Bluetooth: SCO socket layer initialized
[   11.389871] Bluetooth: hci0: BCM: chip id 70
[   11.389879] Bluetooth: hci0: BCM (001.001.011) build 0000
[   11.510875] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   11.510889] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   13.511688] Bluetooth: hci0 command 0x1003 tx timeout
[   19.527193] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.527198] Bluetooth: BNEP filters: protocol multicast
[   19.527206] Bluetooth: BNEP socket layer initialized
[   28.709746] Bluetooth: RFCOMM TTY layer initialized
[   28.709760] Bluetooth: RFCOMM socket layer initialized
[   28.709768] Bluetooth: RFCOMM ver 1.11
[  262.165076] Modules linked in: rfcomm bnep nls_iso8859_1 wl(POE) uvcvideo videobuf2_vmalloc snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hda_core videobuf2_memops snd_hwdep videobuf2_core v4l2_common videodev btusb snd_pcm snd_seq_midi snd_seq_midi_event media btrtl btbcm btintel snd_rawmidi bluetooth kvm cfg80211 snd_seq crct10dif_pclmul crc32_pclmul hp_wmi edac_core snd_seq_device sparse_keymap aesni_intel edac_mce_amd snd_timer joydev aes_x86_64 input_leds snd serio_raw lrw gf128mul glue_helper ablk_helper cryptd k10temp fam15h_power i2c_piix4 hp_wireless soundcore shpchp tpm_crb ccp mac_hid parport_pc ppdev lp parport autofs4 amdkfd amd_iommu_v2 radeon i2c_algo_bit ttm psmouse sdhci_pci drm_kms_helper sdhci ahci drm r8169 libahci mii wmi video
[  275.990697] Modules linked in: rfcomm bnep nls_iso8859_1 wl(POE) uvcvideo videobuf2_vmalloc snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hda_core videobuf2_memops snd_hwdep videobuf2_core v4l2_common videodev btusb snd_pcm snd_seq_midi snd_seq_midi_event media btrtl btbcm btintel snd_rawmidi bluetooth kvm cfg80211 snd_seq crct10dif_pclmul crc32_pclmul hp_wmi edac_core snd_seq_device sparse_keymap aesni_intel edac_mce_amd snd_timer joydev aes_x86_64 input_leds snd serio_raw lrw gf128mul glue_helper ablk_helper cryptd k10temp fam15h_power i2c_piix4 hp_wireless soundcore shpchp tpm_crb ccp mac_hid parport_pc ppdev lp parport autofs4 amdkfd amd_iommu_v2 radeon i2c_algo_bit ttm psmouse sdhci_pci drm_kms_helper sdhci ahci drm r8169 libahci mii wmi video
[  386.488621] Modules linked in: rfcomm bnep nls_iso8859_1 wl(POE) uvcvideo videobuf2_vmalloc snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hda_core videobuf2_memops snd_hwdep videobuf2_core v4l2_common videodev btusb snd_pcm snd_seq_midi snd_seq_midi_event media btrtl btbcm btintel snd_rawmidi bluetooth kvm cfg80211 snd_seq crct10dif_pclmul crc32_pclmul hp_wmi edac_core snd_seq_device sparse_keymap aesni_intel edac_mce_amd snd_timer joydev aes_x86_64 input_leds snd serio_raw lrw gf128mul glue_helper ablk_helper cryptd k10temp fam15h_power i2c_piix4 hp_wireless soundcore shpchp tpm_crb ccp mac_hid parport_pc ppdev lp parport autofs4 amdkfd amd_iommu_v2 radeon i2c_algo_bit ttm psmouse sdhci_pci drm_kms_helper sdhci ahci drm r8169 libahci mii wmi video
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by jeremy31 on 2016-02-05
It might be an issue with the firmware upload.  Some Atheros bluetooth had issues a year or so ago with the timing of a firmware upload and they would only work about 1/3 of the time after a restart

---

### Post by dalekky on 2016-02-05
I just rebooted the laptop 3 times in a row and each time the bluetooth was working normally. Hopefully it will stay that way.

---

### Post by jeremy31 on 2016-02-05
If it gives too many issues, install 14.04 or wait for 16.04 as 15.10 is a short term support release

---

### Post by dalekky on 2016-02-06
Yep.. it's gone disabled again. Seems to do it at random. Completely unpredictable.
I have a bluetooth usb dongle that works should I need it.
In the mean time I will just wait for 16.04 to come out and cross my fingers.

---

### Post by jeremy31 on 2016-02-06
One thing to try is ```
echo "blacklist btusb" | sudo tee /etc/modprobe.d/btusb.conf
```
Then edit /etc/rc.local ```
gksudo gedit /etc/rc.local
```
And add this above exit 0
```
sleep 30
modprobe btusb
```
Save, exit program, reboot

It should work if it is an XHCI issue with firmware loading

---

### Post by dalekky on 2016-02-07
Tried your suggestion. It did not make any noticeable difference.
The only thing I have found which makes it work is to repeatedly enter - ```
sudo modprobe -r btusb
sudo modprobe btusb
```
until the bluetooth activates.
I have no idea why this works, it just does. The number of times you need to repeat the two commands is purely random. Sometimes it works first go. Sometimes after the *n*th go.

---

### Post by jeremy31 on 2016-02-07
You have another issue that may be contributing to this issue, look through dmesg log for errors or a stack trace.  I think it may be related to the video driver(radeon) or drm

---

### Post by dalekky on 2016-02-07
Should I attach my whole dmesg log? I see a couple of items highlighted in red text next to Bluetooth entries, and a few rows of call trace.

---

### Post by jeremy31 on 2016-02-08
It would be better to paste the dmesg at paste.ubuntu.com and post the URL

---

### Post by dalekky on 2016-02-08
here it is
[http://paste.ubuntu.com/14997048/](http://paste.ubuntu.com/14997048/)

---

### Post by jeremy31 on 2016-02-08
Can you run the wireless script from the sticky post "before posting in networking and wireless"?  The issue is with the broadcom wl module

---

### Post by dalekky on 2016-02-08
Contents of wireless-info.txt is here -
[URL="http://paste.ubuntu.com/14999406/"]http://paste.ubuntu.com/14999406/

[/URL]Note that the bluetooth device decided to be enabled when I ran the script. Should I also run the script while the bluetooth has failed to enable, or would the results be the same?

---

### Post by jeremy31 on 2016-02-09
I hope Chili has some ideas on this one as the errors point to the wireless module

---

### Post by dalekky on 2016-02-11
Ok, so are we just waiting for this mysterious Chili person to offer his/her suggestions on the issue now?

---

### Post by jeremy31 on 2016-02-11
I don't know what Chili is doing but the alternative is to file a bug report and see if they can solve the Broadcom wireless issue

This might help bluetooth
```
[COLOR=#111111][FONT=Consolas]wget https://www.dropbox.com/s/olqnqevf698lddo/fw-0a5c_216d.hcd
[/FONT][/COLOR]sudo cp fw-0a5c_216d.hcd /lib/firmware/brcm/BCM.hcd
```

Reboot

---

### Post by chili555 on 2016-02-13
The chili555 person is here!

I see a few things in your wireless script that I suggest changing. 

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot and tell us if connectivity is improved. If not, please let us see another wireless_info as before.

---

### Post by dalekky on 2016-02-16
I'm not having any issues with wireless connections.
I am having an issue with the bluetooth being disabled.

---

### Post by chili555 on 2016-02-16
> **dalekky said:**
> I'm not having any issues with wireless connections.
I am having an issue with the bluetooth being disabled.Yes, I understand. However, these factors are often the difference between a good connection and a great connection and, quite often, between a good connection and no connection at all. Since these factors were so obvious in your wireless script, I thought I would mention them while jeremy31 and I continue to study your bluetooth problem. 

I must say, this is another in my catalog of favorite problems; everything looks perfect, except it doesn't work!

Please try:```
wget https://www.dropbox.com/s/olqnqevf698lddo/fw-0a5c_216d.hcd
sudo cp fw-0a5c_216d.hcd /lib/firmware/
sudo cp fw-0a5c_216d.hcd /lib/firmware/brcm/BCM43142A0-0a5c_216d.hcd
sudo modprobe -r btusb
sudo modprobe btusb
```Any improvement?

---

### Post by dalekky on 2016-02-16
ok, I'll try all the things listed in your previous messages when I get a free moment and post back all the results. ;)

---


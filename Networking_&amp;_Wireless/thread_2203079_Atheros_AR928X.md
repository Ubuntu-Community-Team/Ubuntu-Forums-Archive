---
title: "Atheros AR928X"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by Eduardo_Romaguera on 2014-02-01
Hello. 

I have a problem with my wifi. 
I have instaled ubuntu but my wifi not funtion!
Is posible to solution my problem?
Thank you.

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

for atheros wireless AR928X HP

ubuntu 12.04

lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

help me please

---

### Post by coffeecat on 2014-02-02
Not a tutorial.

*Thread moved to **Networking & Wireless**.*

---

### Post by varunendra on 2014-02-02
> **Eduardo_Romaguera said:**
> 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    **[COLOR="#FF0000"]Soft blocked: yes[/COLOR]**
    Hard blocked: no

Your wifi is currently soft blocked. Please check/try these -

[INDENT]**1)** Make sure "Enable Wireless" has a tick mark beside it in the Network Manager's drop-down menu (the network icon in the upper right corner).

**2)** If the above is okay, try this command in a termianl -
```
rfkill unblock all
```

**3)** Try the hardware switch that toggles the wireless on/off. It may be a simple physical switch or a Fn+<some key> combination. Refer to your laptop's user manual if unsure.[/INDENT]

If none of these help enabling your wifi, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Eduardo_Romaguera on 2014-02-03
Yes  VARUN , thanks you
but this don't work wiht this code.
I checked the parameters but the wifi still does not work

```
lspci -nnk | grep -iA2 net
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Packard Bell B.V. Device [1631:c216]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Quanta Microsystems, Inc EM303 802.11bgn Wireless Mini PCIe Card [AR9281] [1a32:0303]
    Kernel driver in use: ath9k
```
sudo modprobe -rfv ath9k
```
.
```
[sudo] password for durome
```

WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ath9k.conf line 2: ignoring bad line starting with 
WARNING: /etc/modprobe.d/ath9k.conf line 3: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/ath9k.conf line 4: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/ath9k.conf line 5: ignoring bad line starting with 'exit'
WARNING: /etc/modprobe.d/ath9k.conf line 6: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/ath9k.conf line 7: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist.conf.save line 1: ignoring bad line starting with 'exit'
rmmod /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
rmmod /lib/modules/3.2.0-58-generic-pae/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.2.0-58-generic-pae/kernel/net/wireless/cfg80211.ko

---

### Post by Eduardo_Romaguera on 2014-02-03
VARUN , thanks you

---

### Post by Eduardo_Romaguera on 2014-02-03
```

**** iwconfig ****
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

---

### Post by Eduardo_Romaguera on 2014-02-03
```
 
lspci -nnk | grep -iA2 net



02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Packard Bell B.V. Device [1631:c216]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Quanta Microsystems, Inc EM303 802.11bgn Wireless Mini PCIe Card [AR9281] [1a32:0303]
    Kernel driver in use: ath9k

uname -a

Linux durome-EASYNOTE-TN36 3.2.0-58-generic-pae #88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013 i686 i686 i386 GNU/Linux

lspci -nnk | grep -iA2 net

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Packard Bell B.V. Device [1631:c216]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Quanta Microsystems, Inc EM303 802.11bgn Wireless Mini PCIe Card [AR9281] [1a32:0303]
    Kernel driver in use: ath9k

lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 090c:e371 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 006 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 3D Optical Mouse

 pccardctl info

 iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

 rfkill list


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


 lsmod


Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
joydev                 17393  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
ath9k                 117356  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                86546  0 
mac80211              436493  1 ath9k
serio_raw              13027  0 
uvcvideo               67203  0 
ath9k_common           13781  1 ath9k
videodev               86588  1 uvcvideo
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_hw              391626  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178877  3 ath9k,mac80211,ath
soundcore              14635  1 snd
i915                  428248  3 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
wmi                    18744  1 acer_wmi
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
r8169                  56396  0 
usbhid                 41937  0 
hid                    81731  1 usbhid
usb_storage            39646  2 ums_realtek


```

---

### Post by varunendra on 2014-02-04
Please run the following commands in a terminal (copy-paste them to avoid typing errors) -
```
sudo rm /etc/modprobe.d/ath9k.conf
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Then reboot and see if your wifi is active or not. If not, make sure it is "Enabled" in Network Manager menu and also try the physical switch again. If still no luck, run the wireless script again and post back its fresh report (make sure to copy-paste it correctly, the last time was not complete and not in order).

And there also seems to be a wrong entry in one of your system files, although not problematic, lets get it sorted too. Please post back the outputs of -
```
ls /etc/modprobe.d/blacklist*
cat /etc/modprobe.d/blacklist.conf.save
```

---

### Post by Eduardo_Romaguera on 2014-02-05
ls /etc/modprobe.d/blacklist*

```

/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist.conf.save
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-local.conf
/etc/modprobe.d/blacklist-modem.conf
**/etc/modprobe.d/blacklist-oss.conf**
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist-watchdog.conf

```



cat /etc/modprobe.d/blacklist.conf.save

```

exit
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


```

---

### Post by Eduardo_Romaguera on 2014-02-05
Thank you very much VARUN "SOLVED" WIFI

---

### Post by varunendra on 2014-02-06
Glad it did. :)

And nothing serious, but the "blacklist.conf.save" file has a wrong entry "exit" in its first line. It is just a backup of your original blacklist.conf file. So you can safely delete this erroneous file -
```
sudo rm /etc/modprobe.d/blacklist.conf.save
```
Not going to harm if you leave it though, just an error line will keep occurring in the logs until you fix or remove it.

---


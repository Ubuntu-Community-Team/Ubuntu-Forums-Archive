---
title: "Wifi connection dropping to 0b/s until disconnect/reconnect"
date: 2016-03-27
forum: Networking &amp; Wireless
---

### Post by foxj.1994 on 2016-03-27
So I installed Kubuntu today alongside my win10 installation. I've got everything up and running but I'm having trouble with my wifi connection. Every few minutes (from 5-30, usually), the wifi starts losing speed until it eventually hits 0b/s. It doesn't disconnect, but renders the internet unusable. I have to disconnect and reconnect, and then it works perfectly fine again (for another 5-30 minutes).

My wireless adapter is a TP-LINK TL-WN822N
I'm connecting to a Sky hub downstairs (DSL).

I don't get the same issue on my windows installation (although, lately, I have been getting some issues with it saying there are missing network protocols on my PC, but I believe that to be a separate issue, I'm not sure though).

Any help at all would be much appreciated :)

---

### Post by praseodym on 2016-03-27
Hi, please open a terminal and show the outputs of these commands:
```

lsusb
lsmod
iwconfig
```

---

### Post by foxj.1994 on 2016-03-27
Oki doki :)


lsusb:
```

automaton@automaton-GA-MA770-UD3:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID abcd:1234 Unknown 
Bus 002 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lsmod:
```

automaton@automaton-GA-MA770-UD3:~$ lsmod
Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  2
ccm                    20480  2
arc4                   16384  2
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              733184  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              548864  2 mac80211,rtlwifi
fglrx               13447168  139
kvm_amd                65536  0
kvm                   512000  1 kvm_amd
input_leds             16384  0
mac_hid                16384  0
serio_raw              16384  0
k10temp                16384  0
edac_core              53248  0
edac_mce_amd           24576  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     49152  1
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
8250_fintek            16384  0
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
amd_iommu_v2           20480  1 fglrx
i2c_piix4              24576  0
shpchp                 36864  0
soundcore              16384  1 snd
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
uas                    24576  0
usb_storage            69632  1 uas
pata_acpi              16384  0
firewire_ohci          40960  0
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
pata_atiixp            16384  2
ahci                   36864  0
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  1 r8169
wmi                    20480  0
floppy                 73728  0

```

iwconfig:
```

automaton@automaton-GA-MA770-UD3:~$ iwconfig
wlxc04a0028e03e  IEEE 802.11bgn  ESSID:"SKYCDA1A"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 7C:4C:A5:13:D8:A1   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:42   Missed beacon:0


enp2s0    no wireless extensions.


lo        no wireless extensions.

```

---

### Post by praseodym on 2016-03-27
Change the driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
sudo git clone https://github.com/vincent-t/rt8192cu_dkms /usr/src/8192cu-4.0.2.9000.20130911
sudo dkms add -m 8192cu -v 4.0.2.9000.20130911
sudo dkms build -m 8192cu -v 4.0.2.9000.20130911
sudo dkms install -m 8192cu -v 4.0.2.9000.20130911 
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot

---

### Post by foxj.1994 on 2016-03-27
Thanks :)

I tried out a different driver before reading this response and it's now working fine. I used this guide (and driver):
[https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md](https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md)

It's working fine, and it seems like the same driver that you listed; but is there anything in that guide that's missed out that you'd recommend me doing? I'm still new to linux and so don't understand all the commands and the differences between those that you posted and the ones on that guide.

Thanks for the help :)

---

### Post by praseodym on 2016-03-28
No, thats all.

---

### Post by foxj.1994 on 2016-03-28
Alright thanks :)

---


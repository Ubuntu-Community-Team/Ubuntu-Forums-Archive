---
title: "Broadcom BCM4313: norm N not active"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by romung on 2015-05-06
Hi all,

My wireless is suppose to handle the N norm (lspci -vvnn | grep 14e4) :

```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
0b:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe [14e4:1680] (rev 10)
```

however iwconfig return  IEEE 802.11abg : 

```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Livebox-3EF8"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: B8:26:6C:56:3E:F8   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

I have a Dell Latitude E5510 with xubuntu 14.04.

I tried different driver and the ones currently installed are from the *firmware*-linux-*nonfree*.

Can you help me? My roommate has a MacPro and it works perfectly at full speed (Fiber line).

lsmod :

```

Module                  Size  Used by
snd_hda_codec_hdmi     46368  1 
wl                   6367819  0 
snd_hda_codec_idt      54908  1 
cfg80211              484040  1 wl
bnep                   19624  2 
rfcomm                 69160  4 
bluetooth             391136  10 bnep,rfcomm
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
snd_hda_intel          56531  3 
dcdbas                 14928  1 dell_laptop
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143187  0 
kvm                   455835  1 kvm_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ghash_clmulni_intel    13216  0 
snd                    69322  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lp                     17759  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17381  0 
serio_raw              13462  0 
intel_ips              18664  0 
i915                  784123  8 
lpc_ich                21080  0 
drm_kms_helper         55071  1 i915
soundcore              12680  1 snd
shpchp                 37032  0 
drm                   303102  4 i915,drm_kms_helper
wmi                    19177  1 dell_wmi
mei_me                 18627  0 
mei                    82276  1 mei_me
i2c_algo_bit           13413  1 i915
ppdev                  17671  0 
parport_pc             32701  0 
parport                42348  3 lp,ppdev,parport_pc
video                  19476  1 i915
mac_hid                13205  0 
tg3                   166478  0 
psmouse               106714  0 
ptp                    18933  1 tg3
firewire_ohci          40409  0 
pps_core               19382  1 ptp
ahci                   29915  3 
firewire_core          68769  1 firewire_ohci
sdhci_pci              23172  0 
libahci                32716  1 ahci
sdhci                  43015  1 sdhci_pci
crc_itu_t              12707  1 firewire_core

```

iwlist scan:

```

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: B8:26:6C:56:3E:F8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Livebox-3EF8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 54432ms ago
                    IE: Unknown: 000C4C697665626F782D33454638
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 331AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 341606000500000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8F0050F204104A0001101044000102103B00010310470010493F393D3D4AFC3DFA4C4D3F073F393D10210008536167656D636F6D10230016536167656D636F6D46617374333936355F4C42322E381024000C53475F4C42335F312E322E3110420009414E313530393146461054000800060050F204000110110000100800020006103C0001011049000600372A000120

```

Thanks

---

### Post by westie457 on 2015-05-06
Hello romung welcome to Ubuntu Forums.

Hopefully this post will help you. [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by jeremy31 on 2015-05-06
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-dkms broadcom-sta-common
```
```
sudo apt-get install firmware-b43-installer
```

Reboot

linux-firmware-nonfree has not contained the b43 firmware since late last year, it was removed because of Broadcom's license

You may also want to change the wifi router encryption settings to WPA2-AES or WPA2 only as the iwlist scan results show TKIP is being used and it is not as secure as AES(CCMP) and usually results in reduced speeds and other issues in linux

---

### Post by chili555 on 2015-05-06
> You may also want to change the wifi router encryption settings to WPA2-AES or WPA2 only as the iwlist scan results show TKIP is being used and it is not as secure as AES(CCMP) and usually results in reduced speeds and other issues in linux Yes, exactly. You may see, in the dmesg log,:```
disabling HT/VHT due to WEP/TKIP use
```HT and VHT refer to high throughput and very high throughput; what we call N!

---

### Post by romung on 2015-05-07
Thanks for helping .... I finaly found this somewhere else in the forum :

```
sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*)
```

And it made the job .... 

Thanks Guys.

---


---
title: "Query about USB wireless dongle..."
date: 2014-06-09
forum: Networking &amp; Wireless
---

### Post by Mike_Walsh on 2014-06-09
Afternoon, everybody.

I've been reviewing the forums, with a view to learning what I can about possible issues related to the TP-LINK WN725N USB wireless nano adapter (ver. 2).

I've had one of these beasties for a while now, previously running under Win XP. I've just recently switched to Ubuntu 14.04, and reading the forums, there seem to be quite a number of posts relating to various issues with this adapter.

I switched to Ubuntu about a fortnight ago; and, quite frankly, I love it! Way better than XP; faster, smoother, more responsive in every way.

My main machine is a 10-yr old Compaq Presario desktop (the SR1619UK model, or EK335-AA, for those that prefer that), running an AMD Athlon64, 3Gb of RAM, and a WD 160 Gb HDD. I also have a 12-yr old Dell Inspiron laptop, which sees occasional use (still running XP, although now dual-booting with Lubuntu, since its configuration is quite low-spec; 'Netburst' Celeron, for those 'in the know'!). :rolleyes:

Due to a problem with the USBs on the Dell, everything plugged into the USB ports, with the two exceptions of a Bluetooth dongle, and a nano wireless mouse receiver, causes it to crash, and reboot; so I use our Ethernet connection on this on the rare occasions when I use it. This is when I use the TP-LINK adapter; so I have a connection on the Compaq, while the Dell is using the Ethernet. It's also because, due to the location of the PC, it's a complete pain to try and run a second Ethernet connection to it; I nearly tore my hair out running the first one, involving lifting several carpets, door bars, etc., so I decided the wireless adapter would be a simple fix for these occasions...and it suffices.

Touch wood, the adapter seems to work OK; despite several people reporting problems with the version 2 drivers, etc; maybe I don't use it for long enough at a stretch for the problems to show up...I don't know, yet.

Anyway; my question is quite a simple one, though I rather doubt anyone would know the reason for this! Under XP, when in use, the LED would constantly flash. Under Ubuntu, the LED remains on continuously, although it's still working. 

Can anybody enlighten me as to the difference in behaviour? :p


Mike Walsh.

---

### Post by praseodym on 2014-06-09
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lsusb
lsmod
iwconfig
iwlist chan
sudo iwlist scan
```

---

### Post by Mike_Walsh on 2014-06-09
Hallo there.

Okay; returns are as follows;

```
uname -a;

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ uname -a
Linux paul-EK335AA-ABU-SR1619UK-GB540 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 
*********************************************************

lsusb;

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ lsusb
Bus 001 Device 005: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bc2:2312 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 
*********************************************************


lsmod;

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
cfg80211              484040  0 
rfcomm                 69160  8 
bnep                   19624  2 
joydev                 17381  0 
hid_logitech_dj        18581  0 
hid_generic            12548  0 
r8188eu               814658  0 
radeon               1514165  3 
snd_atiixp             19961  4 
snd_ac97_codec        130285  1 snd_atiixp
ac97_bus               12730  1 snd_ac97_codec
snd_pcm               102099  2 snd_ac97_codec,snd_atiixp
snd_page_alloc         18710  2 snd_pcm,snd_atiixp
snd_seq_midi           13324  0 
usbhid                 52570  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
hid                   106148  5 hid_generic,usbhid,hid_logitech_dj
usb_storage            62209  2 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13462  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
k8temp                 12978  0 
edac_core              62291  0 
snd                    69238  16 snd_ac97_codec,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_atiixp,snd_seq_midi
edac_mce_amd           22617  0 
soundcore              12680  1 snd
ttm                    85115  1 radeon
drm_kms_helper         52758  1 radeon
btusb                  32412  0 
drm                   302817  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
bluetooth             395423  22 bnep,btusb,rfcomm
i2c_piix4              22155  0 
shpchp                 37032  0 
mac_hid                13205  0 
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
8139too                33544  0 
firewire_ohci          40409  0 
psmouse               102222  0 
firewire_core          68769  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
8139cp                 27953  0 
mii                    13934  2 8139cp,8139too
pata_atiixp            13271  2 
sata_sil               13512  0 
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 
*********************************************************


iwconfig;

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTHub5-FWTJ"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:8A:AE:98:9C:CA   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=16/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 
*********************************************************

iwlist chan;

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ iwlist chan
eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 
*********************************************************

sudo iwlist scan;

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ sudo iwlist scan
[sudo] password for paul: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:8A:AE:98:9C:CA
                    ESSID:"BTHub5-FWTJ"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8E0050F204104A000110104400010210570001001041000100103B000103104700102647C404F5C05BB0A98DC1F155C50CCA10210002425410230005487562203510240009425420487562203541104200122B3036383534332B4E5134303430323036391054000800060050F204000110110010425420486F6D652048756220352E3041100800020084103C000101
                    Quality=0/100  Signal level=2/100  

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 
*********************************************************
```


I certainly hope this means more to you than it does to me! I've had very little to do with command line stuff over the last 30-odd years...

Mike Walsh.

---

### Post by praseodym on 2014-06-09
> ```
IE: IEEE 802.11i/[COLOR="#FF0000"]WPA2[/COLOR] Version 1
Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
Pairwise Ciphers (2) : [COLOR="#FF0000"]CCMP[/COLOR] [COLOR="#FF0000"]TKIP[/COLOR]
Authentication Suites (1) : PSK
```

This looks weird: WPA2 encryption with TKIP?! Enter your router interface (manual!) and change it to pure WPA2-AES (CCMP), and a fixed channel. The driver rtl8188eu is shown. Maybe you wish to try updating the driver via:

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```
Reboot. This package named "ce" (another driver) also contains the "ee".

---

### Post by Mike_Walsh on 2014-06-09
Well, now...

From investigating my router's access interface, it appears that British Telecom have set things up so that you can ONLY switch between WPA & WPA2; you cannot switch from TKIP to AES or back again, because it appears those options are preset (and I've investigated EVERY menu level that can be accessed by the user)! So, I can't do anything about that...

Actually, we may be at cross purposes here. I wasn't asking for help with connection problems (I don't have problems at the moment); I just wondered why the indicator LED on the adapter was behaving differently under Ubuntu, compared to the way it behaved under Windows XP.

Mike.

---

### Post by wildmanne39 on 2014-06-09
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---


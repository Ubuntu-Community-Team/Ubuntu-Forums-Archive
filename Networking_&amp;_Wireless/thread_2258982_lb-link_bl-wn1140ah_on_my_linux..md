---
title: "lb-link bl-wn1140ah on my linux."
date: 2015-01-01
forum: Networking &amp; Wireless
---

### Post by Bryan_Colina on 2015-01-01
Hi happy new year. I'm a newbie with Linux. i installed Ubuntu 14.10 64 bit. and bought lb-link bl-wn1140ah. I followed every instruction I could find in the forums but I couldn't make it work. I always get this message when I input the command make

```
[sudo] password for mabe: 
make -C tools
make[1]: Entering directory '/home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools'
/home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.16.0-29-generic/build SUBDIRS=/home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-29-generic'
  CC [M]  /home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o
/home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c: In function &#8216;RTMPIoctlShow&#8217;:
/home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c:4941:85: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
             snprintf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                     ^
/home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c:4941:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
             snprintf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                               ^
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o' failed
make[2]: *** [/home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1345: recipe for target '_module_/home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux' failed
make[1]: *** [_module_/home/mabe/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-29-generic'
Makefile:356: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
```

Can anyone help me? Please move my post to the right section if its in a wrong one. Thank you have a good day!

---

### Post by Bryan_Colina on 2015-01-01
By the way I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=2215102](http://ubuntuforums.org/showthread.php?t=2215102)
[http://ubuntuforums.org/showthread.php?t=1826584](http://ubuntuforums.org/showthread.php?t=1826584) 

I cant understand what is in here: [http://ubuntuforums.org/showthread.php?t=1208438](http://ubuntuforums.org/showthread.php?t=1208438)

---

### Post by Bryan_Colina on 2015-01-01
Does anyone have the modified files for driver because I'm to new to follow the instrutions in the readme text file. Please, I badly need your help.

---

### Post by praseodym on 2015-01-01
Please show the outputs of
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Bryan_Colina on 2015-01-01
hi wasnt able to do your suggestions because when i came back to this post i installed a new ubuntu 14.04 32 bit. that one i had was 14.10 64 bit. now i was able to make my lb-link bl-wn1140ah work unfortunately i guess im messed up i guess.

```
breia@mabe:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39205  1 
ctr                    12905  0 
ccm                    17496  0 
bnep                   18895  2 
rfcomm                 53664  8 
arc4                   12536  2 
rt5370sta             726655  1 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
hid_generic            12492  0 
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
usbhid                 47070  0 
hid                    87604  2 hid_generic,usbhid
snd_hda_codec_realtek    59259  1 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
coretemp               13195  0 
kvm_intel             132651  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 51828  0 
snd_rawmidi            25135  1 snd_seq_midi
kvm                   388310  1 kvm_intel
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60939  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ath5k                 134977  0 
joydev                 17101  0 
ath                    23922  1 ath5k
serio_raw              13230  0 
soundcore              12600  1 snd
mac80211              546067  1 ath5k
yenta_socket           40201  0 
pcmcia_rsrc            18319  1 yenta_socket
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
btusb                  27580  0 
bluetooth             342208  22 bnep,btusb,rfcomm
radeon               1420704  3 
cfg80211              409394  3 ath,ath5k,mac80211
ttm                    72725  1 radeon
drm_kms_helper         48868  1 radeon
drm                   244037  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
video                  18903  0 
sis_agp                13091  0 
parport_pc             31981  0 
mac_hid                13037  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
mmc_block              31138  2 
psmouse                91357  0 
sdhci_pci              18535  0 
firewire_ohci          35529  0 
r8169                  61562  0 
firewire_core          61867  1 firewire_ohci
sdhci                  37779  1 sdhci_pci
sata_sis               12711  2 
crc_itu_t              12627  1 firewire_core
mii                    13654  1 r8169


i can't see my ralink here but its working

breia@mabe:~$ lsmod | grep rt
rt5370sta             726655  1 
parport_pc             31981  0 
parport                40836  3 lp,ppdev,parport_pc
breia@mabe:~$ lspci -nnk |grep -iA2 net
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: AzureWave AW-GE780 802.11bg Wireless Mini PCIe Card [1a3b:1026]
    Kernel driver in use: ath5k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:63f1]
    Kernel driver in use: r8169

here i have a different rt not rt 3070 but 5370

breia@mabe:~$ lsusb
Bus 001 Device 005: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 003: ID 1a2c:0023 China Resource Semico Co., Ltd 
Bus 002 Device 005: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

breia@mabe:~$ iwconfig
wlan0     Ralink STA  ESSID:"yeah"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.427 GHz  Access Point: CC:A2:23:86:DA:37   
          Bit Rate=65 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=50/100  Signal level:-66 dBm  Noise level:-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

rename4   IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


breia@mabe:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```


i think it seems working but the only thing wrong is when i use airmon-ng start wlan0, there is no monitor mode and i get disconnected. please help again

---

### Post by slickymaster on 2015-01-01
> **Bryan_Colina said:**
> <---snip--->
i think it seems working but the only thing wrong is when i use [COLOR=#ff0000]**airmon-ng**[/COLOR] start wlan0, there is no monitor mode and i get disconnected. please help again

@Bryan_Colina:
From the [Forum Rules]("http://ubuntuforums.org/misc.php?do=showrules"):
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

airmong-ng isn't supported here, so don't expect this thread to remain open if you'll go on pursuing help regarding it.

---

### Post by praseodym on 2015-01-01
This stick should run with the native driver while deactivating the hardware encryption:
```

sudo modprobe -rfv rt5370sta
sudo modprobe -v rt2800usb nohwcrypt=1
```
If it works make it permanent:
```

echo "options rt2800usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800usb.conf
```
You can uninstall the other one if it works.

What about the internal card?
```

echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by Bryan_Colina on 2015-01-01
> **slickymaster said:**
> @Bryan_Colina:
From the [Forum Rules]("http://ubuntuforums.org/misc.php?do=showrules"):


airmong-ng isn't supported here, so don't expect this thread to remain open if you'll go on pursuing help regarding it.


pardon me. and thank you for the reminder

---

### Post by Bryan_Colina on 2015-01-01
```
breia@mabe:~$ echo "options rt2800usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800usb.conf
options rt2800usb nohwcrypt=1
breia@mabe:~$ echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
options ath5k nohwcrypt=1
```
```
breia@mabe:~$ sudo modprobe -rfv ath5k
rmmod ath5k
rmmod ath
breia@mabe:~$ sudo modprobe -v ath5k
insmod /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1
```

---

### Post by slickymaster on 2015-01-01
> **Bryan_Colina said:**
> pardon me. and thank you for the reminder

No problem, as long as the forum rules are kept. ;)
Good luck.

---

### Post by Bryan_Colina on 2015-01-03
Interface    Chipset        Driver

wlan0        Ralink 2560 PCI    rt2500 (monitor mode enabled)
wlan1        Atheros     ath5k - [phy0]

breia@mabe:~$ lsusb
Bus 001 Device 005: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 003: ID 1a2c:0023 China Resource Semico Co., Ltd 
Bus 002 Device 006: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


different chipset pls help

---

### Post by Bryan_Colina on 2015-01-03
this is very funny i have been trying to work things out with my usb wifi adapter but some things come out of nowhere. happy new year. lol

breia@mabe:~$ lsmod |grep rt
rt5370sta             726655  1 
parport_pc             31981  0 
parport                40836  3 lp,ppdev,parport_pc

---

### Post by Bryan_Colina on 2015-01-03
```
breia@mabe:~$ iwconfig
wlan0     Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=49/100  Signal level:-69 dBm  Noise level:-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"yeah"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: CC:A2:23:86:DA:37   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=23/70  Signal level=-87 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:6   Missed beacon:0
```

---


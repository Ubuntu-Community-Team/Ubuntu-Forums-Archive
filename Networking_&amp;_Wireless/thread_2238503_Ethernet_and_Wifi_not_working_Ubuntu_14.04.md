---
title: "Ethernet and Wifi not working Ubuntu 14.04"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by Francesco_ on 2014-08-08
I have recently downloaded ubuntu14.04 for my acer laptop (it's some 8 years old) and it works well but the only problem is I can't connect to internet in any way... When i click on the network icon on the top right it says  "No network devices found" in the options and i've looked for many ways to try and fix this problem but none of them seem to work. Another strange thing is that i was connected to a wired connection during the ubuntu installation and it worked just fine but when the computer restarted an icon appeared saying "Disconnected-you are now offline" at the login and since that I can't even connect to ethernet :( can anyone help?

---

### Post by Hadaka on 2014-08-08
Hi plesse post the output of..
```
lspci -n | egrep '0200|0280' | awk '{print$3}'
```

the   |  pipe symbol is on the right side of my us keyboard along with the \ symbol

thank you.

---

### Post by Francesco_ on 2014-08-08
Hi thanks for the reply i  have written that code in terminal and the result was 
```
14e4:4311
14e4:170c
```

---

### Post by Hadaka on 2014-08-08
Hi, those numbers tell me you have broadcom cards, please do,
from a wired connection (i know it doesnt work,,it will after the next 3 commands)
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf #its ok if this command does nothing or fails
sudo modprobe b44
```
boot, your wired connection should now be working
then do..still from a wired connection
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
boot
your wireless should now be working.
remove ethernet cable ,,,test

*if this worked like it should have then
mark SOLVED
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Francesco_ on 2014-08-09
Thanks! My ethernet now works perfectly! I still can't see any wifi option in my network icon though... I went through the second procedure three times but when i switch it on again it doesn't seem to work. What should i do?

---

### Post by Hadaka on 2014-08-09
Hi , please make sure you are connected to the internet with the 
cable when you load the wireless commands
with ethernet cable and connected to the internet please do
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
plese post the output of..
```
lspci -nnk | grep -iA2 net
lsmod
rfkill list all
```
thanks

---

### Post by Francesco_ on 2014-08-09
ok should i boot between the two codes?

---

### Post by Hadaka on 2014-08-09
it doesnt really matter but,,,sure,why not?

---

### Post by Francesco_ on 2014-08-09
To save time i didn't boot and the output was ```
 0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no 
```

---

### Post by Francesco_ on 2014-08-09
p.s. this was the final output do you also need the outputs of the other commands as well?

---

### Post by Francesco_ on 2014-08-09
anyway here is the complete ```
 francesco@francesco-Extensa-5200:~$ lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Kernel driver in use: b43-pci-bridge
06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Kernel driver in use: b44
francesco@francesco-Extensa-5200:~$ lsmod
Module                  Size  Used by
arc4                   12536  2 
b43                   356470  0 
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342206  10 bnep,rfcomm
snd_hda_codec_realtek    55125  1 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
acer_wmi               31735  0 
snd_seq_midi           13132  0 
pcmcia                 51828  0 
sparse_keymap          13708  1 acer_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
i915                  705659  3 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
yenta_socket           40201  0 
coretemp               13195  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
pcmcia_rsrc            18319  1 yenta_socket
snd_timer              28584  2 snd_pcm,snd_seq
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
drm_kms_helper         47182  1 i915
lpc_ich                16864  0 
joydev                 17101  0 
drm                   244037  4 i915,drm_kms_helper
ssb_hcd                12749  0 
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13230  0 
i2c_algo_bit           13197  1 i915
wmi                    18673  1 acer_wmi
soundcore              12600  1 snd
mac_hid                13037  0 
video                  18903  2 i915,acer_wmi
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
b44                    31275  0 
sdhci_pci              18535  0 
psmouse                91329  0 
sdhci                  37779  1 sdhci_pci
ssb                    51854  3 b43,b44,ssb_hcd
mii                    13654  1 b44
francesco@francesco-Extensa-5200:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by Hadaka on 2014-08-09
hi , please post the output of,and yes,,,post all of them
```
nm-tool
dmesg | grep b43 
iwlist wlan0 scan
```
thanks.

---

### Post by Francesco_ on 2014-08-09
Hi sorry i didn't answer imediatly... the output was ```
 francesco@francesco-Extensa-5200:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:19:7E:57:8E:D1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Vodafone-25015127: Infra, 00:24:89:A7:93:CC, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2
    Vodafone-26721728: Infra, 00:24:89:CB:BD:34, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA2
    NETGEAR70:       Infra, E0:46:9A:8C:DC:5E, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    SpeedTouch8350DB:Infra, 00:90:D0:F8:B1:08, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    MawFI:           Infra, 9C:D3:6D:0F:DB:0F, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    natospettinato:  Infra, 00:1F:33:87:7E:B8, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    Cartoonia:       Infra, 00:02:CF:BE:F0:00, Freq 2472 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2


- Device: eth0  [Ethernet connection 1] ----------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:16:D4:D8:E3:27

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


francesco@francesco-Extensa-5200:~$ dmesg | grep b43
[  173.563349] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  173.604060] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[  174.836114] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 1321.184145] Modules linked in: arc4 b43 bcma mac80211 cfg80211 rfcomm bnep bluetooth snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc acer_wmi snd_seq_midi pcmcia sparse_keymap snd_seq_midi_event snd_rawmidi i915 snd_seq yenta_socket coretemp snd_seq_device pcmcia_rsrc snd_timer pcmcia_core drm_kms_helper lpc_ich joydev drm ssb_hcd snd serio_raw i2c_algo_bit wmi soundcore mac_hid video parport_pc ppdev lp parport b44 sdhci_pci psmouse sdhci ssb mii
[ 1323.396060] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 1561.192060] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
francesco@francesco-Extensa-5200:~$ iwlist wlan0 scan
wlan0     No scan results

```

---

### Post by praseodym on 2014-08-09
Please check this order of module loading:
```

sudo modprobe -rfv b43 b44
```
Then load them again:
```

sudo modprobe -v ssb
sudo modprobe -v bcma
sudo modprobe -v b43
sudo modprobe -v b44
```

---

### Post by Hadaka on 2014-08-09
hi, please COPY and paste these commands,
```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit 0
```
boot
now does it work??

---

### Post by Francesco_ on 2014-08-09
IT'S WORKING!! I entered the codes praseodym posted and it turned on the wifi! A big thanks to both of you for your help and time there shouldn't be any more problems :)

---

### Post by praseodym on 2014-08-09
If it is occurring again after a reboot, make it permanent and automatic via:
```

echo -e "blacklist b43\nblacklist b44\nblacklist ssb\nblacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf 
sudo sed -i "s/exit 0/# starting order for the broadcom drivers/g" /etc/rc.local
echo -e "modprobe ssb\nmodprobe bcma\nmodprobe b43\nmodprobe b44\nexit 0" | sudo tee -a /etc/rc.local
```

---

### Post by Hadaka on 2014-08-09
GREAT ! Glad it is working.
please mark this thread SOLVED
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


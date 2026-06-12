---
title: "Toshiba nb500-10f wireless card problem"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Barcarich on 2011-02-15
Hi All,

i bought a new netbook for work and im fed up with the general poorness of windows, so on advice i downloaded and installed Ubuntu 10.10 which already looks great. The only problem is that i cant seem to find a wireless driver for it. Even when i look on the toshiba website it tells me to choose the card by searching in windows 7 for the model, which no longer exists. I cant find which model it is, and the wireless card does not show up. Any help would be greatly appreciated.

Rich

---

### Post by scouser27 on 2011-02-15
Can you post some details about your netbook.

For instance, what's the model.

Ubuntu should be able to see the wireless card using something like ```
dmesg | grep Wireless
```

---

### Post by Barcarich on 2011-02-15
FINALLY, thanks guys but i got a fix,

[http://ubuntuforums.org/showthread.php?t=1608908](http://ubuntuforums.org/showthread.php?t=1608908)

---

### Post by Risenn on 2011-04-14
hey, Well I have this problem Its a Toshiba Nb500/00D netbook. just purchased today. First time Linux user aswell. I can't figure out the wireless. The adapter is Integrated Atheros 802.11 a/g/n. I have no idea about linux so any and all information would help. Thank you.

---

### Post by pigle on 2011-04-28
This worked for me
[http://forum.ubuntu-fr.org/viewtopic.php?id=448140](http://forum.ubuntu-fr.org/viewtopic.php?id=448140)

---

### Post by kuric on 2011-09-10
I get intermittent connection with realtek drivers on a Toshiba NB-500, using Ubuntu 11.04 and WPA2 wireless encryptation.
Sometimes it drops/freezes for a few seconds and gets unable to resolve host.
Anyone?

---

### Post by wildmanne39 on 2011-09-10
Hi, please post the results of these commands here:
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn | grep 0280
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by kuric on 2011-09-13
God, I'm sorry for the delay, I couldn't find this webpage anymore... Here it goes, after a fresh install of Xubuntu:

```
sudo lshw -C network

  *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 88:25:2c:bc:3a:a7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: 1c:75:08:76:9b:60
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff

nm-tool

NetworkManager Tool

State: connected

- Device: wlan0  [Auto kubric] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        88:25:2C:BC:3A:A7

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *kubric:         Infra, 48:5B:39:E6:A6:C1, Freq 2422 MHz, Rate 54 Mb/s, Strength 100 WPA2
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:CB:BA:89, Freq 2467 MHz, Rate 54 Mb/s, Strength 100
    ZON-BA80:        Infra, 00:05:CA:CB:BA:88, Freq 2467 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    kubric:          Infra, 00:05:CA:AE:7E:18, Freq 2422 MHz, Rate 54 Mb/s, Strength 100 WPA2
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:A7:76:29, Freq 2417 MHz, Rate 54 Mb/s, Strength 100
    Melita:          Infra, 00:13:F7:79:D4:68, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    MEO-A5A78A:      Infra, 00:26:44:A5:A7:8A, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Thomson962378:   Infra, 00:26:44:96:23:78, Freq 2472 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:7A:18:09, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    Thomson04D224:   Infra, 08:76:FF:04:D2:24, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:AE:7E:19, Freq 2422 MHz, Rate 54 Mb/s, Strength 100
    Thomson72EDF4:   Infra, 00:26:44:72:ED:F4, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Thomson0C1490:   Infra, 08:76:FF:0C:14:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        1C:75:08:76:9B:60

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

lspci -nn | grep 0280

07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 192f:0616 Avago Technologies, Pte. 
Bus 002 Device 002: ID 046e:550f Behavior Tech. Computer Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"kubric"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 48:5B:39:E6:A6:C1   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

rfkill list all

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

lsmod

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  3 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
joydev                 17322  0 
rtl8192ce             120897  0 
i915                  450944  2 
snd_seq_midi           13132  0 
rtlwifi                78961  1 rtl8192ce
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              257001  2 rtl8192ce,rtlwifi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 rtlwifi,mac80211
drm                   180037  3 i915,drm_kms_helper
snd                    55295  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
sparse_keymap          13666  0 
video                  18951  1 i915
coretemp               13283  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  1 
libahci                25548  1 ahci
r8169                  42534  0 

```

---

### Post by wildmanne39 on 2011-09-13
Hi, make sure your router is set to b,g,n mode and not just n mode see if that helps.

I am currently in the hospital, they have wifi but I will not be on much until I am feeling better.
Thank you

---

### Post by kuric on 2011-09-14
Oh... I'm touched by the fact you're trying to help me dispite you're not feeling well. 
But you know, that suggestion didn't make a difference and there's no use. I'm getting really poor performance with Ubuntu and others distros I've tryed in this particular netbook, like irregular internet connection, overheating, low battery life and even irresponsive power button (!), so I'm quitting linux for now and wait for better days. Perhaps I'll try the new Ubuntu release in a few weeks, if I have the time and patience... until them, I must say Windows 7 Starter takes care of the job and gives me no problems. 
So, please concentrate yourself on being healthy! Nice people like you deserve good health. Best regards.

---

### Post by wildmanne39 on 2011-09-15
Hi, I am sorry to hear you have went back to windows but when you are ready the community will be here to help.
Thank you

---

### Post by zsxd45 on 2011-09-15
Hi all PLEASE help me i have Ubuntu Linux 11.04 - and windows 7 but the sumvision svw322p (wifi card) Is not being detected! - This is a custom computer with:

PS. WIFI WORKS FINE IN WIN 7

Amd Phenom II x4 3.2 ghz

8gb ddr3 ram

ATI Radeon HD 5570 2gb

All works except the wifi - Please Help!

---

### Post by wildmanne39 on 2011-09-15
Hi, welcome to the forum! Please open a terminal by hitting ctrl+alt+t and run these commands, just copy and paste them into the terminal, then post the results here

```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network 
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by tx99h4 on 2012-03-14
Hello everybody!

I've found the solution to deal with that problem!
I have a Toshiba NB500 with Ubuntu Lucid (10.04 lts, kernel 2.6.32-33 generic)....

1) Download these packages from computer which has internet connection:

> dkms_2.1.1.2-2fakesync1_all.deb
rtl8192ce-dkms_2.6.0003.0628.2010ubuntu1_all.deb

links:
[http://packages.ubuntu.com/lucid/all/dkms/download](http://packages.ubuntu.com/lucid/all/dkms/download)
[https://launchpad.net/~lexical/+archive/hwe-wireless/+files/rtl8192ce-dkms_2.6.0003.0628.2010ubuntu1_all.deb](https://launchpad.net/~lexical/+archive/hwe-wireless/+files/rtl8192ce-dkms_2.6.0003.0628.2010ubuntu1_all.deb)


2) Copy them to your netbook personal folder.

3) open terminal and type:
```
sudo dpkg -i dkms_2.1.1.2-2fakesync1_all.deb
sudo dpkg -i rtl8192ce-dkms_2.6.0003.0628.2010ubuntu1_all.deb
```

4) reboot!

Now wireless is on \\:D/



P.S. when you upgrade the system and lost your wireless connection, do the same steps above and it will be okay :D

---

### Post by galois1 on 2013-01-04
I have this toshiba nb500 and, with some routers (with xavi amper), the netbook sometimes conect to the wifi, and sometimes not. However, with other routers it connect always. I use Ubuntu 12.04. Any suggestions?

---


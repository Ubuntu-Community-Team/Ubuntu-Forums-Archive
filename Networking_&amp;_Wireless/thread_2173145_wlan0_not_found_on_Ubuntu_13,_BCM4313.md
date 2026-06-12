---
title: "wlan0 not found on Ubuntu 13, BCM4313"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by HrJ7k64 on 2013-09-08
Hi I've just installed ubuntu 13 on my lenovo b570e and the wireless isn't working at all and wlan0 won't come up. I've tried various online tips but nothing works.

If i run: lspci -nn | grep 0280

I get the following
> 02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

Also: iwconfig
> 
eth0      no wireless extensions.

lo        no wireless extensions.


Any tips on how I can get this working? It's very annoying. thanks

---

### Post by HrJ7k64 on 2013-09-08
Anyone?

---

### Post by praseodym on 2013-09-08
Install the package "linux-firmware-nonfree" via cable connection

---

### Post by HrJ7k64 on 2013-09-08
The problem was other drivers being installed. Now i just have brcmsmac installed, however when i click connect to wifi and enter the password it never connects, just keeps prompting me to input the password again (i did it correctly)

Any ideas?

result of: lsmod | grep brc> 
brcmsmac              550698  0 
bcma                   41051  1 brcmsmac
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
mac80211              606457  2 brcmsmac,ath9k_htc
cfg80211              510937  5 wl,ath,brcmsmac,mac80211,ath9k_htc


also my modprobe blacklist has the following added:
blacklist b43
blacklist b43legacy
blacklist bcma
blacklist ndiswrapper

---

### Post by wildmanne39 on 2013-09-08
Please do:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist ath" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist ath9k_htc " | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot
Thanks

---

### Post by HrJ7k64 on 2013-09-08
Did those steps, but it's just as before still

---

### Post by wildmanne39 on 2013-09-08
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by HrJ7k64 on 2013-09-08
Here's the result [http://pastebin.com/vX1MeHFs](http://pastebin.com/vX1MeHFs)

---

### Post by wildmanne39 on 2013-09-08
There is a bug in the driver you are using, you can try the wl driver sometimes it works sometimes it does not.
Please do:
```
sudo modprobe -r brcmsmac
sudo modprobe wl
```
Also it looks like you may have an usb adaptor hooked up if so you will need to disconnect it before you can connect wifi.
These commands are just temparary so do not reboot.
Thanks

---

### Post by HrJ7k64 on 2013-09-08
The 2nd line there gives and error

> libkmod: ERROR ../libkmod/libkmod-module.c:791 kmod_module_insert_module: could not find module by name='wl'
ERROR: could not insert 'wl': Function not implemented
libkmod: ERROR ../libkmod/libkmod-module.c:925 command_do: Error running install command for wl
ERROR: could not insert 'wl': Operation not permitted



---

### Post by wildmanne39 on 2013-09-08
Please do:
```
sudo apt-get install bcmwl-kernel-source
```
Then run the commands from the previous post.
Thanks

---

### Post by HrJ7k64 on 2013-09-08
That fixed the wl error. But it's still behaving the same :( I click connect and 2 seconds later it prompt for password again.

---

### Post by wildmanne39 on 2013-09-08
Copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by HrJ7k64 on 2013-09-08
> [B]cat /etc/lsb-release; uname -a
[/B]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"
Linux richard-lenovo 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




**iwconfig**
usb0      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.



**rfkill list all**

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**lsmod**


Module                  Size  Used by
lib80211_crypt_tkip    17379  0 
wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              510937  1 wl
rndis_host             13855  0 
cdc_ether              13453  1 rndis_host
usbnet                 31879  2 rndis_host,cdc_ether
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228667  10 bnep,rfcomm
nls_iso8859_1          12713  1 
ext2                   72837  1 
arc4                   12615  0 
joydev                 17377  0 
coretemp               13355  0 
kvm                   443165  0 
acer_wmi               32467  0 
snd_hda_codec_hdmi     36906  1 
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  3 
snd_hda_codec         136498  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
rts5139               352481  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               80847  0 
snd_rawmidi            30180  1 snd_seq_midi
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
videodev              129260  2 uvcvideo,videobuf2_core
ideapad_laptop         18394  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mac_hid                13205  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd                     68876  16  snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                17061  0 
microcode              22881  0 
mei                    41158  0 
psmouse                95905  0 
serio_raw              13215  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
xts                    12885  1 
gf128mul               14951  1 xts
dm_crypt               22820  1 
wmi                    19070  1 acer_wmi
i915                  600349  3 
video                  19390  2 i915,acer_wmi
i2c_algo_bit           13413  1 i915
drm_kms_helper         49394  1 i915
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
r8169                  67466  0 
drm                   286028  4 i915,drm_kms_helper
ahci                   25731  3 
libahci                31364  1 ahci


Hopefully that's readable
edit:

FYI after running "
sudo apt-get install bcmwl-kernel-source" i think the wireless device changed from wlan0 to eth1

---

### Post by wildmanne39 on 2013-09-08
Are you tethering to the internet?

---

### Post by HrJ7k64 on 2013-09-08
I'm usb tethering to my phone so i can read the forum yes, but unplugging it for the commands when i enter them. Also tested connecting to wifi with the usb unplugged.

---

### Post by wildmanne39 on 2013-09-08
The modules for the tethering device are still loaded that is why I asked.

I have to leave for a couple of hours maybe someone else will pop in and help will I am gone.

---

### Post by praseodym on 2013-09-08
**bcma** must not be blacklisted, its for the bus of the device!

---

### Post by HrJ7k64 on 2013-09-08
> **praseodym said:**
> **bcma** must not be blacklisted, its for the bus of the device!

Removed it, rebooted, still no luck.

here's my entire blacklist.conf
[http://pastebin.com/aaZuq1BU](http://pastebin.com/aaZuq1BU)

---

### Post by HrJ7k64 on 2013-09-08
Why is it that on my previous linux mint installation wireless worked out of the box and ubuntu fails to do so?

---

### Post by wildmanne39 on 2013-09-08
Here is a link that may help with that driver by installing an earlier version of it.
Link and directions courtesy of chili555.
[http://askubuntu.com/questions/337643/problem-with-ubuntu-12-04-and-ideapad-n581-broadcom/337658#337658](http://askubuntu.com/questions/337643/problem-with-ubuntu-12-04-and-ideapad-n581-broadcom/337658#337658)
If you have any questions please post back for help.
Thanks

---

### Post by HrJ7k64 on 2013-09-09
Once again same result

---

### Post by varunendra on 2013-09-09
HrJ7k64,

First of all, you should use 'Code' tags instead of 'Quote' tags for posting outputs. Please follow the "Using Code tags" link in my signature if you wish to see a How To with screenshots. You might wish to edit your post no. 14 to do that correction now (unless you like smileys among codes) ;)

About your problem -
> **HrJ7k64 said:**
> Once again same result
Did the proposed packages install without errors? I suspect they may not, since the last time I checked, those packages were not compatible with kernel 3.8.. Please show us outputs of -
```
dpkg -s bcmwl-kernel-source | grep Version
apt-cache show bcmwl-kernel-source | grep Version
```

And please run the wireless script again and post back the fresh report. Thanks ! :)

---

### Post by kPckTKC on 2013-09-10
Forgot my login so had to register again.

Here's the output of those
```

richard@richard-lenovo:~$ dpkg -s bcmwl-kernel-source | grep Version
Version: 5.100.82.112+bdcom-0ubuntu3
richard@richard-lenovo:~$ apt-cache show bcmwl-kernel-source | grep Version
Version: 6.20.155.1+bdcom-0ubuntu6
Version: 5.100.82.112+bdcom-0ubuntu3

```

And the wireless script:

```


*************** info trace ***************

***** uname -a *****

Linux richard-lenovo 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 18d1:4ee3 Google Inc. 
Bus 001 Device 003: ID 0bda:58e4 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. Card reader

***** PCMCIA Card Info *****


***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
brcmutil               14755  0 
cfg80211              510937  2 wl,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BTHomeHub2-C3Z3: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    BTHub3-GS5G:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    utility :        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    BTWiFi:          Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 92
    BTWiFi:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19
    BTWiFi-with-FON: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19
    BTWiFi-with-FON: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 52


- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.130
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-GS5G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000B4254487562332D47533547
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 7956ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0050000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-C3Z3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000F4254486F6D65487562322D43335A33
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050402030100
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050402030100
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0050000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 7956ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.1.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist b43legacy
blacklist ndiswrapper
blacklist wl
blacklist ath
blacklist ath9k_htc 

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

***** modinfo *****

filename:       /lib/modules/3.8.0-30-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6E2531203CF49EB24353067
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.8.0-30-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     91AD18A369EC5A3CB1923DE
depends:        
intree:         Y
vermagic:       3.8.0-30-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x0846:0x9030 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

***** dmesg *****

[   29.157743] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   29.157778] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   29.157805] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   29.157857] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   29.170423] bcma: bus0: Bus registered
[   29.892116] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   35.602855] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   35.602866] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   35.603451] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.603733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.530708] wlan0: authenticate with <MAC address removed>
[   53.534320] wlan0: send auth to <MAC address removed> (try 1/3)
[   53.536071] wlan0: authenticated
[   53.537785] wlan0: associate with <MAC address removed> (try 1/3)
[   53.541293] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   53.541952] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   53.541959] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   53.541962] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   53.541973] wlan0: associated
[   53.541983] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   57.973304] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   57.977043] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   57.977050] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[   57.977053] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   65.913044] wlan0: authenticate with <MAC address removed>
[   65.914553] wlan0: send auth to <MAC address removed> (try 1/3)
[   65.916452] wlan0: authenticated
[   65.920540] wlan0: associate with <MAC address removed> (try 1/3)
[   65.924098] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   65.924767] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   65.924774] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   65.924777] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   65.924787] wlan0: associated
[   70.451007] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   70.455351] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   70.455358] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[   70.455360] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2000.961508] wl: module license 'MIXED/Proprietary' taints kernel.
[ 2001.001573] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[ 2001.144162] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[ 2094.441844] ERROR @wl_dev_intvar_get : error (-1)
[ 2094.441848] ERROR @wl_cfg80211_get_tx_power : error (-1)

****************** done ******************


```

---

### Post by varunendra on 2013-09-10
> **kPckTKC said:**
> Forgot my login so had to register again.

No problem. You can take this up in [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") if you wish to get your previous account's password reset for you and/or want any reasonable change to your account.

Onto the problem. All those "brcmsmac" lines, the presence of "brcmutil" in lsmod etc. are making me uncomfortable. Did you try to manually load one of the previous drivers or did they load automatically? Is this report from a fresh start?

Please do a fresh restart, don't plug in your USB dongle > try to connect via internal wifi > let it fail, then check -
```
dmesg | egrep 'bcm|brcm|wl'
```

We are expecting to see ONLY "**wl**" related lines in the output. If you see any lines related to **bcma** or **brcmsmac**, post back the output as well as outputs of -
```
cat /etc/modules
cat /etc/rc.local
```

However, if there are no lines related to bcma or brcmsmac/brcmutil in the output of grep above, run the script again and post back the new result.

Connect the USB dongle only after running these tests and the script, not before that. Sorry for the trouble, but it seems your setup is quite messed up at the moment.

---

### Post by kPckTKC on 2013-09-10
Just upgrading to 13.10 then will try those. I do think i tried a tutorial a few days ago that involved building the driver locally, however I cannot find the link now to revert that.

---

### Post by varunendra on 2013-09-10
Good luck !

Just for your info, the inbuilt brcmsmac driver (in kernel 3.8 and later) works nicely with this particular card in almost all cases. In the rare cases where it doesn't, the wl driver "wl" (version 5.100.82.38) has been found to work better.

Apart from these two, there is a [newer version]("https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504") (probably not in the repo yet) that builds fine, and the few users who cared to report its performance, all reported it to be working fine..

Accordingly, I'd suggest you try the native brcmsmac driver first (DON't check the "Install updates" or "Third party software" checkboxes during installation), and post back if it doesn't seem to work. It is much easier to troubleshoot a problem when things are at defaults.

Hopefully, you won't need any troubleshooting though. :)

---

### Post by kPckTKC on 2013-09-10
edit: installing the above .deb did nothing, acts just as it has been :/

So with 13.10 the fail continues.

Ok here's the output from the commands 

1.

```
richard@richard-lenovo:~$ dmesg | egrep 'bcm|brcm|wl'
[   79.700195] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   79.700229] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   79.700255] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   79.700307] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   79.712884] bcma: bus0: Bus registered
[   80.194379] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   80.376683] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   97.545094] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   97.545107] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   97.545730] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   97.546165] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  183.178598] wlan0: authenticate with 00:24:17:a5:70:7b
[  183.181677] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  183.183417] wlan0: authenticated
[  183.185005] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  183.185230] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  183.185272] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  183.188984] wlan0: RX AssocResp from 00:24:17:a5:70:7b (capab=0x411 status=0 aid=1)
[  183.189630] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  183.189640] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  183.189658] wlan0: associated
[  183.189678] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  183.306478] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  184.174264] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  185.172866] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  186.171799] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  187.170624] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  188.169578] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  189.168717] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  190.175209] brcmsmac bcma0:0: phyerr 0x80, rate 0xb00
[  193.501562] wlan0: deauthenticated from 00:24:17:a5:70:7b (Reason: 15)
[  193.513728] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  193.513737] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  199.776145] wlan0: authenticate with 00:24:17:a5:70:7b
[  199.777194] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  199.784145] wlan0: authenticated
[  199.786922] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  199.787293] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  199.787831] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  199.788117] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  199.788202] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  199.788468] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  199.788494] wlan0: association with 00:24:17:a5:70:7b timed out
[  200.755032] wlan0: authenticate with 00:24:17:a5:70:7b
[  200.756144] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  200.758163] wlan0: authenticated
[  200.761771] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  200.762168] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  200.762289] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  200.762671] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  200.762767] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  200.763090] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  200.763183] wlan0: association with 00:24:17:a5:70:7b timed out
[  201.710475] wlan0: authenticate with 00:24:17:a5:70:7b
[  201.711144] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  201.713182] wlan0: authenticated
[  201.716630] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  201.716850] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  201.716890] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  201.717055] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  201.717142] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  201.717331] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  201.717411] wlan0: association with 00:24:17:a5:70:7b timed out
[  202.680837] wlan0: authenticate with 00:24:17:a5:70:7b
[  202.682004] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  202.684142] wlan0: authenticated
[  202.687635] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  202.688016] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  202.688091] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  202.688418] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  202.688489] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  202.688801] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  202.688871] wlan0: association with 00:24:17:a5:70:7b timed out
[  203.639910] wlan0: authenticate with 00:24:17:a5:70:7b
[  203.640955] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  203.643114] wlan0: authenticated
[  203.646536] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  203.646799] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  203.646873] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  203.647093] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  203.647164] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  203.647376] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  203.647447] wlan0: association with 00:24:17:a5:70:7b timed out
[  204.590658] wlan0: authenticate with 00:24:17:a5:70:7b
[  204.591922] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  204.593984] wlan0: authenticated
[  204.597571] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  204.597794] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  204.597851] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  204.598010] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  204.598041] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  204.598226] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  204.598442] wlan0: association with 00:24:17:a5:70:7b timed out
[  205.545752] wlan0: authenticate with 00:24:17:a5:70:7b
[  205.546871] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  205.548934] wlan0: authenticated
[  205.552443] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  205.552654] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  205.552758] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  205.552978] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  205.553085] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  205.553272] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  205.553368] wlan0: association with 00:24:17:a5:70:7b timed out
[  206.504562] wlan0: authenticate with 00:24:17:a5:70:7b
[  206.505830] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  206.507904] wlan0: authenticated
[  206.511367] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  206.511622] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  206.511777] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  206.512020] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  206.512087] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  206.512341] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  206.512387] wlan0: association with 00:24:17:a5:70:7b timed out
[  207.459287] wlan0: authenticate with 00:24:17:a5:70:7b
[  207.460693] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  207.462777] wlan0: authenticated
[  207.466310] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  207.466518] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  207.466594] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  207.466788] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  207.466902] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  207.467110] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  207.467216] wlan0: association with 00:24:17:a5:70:7b timed out
[  208.410517] wlan0: authenticate with 00:24:17:a5:70:7b
[  208.411733] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  208.413783] wlan0: authenticated
[  208.417267] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  208.417477] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  208.417516] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  208.417751] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  208.417793] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  208.417997] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  208.418023] wlan0: association with 00:24:17:a5:70:7b timed out
[  209.361149] wlan0: authenticate with 00:24:17:a5:70:7b
[  209.362887] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  209.364873] wlan0: authenticated
[  209.368267] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  209.372018] wlan0: RX AssocResp from 00:24:17:a5:70:7b (capab=0x411 status=0 aid=1)
[  209.372625] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  209.372634] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  209.372652] wlan0: associated
[  209.492276] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  210.145727] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  211.144442] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  212.143302] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  213.142257] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  214.141142] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  215.140016] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  216.138923] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  217.137843] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  218.136794] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  219.136023] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  219.362477] wlan0: disassociating from 00:24:17:a5:70:7b by local choice (reason=3)
[  219.363693] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  219.363709] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  219.364881] wlan0: deauthenticating from 00:24:17:a5:70:7b by local choice (reason=3)
[  221.196498] wlan0: authenticate with 00:24:17:a5:70:7b
[  221.197603] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  221.199717] wlan0: authenticated
[  221.203305] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  221.203566] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  221.203603] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  221.203766] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  221.203798] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  221.203958] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  221.203991] wlan0: association with 00:24:17:a5:70:7b timed out
[  222.151387] wlan0: authenticate with 00:24:17:a5:70:7b
[  222.153107] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  222.154914] wlan0: authenticated
[  222.158297] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  222.158586] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  222.158635] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  222.158860] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  222.158902] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  222.159139] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  222.159179] wlan0: association with 00:24:17:a5:70:7b timed out
[  223.114290] wlan0: authenticate with 00:24:17:a5:70:7b
[  223.116087] wlan0: send auth to 00:24:17:a5:70:7b (try 1/3)
[  223.117833] wlan0: authenticated
[  223.121208] wlan0: associate with 00:24:17:a5:70:7b (try 1/3)
[  223.121415] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  223.121459] wlan0: associate with 00:24:17:a5:70:7b (try 2/3)
[  223.121627] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  223.121659] wlan0: associate with 00:24:17:a5:70:7b (try 3/3)
[  223.121824] brcmsmac bcma0:0: phyerr 0x4, rate 0xa
[  223.121855] wlan0: association with 00:24:17:a5:70:7b timed out


```

2 & 3.

```

richard@richard-lenovo:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
brcmsmac


```

```
richard@richard-lenovo:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


```

---

### Post by chili555 on 2013-09-10
Everyone in the forum has posted here so I hope I am not stepping on toes! Please do:```
gksudo gedit /etc/modules
```Remove *brcmsmac*. Proofread, save and close gedit. Reboot and let us see:```
lsmod
```Is there any improvement?

I would *NOT* try a newer version of brcmwl-kernel-source until we troubleshoot further.

---

### Post by kPckTKC on 2013-09-10
ok i've decided to reformat, this isnt work the pain. (also the above did nothing different)

---

### Post by varunendra on 2013-09-10
> **chili555 said:**
> I would *NOT* try a newer version of brcmwl-kernel-source until we troubleshoot further.
Precisely what he said.

> Everyone in the forum has posted here...
.. Three cheers to that !! :D


@kPckTKC,

You seem to have tried many different things and nothing worked. So I'd suggest to stop trying things on your own and try only what is suggested here - one step at a time. This card shouldn't be that difficult to troubleshoot, unless the problem is external.

---

### Post by wildmanne39 on 2013-09-10
While you are reformatting I would install 12.04 or 13.04 but not 13.10 it is still under development.

---


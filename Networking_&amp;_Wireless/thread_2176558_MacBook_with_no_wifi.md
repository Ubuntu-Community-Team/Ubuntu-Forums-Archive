---
title: "MacBook with no wifi"
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by Samuel_Kneppel on 2013-09-24
Hi all,

I've been searching this forum for the past couple hours for a solution to my problem, but all of the solutions I found did not work for me. I've tried installing multiple things via the Terminal but nothing would get my wifi to work. I have a Mid-2012 Macbook Pro 9,2 triple booted with ubuntu, windows 8 (which i am using now), and mac os x. any help would be appreciated.

Thanks in advance

---

### Post by varunendra on 2013-09-25
Welcome to the forums Samuel !

Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
nm-tool
```

---

### Post by Samuel_Kneppel on 2013-09-25
ok here it is:

```

samuel@samuel-MacBookPro:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3
01:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
    Subsystem: Broadcom Corporation Device [14e4:0000]
    Kernel driver in use: sdhci-pci
02:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. Device [106b:00f5]
    Kernel driver in use: bcma-pci-bridge
samuel@samuel-MacBookPro:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 002 Device 003: ID 0424:2513 Standard Microsystems Corp. 
Bus 002 Device 009: ID 05ac:821d Apple, Inc. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 005: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 002 Device 006: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
samuel@samuel-MacBookPro:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


samuel@samuel-MacBookPro:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
samuel@samuel-MacBookPro:~$ lsmod
Module                  Size  Used by
dm_crypt               22820  1 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
nls_iso8859_1          12713  1 
btusb                  22474  0 
bluetooth             228619  22 bnep,btusb,rfcomm
bcm5974                17347  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_cirrus    23829  1 
b43                   378642  0 
mac80211              606457  1 b43
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_cirrus
snd_hwdep              13602  1 snd_hda_codec
cfg80211              510937  2 b43,mac80211
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
joydev                 17377  0 
snd_seq_midi           13324  0 
ssb                    56748  1 b43
coretemp               13355  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm_intel             132891  0 
apple_gmux             13406  0 
kvm                   443165  1 kvm_intel
snd_rawmidi            30180  1 snd_seq_midi
apple_bl               13673  1 apple_gmux
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus
applesmc               19353  0 
input_polldev          13896  1 applesmc
mei                    41158  0 
lpc_ich                17061  0 
mac_hid                13205  0 
bcma                   41051  1 b43
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
microcode              22881  0 
hid_generic            12540  0 
hid_apple              13237  0 
usbhid                 47074  0 
hid                   101002  3 hid_generic,usbhid,hid_apple
ghash_clmulni_intel    13259  0 
i915                  600351  3 
firewire_ohci          40103  0 
i2c_algo_bit           13413  1 i915
aesni_intel            55399  97 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
firewire_core          64508  1 firewire_ohci
cryptd                 20373  4 ghash_clmulni_intel,aesni_intel,ablk_helper
crc_itu_t              12707  1 firewire_core
sdhci_pci              18590  0 
tg3                   153796  0 
sdhci                  32522  1 sdhci_pci
drm_kms_helper         49394  1 i915
ptp                    18621  1 tg3
pps_core               14080  1 ptp
drm                   286313  4 i915,drm_kms_helper
ahci                   25731  3 
libahci                31364  1 ahci
video                  19390  2 i915,apple_gmux
samuel@samuel-MacBookPro:~$ nm-tool


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        10:DD:B1:E4:75:77


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

```

---

### Post by varunendra on 2013-09-25
> **Samuel_Kneppel said:**
> ok here it is:

```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n **[14e4:4331]** (rev 02)
    Subsystem: Apple Inc. Device [106b:00f5]
    Kernel driver in use: **bcma-pci-bridge**

```
If you can connect to internet via cable, please do -
```
sudo apt-get install linux-firmware-nonfree
```

If you can't connect to internet anyhow, then download the above package from here : [http://packages.ubuntu.com/raring/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/raring/all/linux-firmware-nonfree/download)
Copy it to your Ubuntu Desktop and double-click to install.

Once it is installed, please do -
```
sudo modprobe -rv b43
sudo modprobe -v b43
```
..or just reboot. Does the wireless work now?

---

### Post by Samuel_Kneppel on 2013-09-25
I double clicked it but the install button isn't able to be pressed. Can I install it via terminal?

---

### Post by Samuel_Kneppel on 2013-09-25
Never mind. I figured it out. So I installed it, and now if I click on the network thing at the top right corner of the screen I can see now see that wifi networks is there but it's disconnected. And there aren't any wifi connections to connect too. I restarted it as and executed the code as well

---

### Post by Hadaka on 2013-09-25
Hi, If you are able to connect with the ethernet cable
then please do via terminal..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
*The first command is incase there is anything left
from that driver.
thanks.

---

### Post by Samuel_Kneppel on 2013-09-25
I don't have access to Ethernet right now. Is there any way to download it on a brower then copy that over?

---

### Post by Hadaka on 2013-09-25
Hi, I see yu were able to load the file varun sent..
*if you loaded brcm-kernel-source while attempting
to get it going, that one loads blacklist files, so it
needs to be removed, ,you dont need internet connection
to remove it. so please do the first command in the last
post.
thanks.

---

### Post by praseodym on 2013-09-25
Download this file and save it in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Installation via
```

sudo dpkg -i ~/Downloads/*.deb
sudo modprobe -rfv b43
sudo modprobe -v b43
```
Check:
```

lsmod
iwconfig
rfkill list
dmesg | grep b43
cat /etc/resolv.conf
```

---

### Post by Samuel_Kneppel on 2013-09-25
Ok, so I first followed hadaka's instructions and got this:

 ```
samuel@samuel-MacBookPro:~$ sudo apt-get remove --purge bcmwl-kernel-source[sudo] password for samuel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
samuel@samuel-MacBookPro:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
samuel@samuel-MacBookPro:~$ sudo modprobe b43
samuel@samuel-MacBookPro:~$ 

```

... so I'm assuming that this didn't do anything since it said nothing was upgraded. Either way I still didn't have wifi so I tried praseodym's solutions and it did something... but it didn't solve my problem. My Wifi network is still "disconnected" according to the network widget/app in the top right corner. Just in case this is helpful, I included all the code for what I put into Terminal for praseodym's solution:

```
samuel@samuel-MacBookPro:~$ sudo dpkg -i ~/Downloads/*.deb[sudo] password for samuel: 
(Reading database ... 155516 files and directories currently installed.)
Preparing to replace linux-firmware-nonfree 1.14ubuntu1 (using .../linux-firmware-nonfree_1.14ubuntu1_all.deb) ...
Unpacking replacement linux-firmware-nonfree ...
Setting up linux-firmware-nonfree (1.14ubuntu1) ...
samuel@samuel-MacBookPro:~$ sudo modprobe -rfv b43
rmmod b43
rmmod ssb
rmmod mac80211
rmmod cfg80211
rmmod bcma
samuel@samuel-MacBookPro:~$ sudo modprobe -v b43
insmod /lib/modules/3.8.0-19-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.8.0-19-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-19-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-19-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/b43/b43.ko 
samuel@samuel-MacBookPro:~$ lsmod
Module                  Size  Used by
b43                   378642  0 
bcma                   41051  1 b43
mac80211              606457  1 b43
cfg80211              510937  2 b43,mac80211
ssb                    56748  1 b43
nls_utf8               12557  1 
hfsplus                88539  1 
dm_crypt               22820  1 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
nls_iso8859_1          12713  1 
arc4                   12615  2 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
btusb                  22474  0 
bluetooth             228619  22 bnep,btusb,rfcomm
uvcvideo               80847  0 
bcm5974                17347  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_cirrus    23829  1 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_cirrus
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
apple_gmux             13406  0 
joydev                 17377  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
apple_bl               13673  1 apple_gmux
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus
mei                    41158  0 
lpc_ich                17061  0 
applesmc               19353  0 
microcode              22881  0 
input_polldev          13896  1 applesmc
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
hid_generic            12540  0 
hid_apple              13237  0 
usbhid                 47074  0 
hid                   101002  3 hid_generic,usbhid,hid_apple
tg3                   153796  0 
ptp                    18621  1 tg3
ghash_clmulni_intel    13259  0 
pps_core               14080  1 ptp
firewire_ohci          40103  0 
i915                  600351  3 
aesni_intel            55399  103 
firewire_core          64508  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
aes_x86_64             17255  1 aesni_intel
ahci                   25731  3 
libahci                31364  1 ahci
video                  19390  2 i915,apple_gmux
i2c_algo_bit           13413  1 i915
usb_storage            57204  1 
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  4 ghash_clmulni_intel,aesni_intel,ablk_helper
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
sdhci_pci              18590  0 
sdhci                  32522  1 sdhci_pci
samuel@samuel-MacBookPro:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
samuel@samuel-MacBookPro:~$ dmesg | grep b43
[   18.765995] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   18.766441] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[   25.141984] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  116.613920] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[  116.614353] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[  116.779462] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
samuel@samuel-MacBookPro:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
samuel@samuel-MacBookPro:~$ 


```

Am I doing something wrong? I am fairly new to working with Linux so I don't have much experience with it.

---

### Post by Hadaka on 2013-09-25
Hi, no you are not doing anyting wrong
so far it looks great. lets take a look at a couple things.
please post the output of..
```
cat /etc/network/interfaces
sudo iwlist wlan0 scan
sudo modprobe -rf b43
sudo modprobe b43
dmesg | egrep 'b43|wlan'
```
thanks.

---

### Post by praseodym on 2013-09-25
It looks good, but you need nameservers in your /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
sudo service network-manager restart
```

---

### Post by Hadaka on 2013-09-25
indeed, looks fine for the driver, lets make sure you
have the network mgr configured correctly..
click your wifi symbol (network mgr)
click edit connections
click your essid configure IPv4  like the attached set IPv6 to Ignore
[ATTACH=CONFIG]246504[/ATTACH]

---

### Post by Samuel_Kneppel on 2013-09-25
I installed ubuntu without "features"... Could that cause this? Because I'm thinking of just reinstalling

---

### Post by Hadaka on 2013-09-25
If the wired side is working in Ubuntu you can get
the "features" via ethernet/internet connection..
```
sudo apt-get update
sudo apt get upgrade
```
If not...then yeah..reload, but you will
still have to mess with the wireless driver.

---

### Post by varunendra on 2013-09-25
> **Samuel_Kneppel said:**
> I installed ubuntu without "features"... Could that cause this? Because I'm thinking of just reinstalling

Doesn't look like a bad install problem to me. The b43 driver seems to support only **b/g** channels on this card. Can you confirm your router is in b/g mode? Try b-only and g-only modes as well. If the router is in b/g/n or a/b/g/n mode, it may be confusing the driver.

Also, try saving your access-point's SSID and security settings (preferably WPA2-PSK (AES)) in the network manager, then choose to "Connect to hidden network" in the nm drop-down list. All of these are mostly shots in the dark but if it helps, we can proceed from there.

Just so you know, the proprietary wl driver also supports this card, so we can try that one as well as yet another shot.

---

### Post by Kopkins on 2013-09-25
I'm pretty sure that macbooks need special b43 firmware for some reason. Even by using the correct firmware, I've tried all of them, I can't get mine to work. I have a thread open right now too.

You need the b43 firmware from the mactel repo.

```

sudo add-apt-repository ppa:mpodroid/mactel

sudo apt-get update 

sudo apt-get install firmware-b43-installer b43-fwcutter

```

Also, my wifi will work but i have to attempt to connect to ANY hidden network first. Even if the network does not exist.

So far I've had the same success with the packages ```

linux-firmware-nonfree 

and

firmware-b43-installer # from mactel

```

---

### Post by Samuel_Kneppel on 2013-09-27
Ok, so I basically wiped my drive clean, reformatted and repartitioned it, and put a backup of os x back onto it. Then, I installed Virtual Box and installed Ubuntu on that which works perfectly fine. Thanks for all the help though

Now, I do not know if this thread should be marked as "solved" because it was not really technically solved... lol. Just leave it as is I guess?

---

### Post by varunendra on 2013-09-27
Well, yeah, the topic under discussion never really got solved, so marking as [solved] doesn't make sense..

---


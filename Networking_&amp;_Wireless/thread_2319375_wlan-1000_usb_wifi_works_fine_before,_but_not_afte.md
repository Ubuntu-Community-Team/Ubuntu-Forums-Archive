---
title: "wlan-1000 usb wifi works fine before, but not after (!) live-cd installation."
date: 2016-04-03
forum: Networking &amp; Wireless
---

### Post by jasper6 on 2016-04-03
Dear all. I have a problem with my usb wifi adapter. Tried to solve it for a week now, but I didn&#8217;t succeed and do not know where to look now. Can someone help me out?

thanks, greetings from NL.

Setting:
 - laptop Toshiba Satellite A200-1G3
 - since the internal wifi is broken (works neither using windows) - I use an usb wifi adapter
 - usb wifi adapter = Sitecom Wireless Network USB Micro Adapter 150N X1 WLA-1000
 - WLA-1000 works fine with Windows 7
 - WLA-1000 works also fine (!) with lubuntu-15.10-desktop-i386.iso - note: the live cd, **before** the actual installation

Here comes the interesting part, once installed on the HD (or another flash drive) - the usb wifi does not work anymore: I get no specific error message, but no network is shown to select to connect. I am talking here about a completely fresh install, no config changes made. Format drive again -- fresh install -- no change: with the flash drive it works during live Lubuntu, after install/regular boot, it doesn&#8217;t anymore.

So below I paste some interesting commands that I checked while surfing all forum website I could find. Does anyone have an idea?

BEFORE = live usb - straight from website
AFTER = regular boot, directly after installation from live-cd

```

root@lubuntu:/home/lubuntu# uname -r
BEFORE: 4.2.0-16-generic
AFTER: 4.2.0-34-generic

BEFORE:
lubuntu@lubuntu:~$ iwconfig
wlx000cf6b6e851  IEEE 802.11bgn  ESSID:"Doornroosje"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: A4:2B:B0:A5:79:D8  
          Bit Rate:150 Mb/s   Sensitivity:0/0 
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=67/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

enp4s0    no wireless extensions.

wlp5s0    IEEE 802.11abg  ESSID:off/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm  
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

AFTER:   (** so somehow the usb is notified by lubuntu...)
root@lubuntu-usb1:/home/lubuntu# iwconfig
wlx000cf6b6e851  unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


(NO changes before/after)
lubuntu@lubuntu:~$ lsusb
Bus 002 Device 004: ID 0df6:005b Sitecom Europe B.V. 
Bus 002 Device 003: ID 0781:5583 SanDisk Corp. 
Bus 002 Device 002: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

(NO changes before/after)
lubuntu@lubuntu:~$ lsusb -t
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
    |__ Port 2: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 5: Dev 3, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 6: Dev 4, If 0, Class=Vendor Specific Class, Driver=r8712u, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M


(NO changes before/after)
root@lubuntu-usb1:/home/lubuntu# cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


lubuntu@lubuntu:~$ lsmod | grep w
iwl3945                65536  0
iwlegacy               90112  1 iwl3945
serio_raw              16384  0
mac80211              659456  2 iwl3945,iwlegacy
cfg80211              483328  3 iwl3945,iwlegacy,mac80211
snd_rawmidi            28672  1 snd_seq_midi
snd_hwdep              16384  1 snd_hda_codec
wmi                    20480  1 toshiba_acpi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    69632  13 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
firewire_ohci          36864  0
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core

(BEFORE)
root@lubuntu:/home/lubuntu# cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

(AFTER) the following line appears at the end of the file:
options iwlwifi bt_coex_active=0


(NO changes before/after)
root@lubuntu:/home/lubuntu# cat /var/log/syslog | grep wlan | tail -n20
Apr  3 18:51:06 lubuntu kernel: [   25.714729] iwl3945 0000:05:00.0 wlp5s0: renamed from wlan0
Apr  3 18:51:07 lubuntu kernel: [   27.315142] r8712u 2-6:1.0 wlx000cf6b6e851: renamed from wlan0


(BEFORE)
root@lubuntu:/home/lubuntu# ps aux | grep etwork
root      1248 43.7  0.6  87048 13508 ?        Ssl  18:51   7:25 /usr/sbin/NetworkManager --no-daemon
root      2943  0.0  0.3   9276  7840 ?        S    18:51   0:00 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-helper -pf /run/sendsigs.omit.d/network-manager.dhclient-wlx000cf6b6e851.pid -lf /var/lib/NetworkManager/dhclient-d35c1c7a-3091-4311-a7d3-04900b76b132-wlx000cf6b6e851.lease -cf /var/lib/NetworkManager/dhclient-wlx000cf6b6e851.conf wlx000cf6b6e851
nobody    2952  0.0  0.1   8480  3820 ?        S    18:51   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
root      3998  0.0  0.0   4544  2004 pts/1    S+   19:08   0:00 grep --color=auto etwork

(AFTER)
root@lubuntu-usb1:/home/lubuntu# ps aux | grep etwork
root       569  0.0  0.9  86900 19160 ?        Ssl  19:11   0:00 /usr/sbin/NetworkManager --no-daemon
root      1595  0.0  0.0   4548  1960 pts/0    S+   19:20   0:00 grep --color=auto etwork
** so here I miss 2 lines

```

---

### Post by chili555 on 2016-04-03
> lubuntu@lubuntu:~$ lsmod | grep wWhy grep w? What are you hoping or expecting to find with w?> lubuntu@lubuntu:~$ lsmod | grep w
[COLOR="#FF0000"]iwl3945[/COLOR] 65536 0
iwlegacy 90112 1 iwl3945
serio_raw 16384 0
mac80211 659456 2 iwl3945,iwlegacy
cfg80211 483328 3 iwl3945,iwlegacy,mac80211
snd_rawmidi 28672 1 snd_seq_midi
snd_hwdep 16384 1 snd_hda_codec
wmi 20480 1 toshiba_acpi
snd_seq_device 16384 3 snd_seq,snd_rawmidi,snd_seq_midi
snd 69632 13 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_ codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_cod ec_generic,snd_hda_codec,snd_hda_intel,snd_seq_dev ice
firewire_ohci 36864 0
firewire_core 65536 1 firewire_ohci
crc_itu_t 16384 1 firewire_coreDo you have an internal wireless device? Isn't it working as expected? Why did you get a USB wireless?

May I see:```
rfkill list all
lspci -nnk | grep 0280 -A2
```Both taken from the full install, please.

Fascinating...

---

### Post by jasper6 on 2016-04-03
Hi, thanks for the reply.

The "grep w" idea was to identify wireless lan stuff .. assuming that everything with wifi is abbreviated with a "w".

There is indeed an internal wireless device, but as per the original owner (it is a second hand) - the internal device is broken. And in fact I was not able to enable the internal device in windows neither .. like the usb-device is enabled perfectly in windows.

Here you go .. the full install details:

```

root@lubuntu-usb1:/home/lubuntu# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


root@lubuntu-usb1:/home/lubuntu# lspci -nnk | grep 0280 -A2
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1041]
    Kernel driver in use: iwl3945

```


Let me know if anything is still missing.

---

### Post by chili555 on 2016-04-03
> 0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yesThis suggests that the wireless switch or key combination is set to disable wireless; undoubtedly the source of the 'broken' condition. Is there a switch than can be manipulated?

At any rate, it is probably helpful to blacklist the internal device. In the terminal:```
sudo -i
echo "blacklist iwl3945"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r iwl3945
exit
```> The "grep w" idea was to identify wireless lan stuff .. assuming that everything with wifi is abbreviated with a "w".Most are not. In fact, the driver for your USB is curiously named r8712u. Not very "w".

After blacklisting and unloading iwl3945, is there any improvement? May we see:```
dmesg | grep -e r87 -e wlx
```

---

### Post by jasper6 on 2016-04-04
It works! Apparantly the internal device was in the way of the usb device. Many thanks chilli.. also from my wife, because now I can spend my time downstairs with her using wifi ;-)


In case there is still something interesting to be found ;)

```
root@lubuntu-usb1:~# dmesg | grep -e r87 -e wlx
[    8.514948] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[    8.516095] r8712u: register rtl8712_netdev_ops to netdev_ops
[    8.516102] usb 2-6: r8712u: USB_SPEED_HIGH with 4 endpoints
[    8.516752] usb 2-6: r8712u: Boot from EFUSE: Autoload OK
[    9.246144] usb 2-6: r8712u: CustomerID = 0x0000
[    9.246155] usb 2-6: r8712u: MAC Address from efuse = 00:0c:f6:b6:e8:51
[    9.246161] usb 2-6: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[    9.246300] usbcore: registered new interface driver r8712u
[    9.515067] r8712u 2-6:1.0 wlx000cf6b6e851: renamed from wlan0
[   10.320809] IPv6: ADDRCONF(NETDEV_UP): wlx000cf6b6e851: link is not ready
[   11.032648] r8712u 2-6:1.0 wlx000cf6b6e851: 1 RCR=0x153f00e
[   11.033638] r8712u 2-6:1.0 wlx000cf6b6e851: 2 RCR=0x553f00e
[   11.140428] IPv6: ADDRCONF(NETDEV_UP): wlx000cf6b6e851: link is not ready
[   11.448423] IPv6: ADDRCONF(NETDEV_UP): wlx000cf6b6e851: link is not ready
[   11.847941] IPv6: ADDRCONF(NETDEV_UP): wlx000cf6b6e851: link is not ready
[   21.885319] IPv6: ADDRCONF(NETDEV_UP): wlx000cf6b6e851: link is not ready
[  131.169237] IPv6: ADDRCONF(NETDEV_CHANGE): wlx000cf6b6e851: link becomes read
```

---

### Post by Bucky Ball on 2016-04-04
Good news. Please mark thread as solved (see link in my signature below) and for future reference, codes tags for terminal output please. :)

I have added to your last post as an example and instructions for use also in my signature. 

Enjoy! ;)

(PS: Marking as solved does not close the thread to further discussion.)

---

### Post by jasper6 on 2016-04-04
Many thanks! Thread is marked solved now. 

thanks for the code-tags explanation, in fact this was what I was looking for as well, I will adapt the other posts as well. Greetings from NL.

---


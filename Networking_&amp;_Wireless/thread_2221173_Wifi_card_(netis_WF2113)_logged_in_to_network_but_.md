---
title: "Wifi card (netis WF2113) logged in to network but no internet connection"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by Guy_Steward on 2014-05-01
Hey all i just installed a Wifi card (netis wf2113) into my tower (running 14.04) and it recognized my local network right away and i was able to put in my password and it appears to be connected but its not actually connected to the Internet. 

this is what im getting out of terminal 

home@MediaPC:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"myqwest8080"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 50:67:F0:F3:3A:8B   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0

Ive been using ubuntu for a couple years but my functional knowledge is still pretty basic so i could just be missing something obvious. 

thanks

---

### Post by praseodym on 2014-05-01
Please check:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
cat /etc/resolv.conf
ifconfig -a
route -n
rfkill list
```

---

### Post by Guy_Steward on 2014-05-02
[URL="http://ubuntuforums.org/misc.php?do=bbcode#code"]```
[/URL]
home@MediaPC:~$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Dell Device [1028:0282]
    Kernel driver in use: r8169
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178]
    Kernel driver in use: rtl8192ce
home@MediaPC:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0e8f:0022 GreenAsia Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 018: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
home@MediaPC:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39835  1 
ctr                    13049  1 
ccm                    17773  1 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
joydev                 17381  0 
arc4                   12608  2 
gpio_ich               13476  0 
dcdbas                 14928  0 
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
coretemp               13435  0 
snd_seq_midi           13324  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
psmouse               102222  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
serio_raw              13462  0 
rtl8192ce              53550  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
parport_pc             32701  0 
lpc_ich                21080  0 
mac80211              626489  3 rtl_pci,rtlwifi,rtl8192ce
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ppdev                  17671  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
radeon               1514165  3 
cfg80211              484040  2 mac80211,rtlwifi
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ttm                    85115  1 radeon
drm_kms_helper         52758  1 radeon
soundcore              12680  1 snd
drm                   302817  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
mac_hid                13205  0 
pata_acpi              13038  0 
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
pata_jmicron           12758  0 
r8169                  67581  0 
mii                    13934  1 r8169
ahci                   25819  3 
libahci                32168  1 ahci
home@MediaPC:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
home@MediaPC:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:9b:23:1b:e9  
          inet6 addr: fe80::221:9bff:fe23:1be9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1094747 (1.0 MB)  TX bytes:156442 (156.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:487262 (487.2 KB)  TX bytes:487262 (487.2 KB)

wlan0     Link encap:Ethernet  HWaddr 04:8d:38:1a:f4:d8  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::68d:38ff:fe1a:f4d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111611 (111.6 KB)  TX bytes:96597 (96.5 KB)

home@MediaPC:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
home@MediaPC:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[URL="http://ubuntuforums.org/misc.php?do=bbcode#code"]
```[/URL]

---

### Post by praseodym on 2014-05-02
Try to update the driver:

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot.

---

### Post by drink1297 on 2014-05-02
Looks to me like the PC IS the nameserver.  Connected to the network with a local IP, but looking for the machine itself to resolve the address.

Is your router set to give out DNS servers?

---

### Post by kengordo on 2014-05-03
i had the same problem...I adjusted the wireless mode on my router...I set the 2.4ghz band to mixed.  I guess you could use N-only if you didn't have other G-band devices using the router.  It was on G-only, and this card will not ping the gateway until it can connect at 2.4ghz N-band. 

I do have another problem with this card that the speeds are slow however, so I will start another thread if I can't find the answer in the Networking forum.

---


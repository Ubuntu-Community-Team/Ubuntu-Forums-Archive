---
title: "Slow wifi on Saucy"
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by stuart77 on 2013-12-01
Hello, I am having problems with Lubuntu 13.10 (but they started on 13.04).

I have a Broadcom 4312 LP-PHY chipset for the wifi and Lubuntu had been working fine for several months until yesterday.  Wifi was really slow to the point connections timed out.  I tried a few fixes but nothing worked so I downloaded 13.10 and did a clean install.

To get the wifi running I tried

```

sudo apt-get install bcmwl-kernel-source

```

which worked.  I then used it for five minutes then the connection problems happened again.  I rebooted then tried purging bcmwl-kernel-source and then

```

sudo apt-get install linux-firmware-nonfree

```
Still the same problems.  I also tried Linux Mint but have a hidden SSID and ran into all kinds of problems so I went back to Lubuntu.

I have read and worked on this for hours since yesterday and cannot find the problem, I am not a Linux newbie but I'm also not hugely advanced with terminal but I get the basics so my brain is now fried and I need help if anyone can offer it please.  I am getting the impression reading out there this is not an isolated problem to just me.

lspci -nnk | grep -iA2 net shows

```
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Gateway, Inc. Device [107b:0185]
    Kernel driver in use: sky2
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. T77H030.00 Wireless Mini PCIe Card [105b:e003]
    Kernel driver in use: wl

```
lsusb shows
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lsmod shows
```

Module                  Size  Used by
zram                   18525  1 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371880  10 bnep,rfcomm
joydev                 17377  0 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
lib80211_crypt_tkip    17619  0 
wl                   4207474  0 
snd_hda_codec_realtek    55704  1 
snd_hda_intel          48171  1 
snd_hda_codec         188738  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
kvm_amd                59958  0 
kvm                   431315  1 kvm_amd
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
lib80211               14352  2 wl,lib80211_crypt_tkip
edac_core              62312  0 
snd                    69141  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
psmouse                97626  0 
serio_raw              13413  0 
sp5100_tco             13979  0 
edac_mce_amd           22617  0 
k8temp                 12978  0 
soundcore              12680  1 snd
i2c_piix4              22106  0 
cfg80211              479757  1 wl
radeon               1402449  2 
ttm                    83995  1 radeon
drm_kms_helper         52651  1 radeon
drm                   296739  4 ttm,drm_kms_helper,radeon
video                  19318  1 acer_wmi
i2c_algo_bit           13413  1 radeon
wmi                    19070  1 acer_wmi
mac_hid                13205  0 
shpchp                 37032  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
pata_atiixp            13242  0 
sky2                   58057  0 
ohci_pci               13561  0 
ahci                   25819  2 
libahci                31898  1 ahci
```

ifconfig shows
```

eth0      Link encap:Ethernet  HWaddr 00:1d:72:e3:0c:5f  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fee3:c5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3713684 (3.7 MB)  TX bytes:771331 (771.3 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:23:4d:97:bf:3b  
          inet addr:192.168.0.23  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe97:bf3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:843 errors:0 dropped:0 overruns:0 frame:438516
          TX packets:614 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:387689 (387.6 KB)  TX bytes:68027 (68.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100057 (100.0 KB)  TX bytes:100057 (100.0 KB)


```

rfkill list shows
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by BenjaminCHILOE IS. on 2013-12-01
Hello stuart-andrews,

have you tried the section additional drivers, located in Settings? Because this section  can let you pick between private drivers or  opensurce drivers for linux for your wireless card. Try and check if you're  using the open source Linux drivers and firmware, and google if this wifi card has additional Private dirvers for Linux. 
Another choice maybe try Ndiswrapper Linux tool to install windows drivers for linux laptops.

---

### Post by stuart77 on 2013-12-02
The driver in use is the bcmwl-kernel-source STA driver.  I have tried the fwcutter driver too.

So far it's staying on tonight but one thing I did notice is the power - when installing the OS over the weekend the laptop was plugged in.  Tonight it wasn't and I noticed no battery icon appeared in the notification area.  I went into the power settings and it told me XFCE power manager is not launched and would I like to run it.  One of the posts I came across when searching indicated a power related issue.  If I have this problem again I can post more logs if that would help but could power management be an issue?

---

### Post by stuart77 on 2013-12-06
Still having problems, I have ran a software update to ensure I'm on the current kernel, wifi is really poor.  Any suggestions please?

---

### Post by tlk2drew on 2013-12-07
Disable WMM in your wireless router.  Should be under QoS.

---

### Post by stuart77 on 2013-12-07
WMM isn't option on my router, and have only experienced this problem in last 2 weeks, came out the blue on the existing 13.04 installation, still problem on clean 13.10 installation, must be some sort of issue on Ubuntu surely?

---

### Post by mario.net on 2013-12-07
To improve our Wi-Fi on Ubuntu and derivatives, we need to edit the file sysctl.conf to do it from a terminal type:For Ubuntu: gksu gedit / etc / sysctl.conf For Kubuntu, Xubuntu, Lubuntu, and other derivatives: sudo nano / etc / sysctl.conf And add at the end: net.ipv4.tcp_syncookies = 1 = 0 net.ipv4.tcp_window_scaling net. ipv4.tcp_ecn = 0And save (nano just type CTRL + X and then S).sysctl.confNow, again from the terminal, we set  iwconfig  (tool dedicated to setting   the parameters of the network interfaces) to 54 MB, to do so from a terminal type:sudo / etc / init.d / networking restart sudo iwconfig sudo iwconfig wlan0 rate 54Mand restart.

---


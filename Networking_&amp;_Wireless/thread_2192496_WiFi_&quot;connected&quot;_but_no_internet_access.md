---
title: "WiFi &quot;connected&quot; but no internet access"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by dekaru01 on 2013-12-08
I have a strange problem. I connect my laptop to my router's wireless network in 13.10, it says it's connected, but I can't access the internet. Pinging the router's IP results in something along the lines of "not reachable". Ditto if I ping the laptop from the router.
I have many other wireless devices connected to the router just fine. On the same machine that's not working with Ubuntu, I have Windows on and everything works just fine over there. Ubuntu itself connects just fine to other WiFi APs, just not to my router's.
It's a new router, this hasn't happened until yesterday when I set it up. It's not the router's fault - as I said, many other devices connect to it fine and Internet works. The same laptop when in Windows connects fine and Internet works.
Over the past couple of days I've been configuring a bunch of routers while in this Ubuntu installation, and some required some manual settings in Network Manager (that's what I think it's called). So I think maybe something got mangled in Wireless settings... but I don't know where to look. Please help.

System details: Dell Inspiron 13R N3010, Ubuntu 13.10 32-bit fully up to date. Ask away for anything else. Thanks in advance.

---

### Post by praseodym on 2013-12-08
Please show the terminal outputs of
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by dekaru01 on 2013-12-08
Thanks for the reply. Here's what I get (this is with wireless on, but not connected - for obvious reasons; I'm connected via ethernet at the moment):

```
lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl
05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Dell Device [1028:0455]
    Kernel driver in use: atl1c
```

```
lsusb
Bus 002 Device 003: ID 040b:2012 Weltrend Semiconductor 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
lsmod
Module                  Size  Used by
ums_realtek            17733  0 
usb_storage            48294  1 ums_realtek
nvram                  13986  0 
rfcomm                 53664  0 
parport_pc             31981  0 
bnep                   18893  2 
ppdev                  17391  0 
bluetooth             323622  10 bnep,rfcomm
binfmt_misc            13140  1 
uvcvideo               71309  0 
intel_powerclamp       14239  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
coretemp               13195  0 
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
kvm_intel             128218  0 
kvm                   364766  1 kvm_intel
ip6t_REJECT            12826  1 
xt_hl                  12465  6 
ip6t_rt                13259  3 
dell_laptop            17161  0 
dell_wmi               12665  0 
joydev                 17097  0 
sparse_keymap          13708  1 dell_wmi
dcdbas                 14383  1 dell_laptop
nf_conntrack_ipv6      18450  7 
nf_defrag_ipv6         26064  1 nf_conntrack_ipv6
lib80211_crypt_tkip    17387  0 
ipt_REJECT             12485  1 
xt_LOG                 17446  10 
xt_limit               12541  13 
xt_tcpudp              12756  18 
xt_addrtype            12563  4 
wl                   3999432  0 
nf_conntrack_ipv4      14492  7 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  14 
radeon               1307301  5 
snd_hda_codec_hdmi     40373  1 
ip6table_filter        12711  1 
ip6_tables             17819  1 ip6table_filter
snd_hda_codec_realtek    45592  1 
snd_hda_intel          42658  5 
ttm                    71886  1 radeon
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12645  0 
drm_kms_helper         46867  1 radeon
nf_nat                 25588  1 nf_nat_ftp
snd_hwdep              13272  1 snd_hda_codec
nf_conntrack_ftp       14056  1 nf_nat_ftp
drm                   242354  7 ttm,drm_kms_helper,radeon
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
nf_conntrack           82912  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12706  1 
lib80211               14040  2 wl,lib80211_crypt_tkip
ip_tables              17987  1 iptable_filter
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
cfg80211              401436  1 wl
i2c_algo_bit           13197  1 radeon
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
x_tables               22067  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
mei_me                 13933  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
mei                    66411  1 mei_me
snd                    60790  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lp                     13299  0 
wmi                    18590  1 dell_wmi
soundcore              12600  1 snd
psmouse                90642  0 
lpc_ich                16864  0 
serio_raw              13189  0 
microcode              18830  0 
video                  18777  0 
mac_hid                13037  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
atl1c                  40949  0 
ahci                   25579  2 
libahci                26554  1 ahci
```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by dekaru01 on 2013-12-09
I've put 13.10 on a USB stick and ran it on the same laptop. Without changing any configs for wireless, it connects fine AND the internet actually works.
I've checked in Additional Drivers and the default install doesn't use the proprietary STA Broadcom driver, while my system does. That's because at some point over the past couple of years the open source driver gave me a lot of trouble, randomly disconnecting (and not even showing as "disconnected") and such. So a while back I turned to the proprietary driver and never looked back. All worked fine until this 'incident'.

Any ideas? Should I try and get rid of the STA driver and use the open source one? If so, how?
Is it possible to just reinstall the STA driver without leaving any trace of its configs and such? If so, how?
Any other ideas?

Once again, thanks in advance.

---

### Post by pbrane on 2013-12-09
You might try removing the manual settings in NetworkManger that you set. It sounds like there is something not right in the manual settings. Also you might want to remove the wireless connection for the one that's not working. Then try to connect again.

---

### Post by dekaru01 on 2013-12-09
I've deleted the connection from NM, then re-added it countless times. There are no 'manual' settings (that I know of) currently in NM. It's all the default things - like I just connected to it for the first time. This really looks like a driver issue to me, but hey - I'm no expert.

---

### Post by praseodym on 2013-12-09
Same as here:

[http://ubuntuforums.org/showthread.php?t=2192555&p=12868571#post12868571](http://ubuntuforums.org/showthread.php?t=2192555&p=12868571#post12868571)

---

### Post by dekaru01 on 2013-12-09
> **praseodym said:**
> Same as here:

[http://ubuntuforums.org/showthread.php?t=2192555&p=12868571#post12868571](http://ubuntuforums.org/showthread.php?t=2192555&p=12868571#post12868571)

Thanks, I'll try that in a few hours. One more thing. When I switched to the STA driver I couldn't get the wireless interface to autostart upon boot. After each boot I had to sudo modprobe wl. So I asked around and someone told me how to add "wl" to a file somewhere, which would make that command execute upon boot each time. However, many months have passed and now I have no clue what that file is (where I added the wl command). Any insight? I assume that I have to comment that out, otherwise I'll have boot troubles (or wireless errors), if I try the 'native' driver as you suggested in the linked post.

---

### Post by praseodym on 2013-12-09
The whitelist is **/etc/modules**, the blacklist can be checked via
```

grep wl /etc/modprobe.d/*
```
But that commands remove the respective blacklist files

---

### Post by dekaru01 on 2013-12-09
> **praseodym said:**
> The whitelist is **/etc/modules**, the blacklist can be checked via
```

grep wl /etc/modprobe.d/*
```
But that commands remove the respective blacklist files

It was /etc/modules (where I added "wl"). Thanks! Btw, I also see an "lp" line in there. Is that OK?

Also, does this look fine?

```
grep wl /etc/modprobe.d/*
/etc/modprobe.d/blacklist-bcm43.conf:# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
/etc/modprobe.d/blacklist-local.conf:blacklist wl
/etc/modprobe.d/blacklist-watchdog.conf:blacklist twl4030_wdt
/etc/modprobe.d/broadcom-sta-common.conf:# wl module from Broadcom conflicts with ssb
/etc/modprobe.d/broadcom-sta-common.conf:install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
/etc/modprobe.d/iwlwifi.conf:# /etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/iwlwifi.conf:# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
/etc/modprobe.d/iwlwifi.conf:# microcode file installed on the system.  When removing iwlwifi, first
/etc/modprobe.d/iwlwifi.conf:# remove the iwl?vm module and then iwlwifi.
/etc/modprobe.d/iwlwifi.conf:remove iwlwifi \
/etc/modprobe.d/iwlwifi.conf:(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
```

---

### Post by praseodym on 2013-12-09
"lp" is ok, these will be deleted:
```

/etc/modprobe.d/[COLOR="#FF0000"]blacklist-bcm43.conf[/COLOR]:# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
/etc/modprobe.d/[COLOR="#FF0000"]blacklist-local.conf[/COLOR]:blacklist wl
...
/etc/modprobe.d/[COLOR="#FF0000"]broadcom-sta-common.conf[/COLOR]:# wl module from Broadcom conflicts with ssb
/etc/modprobe.d/[COLOR="#FF0000"]broadcom-sta-common.conf[/COLOR]:install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
```

---

### Post by dekaru01 on 2013-12-09
> **praseodym said:**
> Same as here:

[http://ubuntuforums.org/showthread.php?t=2192555&p=12868571#post12868571](http://ubuntuforums.org/showthread.php?t=2192555&p=12868571#post12868571)

Followed the instructions in the linked post. Now "Enable Wireless" isn't even an option anymore in the menu corresponding to the network indicator. All I have is "Enable Networking". It's like the Wi-Fi card doesn't even exist. In Additional Drivers, it says "this device is not working" under the Wi-Fi card's heading.

So now what? :)

---

### Post by dekaru01 on 2013-12-09
OK, so I also purged "broadcom-sta-common" and "broadcom-sta-source". Then (but may be unrelated), with a sudo modprobe brcmsmac the wireless networks 'magically' showed up. I added "brcmsmac" to /etc/modules and voila! Everything works now, using the brcmsmac driver. I hope I'll be more lucky with it this time, since before it was really problematic.

Thanks for all your help.

Just one more question: if I ever feel the need to try the STA driver again, what's the best procedure? Should I just go to Additional Drivers and enable it from there? Or is it quicker/safer/easier to do it via Terminal? If so, how?

---

### Post by praseodym on 2013-12-11
Via terminal:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms bcmwl-kernel-source
```

---

### Post by dekaru01 on 2013-12-13
> **praseodym said:**
> Via terminal:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms bcmwl-kernel-source
```

Thanks.

---

### Post by andrespara on 2013-12-29
What do you exactly mean by adding "brcmsmac" to /etc/modules? I am a newbie here so I would like to know the command line needed. THANKS

By running > sudo modprobe [COLOR=#000080]brcmsmac[/COLOR] the networks appeared and everything is fine, thank you and **praseodym.**

---

### Post by jerry34 on 2014-12-16
Have same problems with my dell latitude cannot ping my router in windows but in Linux I have no problems with wifi.  I would suggest a different router config.

---

### Post by wildmanne39 on 2014-12-16
Old thread closed! Please do not post in old threads.
Thanks

---


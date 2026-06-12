---
title: "Soooo CLOSE - Broadcom 4313 connects to unsecured router - but not to mine"
date: 2013-09-14
forum: Networking &amp; Wireless
---

### Post by Donny Bahama on 2013-09-14
Save yourself some time - skip to the 2nd post.  :)

This has been a bloody freaking NIGHTMARE. I don't normally offer to install Linux for someone unless I boot a live distro and verify that wireless and sound are both working. But the Broadcom 4313 tricked me -- it showed that I was connected and it successfully completed a Google search.  It wasn't until after I installed Precise and setup a nice dual-boot system (with Windows networking disabled - for a virus-prone customer who has a handful of must-have Windows apps) that my client discovered that download speeds were drastically slower on the linux side, and often didn't work at all. With all the time I've put in this thing, my hourly rate is quickly approaching minimum wage. 

I tried a variety of Broadcom-related solutions that did not work - until I found [this thread]("http://ubuntuforums.org/showthread.php?t=1889170") (which discusses the exact Broadcom wireless card & version that I am working with). I went through the step-by-steps and at one point (in the wee hours of the morning last night) I actually had it working. But then I rebooted and *POOF* everything good vanished.

How I got here...

I followed the basic steps outlined in the 2nd post of the thread:
[LIST=1]
[*]Check to see what bcm drivers are loaded using [FONT=Courier New]lsmod | grep "b43\|ssb\|bcma\|wl"[/FONT] 
[*]rmmod them and blacklist them 
[*]re/install bcmwl-kernel-source, broadcom-sta-source and broadcom-sta-common 
[/LIST]

That worked and I was very happy. Then I rebooted and b43, bcma and ssb were all back (and wl was not.) My blacklist.conf was completely ignored.

```
# cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist b43
blacklist amd76x_edac
blacklist hp_wmi
blacklist ssb
blacklist bcma
blacklist brmcsmac

```

The next thing I tried was to find the ko files for b43, bcma, brmcsmac, etc. in /lib/modules and rename them to .ko9. On reboot, they were no longer reenabled, but now even my wired netowrking was broken so I put them all back. I tried various additional iterations of the basic steps above; mostly I tried not to reboot since doing so always resurrected those accursed blacklisted drivers. I also tried backing up /boot/initrd.img... and doing an update-initramfs -u after rmmod'ing b43, bcma and ssb. No joy.

Finally, I decided to try building a new driver (again, per the instructions in the linked thread) using the driver on Broadcom's website and the (attached) readme - and this ***almost*** works... I can connect to a neighbor's router (no encryption) but not to my own (WPA/WPA2 Personal). 

```
# nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1  [MaunaLoa] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        XX:XX:XX:XX:66:3F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    keisha09:        Infra, XX:XX:XX:XX:95:10, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    keisha09-guest:  Infra, XX:XX:XX:XX:95:12, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    A3CF59:          Infra, XX:XX:XX:XX:CF:59, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    [COLOR=#ff0000]MaunaLoa:        Infra, XX:XX:XX:XX:6A:07, Freq 2447 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2     <-- That's my router[/COLOR]

```

```
 # lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: XX:XX:XX:XX:66:3f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:c2500000-c2503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: XX:XX:XX:XX:3f:88
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=10.88.7.107 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff

```

```
# lspci -nn | grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)

```

```
# lsmod
Module                  Size  Used by
lib80211_crypt_tkip    17390  0 
wl                   4207769  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
ext2                   73795  1 
ip6t_LOG               16974  4 
xt_hl                  12521  6 
ip6t_rt                12558  3 
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
joydev                 17693  0 
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
psmouse                87603  0 
serio_raw              13211  0 
snd_hwdep              13668  1 snd_hda_codec
xt_limit               12711  12 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
xt_tcpudp              12603  26 
snd_seq_midi           13324  0 
xt_addrtype            12713  4 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
xt_state               12578  14 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
wmi                    19256  0 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
mac80211              506816  0 
iptable_filter         12810  1 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              27473  1 iptable_filter
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
cfg80211              205544  2 wl,mac80211
mac_hid                13253  0 
i915                  468651  3 
rts_pstor             445196  0 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 

```

```
 # iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.

```

My head hurts from banging it against my desk. Please, PLEASE help me, wireless gurus!
If there's any additional info needed, please let me know and I'll post it right away!

Thank you for your time and consideration!

---

### Post by Donny Bahama on 2013-09-14
Well, I kept digging and found a post somewhere that talked about a bug in the 3.2.x kernel that applied to this card. So I [upgraded]("http://www.perseosblog.com/en/posts/how-to-install-kernel-35x-lts-ubuntu-1204-mint-13-derivates/") and now it's working... sort of.

Still, whenever I reboot, b43, bcma and ssb all come back. I have to rmmod each of them, then modprobe wl, then my wireless works.

They're already blacklisted (see above post). I'd really appreciate some help on how to keep them from reenabling at each boot.

---

### Post by Hadaka on 2013-09-14
Hi, please post the output of..
```
cat /etc/modules
lsmod
```
thanks.

---


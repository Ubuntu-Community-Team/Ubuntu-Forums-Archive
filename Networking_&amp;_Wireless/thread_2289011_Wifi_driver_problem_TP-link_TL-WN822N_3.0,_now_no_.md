---
title: "Wifi driver problem TP-link TL-WN822N 3.0, now no connection"
date: 2015-07-31
forum: Networking &amp; Wireless
---

### Post by reece1984 on 2015-07-31
Hello everyone, 


I have a TP-Link TL-WN822N ver 3.0 which was disconnecting every 5 minutes. 


I've followed these instructions:
[https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md](https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md)


But then realised that they are not appropriate for this TP-link device. 


And then tried to correct it by following this link with no success:
[http://ubuntuforums.org/showthread.php?t=2158548](http://ubuntuforums.org/showthread.php?t=2158548)


Then I ran the commands suggested in this link to provide my setup information as follows:
[http://askubuntu.com/questions/401045/wifi-problems-with-tp-link-wn822n-ubuntu-13-10](http://askubuntu.com/questions/401045/wifi-problems-with-tp-link-wn822n-ubuntu-13-10)

Thank you very much for your support. 


Here is the output:
```
james@james-H61M-S2PV:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
james@james-H61M-S2PV:~$ lsusb
Bus 002 Device 003: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c52e Logitech, Inc. 
Bus 001 Device 003: ID 04e8:61b6 Samsung Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
james@james-H61M-S2PV:~$ lspci -k -nn | grep -A 3 -i net 
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
  Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
  Kernel driver in use: atl1c
04:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. Device [1283:8892] (rev 30)
james@james-H61M-S2PV:~$ sudo lshw -C network 
[sudo] password for james: 
  *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 50:e5:49:14:da:eb
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f7100000-f713ffff ioport:d000(size=128)
james@james-H61M-S2PV:~$ lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
dm_crypt               23177  0 
snd_hda_codec_hdmi     46368  1 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143187  0 
kvm                   455794  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_hda_codec_realtek    65626  1 
joydev                 17381  0 
snd_hda_intel          56531  5 
snd_hda_codec         192980  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
serio_raw              13462  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
nvidia              10744943  54 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
rfcomm                 69160  0 
snd_timer              29482  2 snd_pcm,snd_seq
bnep                   19624  2 
lpc_ich                21080  0 
bluetooth             391136  10 bnep,rfcomm
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   303102  2 nvidia
nls_iso8859_1          12713  2 
mei_me                 18627  0 
mac_hid                13205  0 
soundcore              12680  1 snd
mei                    82276  1 mei_me
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
psmouse               106647  0 
video                  19476  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
usb_storage            62209  1 
atl1c                  46086  0 
james@james-H61M-S2PV:~$ iwconfig 
eth0      no wireless extensions.


lo        no wireless extensions.


james@james-H61M-S2PV:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 50:e5:49:14:da:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:471949 (471.9 KB)  TX bytes:471949 (471.9 KB)


james@james-H61M-S2PV:~$ sudo iwlist scan 
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


james@james-H61M-S2PV:~$ uname -r -m 
3.13.0-57-generic x86_64
james@james-H61M-S2PV:~$ nm-tool


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        50:E5:49:14:DA:EB


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




james@james-H61M-S2PV:~$ sudo rfkill list 
james@james-H61M-S2PV:~$ 

```

---

### Post by praseodym on 2015-08-01
Check driver version 1.10:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-12-04-5-und-14-04-fuer-Kernel-3-11-3-13-und-3-16](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-12-04-5-und-14-04-fuer-Kernel-3-11-3-13-und-3-16)

---


---
title: "Web Browser super slow"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by moisesrntr on 2013-12-30
Hello Everyone!
When connected to the internet via wireless it runs really slow, for example, when I’m logged in to my Google drive account and try to access a folder it takes super long to load and that's if it does. It sometimes does it in other websites, But when I connect my laptop to my router via wired connection it runs fine and all folders on my Google drive account open up smoothly. Could it be a driver issue. I install Xubuntu 12.04 on my laptop Windows XP. I'm really starting to like Xubuntu and I want to keep enjoying it.

---

### Post by praseodym on 2013-12-31
Please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
sudo iwlist scan
```
Which browser do you use? If it is Firefox type
```

about:config
```
into the URL-line, search for "network.dns.disableIPv6" and change it to "true" via double click. Restart FF.

---

### Post by moisesrntr on 2013-12-31
moises@molaptop:~$ lspci -nnk | grep -iA2 net
04:02.0 Ethernet controller [0200]: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7094]
    Kernel driver in use: ath5k
--
04:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: 8139too
moises@molaptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 003: ID 1d57:0008  
moises@molaptop:~$ lsmod
Module                  Size  Used by
vesafb                 13516  0 
joydev                 17393  0 
microcode              18187  0 
snd_atiixp             19381  3 
snd_atiixp_modem       18656  6 
snd_ac97_codec        110213  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
arc4                   12473  2 
snd_pcm                80916  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
pcmcia                 39826  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436493  1 ath5k
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                738089  2 
snd                    62218  24 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178877  3 ath5k,ath,mac80211
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
rfcomm                 38139  4 
psmouse                96744  0 
bnep                   17830  2 
parport_pc             32114  0 
soundcore              14635  1 snd
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
serio_raw              13027  0 
binfmt_misc            17292  1 
snd_page_alloc         14115  3 snd_atiixp,snd_atiixp_modem,snd_pcm
video                  19115  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197641  4 radeon,ttm,drm_kms_helper
i2c_piix4              13093  0 
i2c_algo_bit           13199  1 radeon
mac_hid                13077  0 
shpchp                 32265  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    81731  1 usbhid
8139too                23283  0 
8139cp                 26688  0 
pata_atiixp            12999  2 
moises@molaptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:a5:66:2a  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fea5:662a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81519467 (81.5 MB)  TX bytes:4636905 (4.6 MB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:957 errors:0 dropped:0 overruns:0 frame:0
          TX packets:957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90435 (90.4 KB)  TX bytes:90435 (90.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:f5:b7:29:14  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:f5ff:feb7:2914/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1599495 (1.5 MB)  TX bytes:297055 (297.0 KB)

moises@molaptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"gogetter"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:25:9C:D9:FC:74   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:560   Missed beacon:0

eth0      no wireless extensions.

moises@molaptop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search sc.rr.com
moises@molaptop:~$ sudo iwlist scan

---

### Post by moisesrntr on 2013-12-31
network.dns.disableIPv6 it is in "true".
By the way, Im an infant to xubuntu and learning as I go along. I hope the info I gave is what you where looking for. If not you mind giving me step by step instructions on how to give you the right terminal outputs. Was I suppose to do this command with the ethernet unplugged and go wireless or doesnt matter? thanks for your patients with this rookie.

---

### Post by praseodym on 2014-01-01
Hi,

deactivate the hardware encryption of the driver:
```

echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
WPA2 is not affected by this.

---

### Post by moisesrntr on 2014-01-02
It looks like its working fine now, Thank you!

One more question...I notice in Thunderbird Mail there is no sound when receiving new mail. I'm currently using Thunderbird 24.2.0

---

### Post by praseodym on 2014-01-02
Here with TB 26.2: Settings->Settings->"somewhere". ;)

---


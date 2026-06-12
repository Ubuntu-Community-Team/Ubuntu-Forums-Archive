---
title: "no wired connection = Kubuntu lockup?"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by StuartCarter on 2013-10-22
if I start Kubuntu without a wired connection, the system locks up.

If I remove the ethernet cable, Kubuntu locks up.

Version 12.04.3

---

### Post by varunendra on 2013-10-24
Then when does the system/OS DOES NOT lock ? :P
Do you even get the box running in any case?

What if you disable the Ethernet in the BIOS, then boot?

---

### Post by StuartCarter on 2013-10-24
the OS works fine on ethernet. Without ethernet, the OS locks up - whether cable unplugged, or disabled in BIOS.

---

### Post by varunendra on 2013-10-24
Oh, sorry I misread the first line of your original post.

Is the Ethernet connection set to get IP from DHCP? Please post the outputs of -
```
lspci -nnk | grep -A2 0200
ifconfig
nm-tool
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
lsmod
```

Please post the outputs within '**Code**' tags.

---

### Post by StuartCarter on 2013-10-24
```
machine:~$ lspci -nnk | grep -A2 0200
07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
        Subsystem: Acer Incorporated [ALI] Device [1025:0614]
        Kernel driver in use: atl1c
machine:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 38:60:77:a9:28:5b  
          inet6 addr: fe80::3a60:77ff:fea9:285b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1109669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:763346 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:752635776 (752.6 MB)  TX bytes:97263239 (97.2 MB)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4313173 (4.3 MB)  TX bytes:4313173 (4.3 MB)

wlan0     Link encap:Ethernet  HWaddr 74:de:2b:b2:59:89  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76de:2bff:feb2:5989/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:592514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:192620912 (192.6 MB)  TX bytes:26132404 (26.1 MB)

machine:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             disconnected
  Default:           no
  HW Address:        38:60:77:A9:28:5B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0  [hos] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        74:DE:2B:B2:59:89

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *MINE:            Infra, C0:83:0A:CF:A3:51, Freq 2462 MHz, Rate 54 Mb/s, Strength 61 WPA WPA2
    BHNDVW3201B70C4: Infra, 68:94:23:56:32:E8, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA
    cdw:             Infra, C0:C1:C0:7B:87:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    2WIRE100:        Infra, 28:16:2E:36:BA:C9, Freq 2422 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Rusmisel_wifi:   Infra, 7C:E9:D3:84:90:3F, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WEP

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             208.67.222.222
    DNS:             208.67.220.220


machine:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

machine:~$ cat /etc/NetworkManagre/NetworkManager.conf
cat: /etc/NetworkManagre/NetworkManager.conf: No such file or directory
stuart@ThinkDrinkLocal:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
machine:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
pci_stub               12622  1 
joydev                 17693  0 
vboxpci                23237  0 
vboxnetadp             13382  0 
vboxnetflt             23478  0 
vboxdrv               287130  3 vboxpci,vboxnetadp,vboxnetflt
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_codec_realtek   224173  1 
snd_hda_codec_hdmi     32474  1 
snd_seq_midi           13324  0 
snd_hda_intel          33719  5 
snd_rawmidi            30748  1 snd_seq_midi
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
psmouse                97519  0 
ath9k                 132428  0 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
k10temp                13166  0 
serio_raw              13211  0 
mac80211              506862  1 ath9k
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
snd_timer              29990  2 snd_pcm,snd_seq
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205774  3 ath9k,mac80211,ath
sp5100_tco             13791  0 
i2c_piix4              13301  0 
snd                    79041  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180113  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41718  0 
ums_realtek            18248  0 
radeon                804577  3 
video                  19651  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   241971  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
wmi                    19256  1 acer_wmi
usb_storage            49198  1 ums_realtek
stuart@ThinkDrinkLocal:~$ 


```

---

### Post by varunendra on 2013-10-24
> **StuartCarter said:**
> ```

machine:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 38:60:77:a9:28:5b  
          inet6 addr: fe80::3a60:77ff:fea9:285b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1109669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:763346 errors:0 dropped:0 overruns:0 carrier:[COLOR="#FF0000"]5[/COLOR]
          collisions:0 txqueuelen:1000 
         ** RX bytes:752635776 (752.6 MB)  TX bytes:97263239 (97.2 MB)**
          Interrupt:42 
```
Was it being used before disconnecting? How have you disabled it?

Is it safe to assume that you have "disconnected" it from Network Manager's menu and that doesn't cause any problem?

And this..
```
machine:~$ cat /etc/NetworkMana**[COLOR="#FF0000"]gre[/COLOR]**/NetworkManager.conf
cat: /etc/NetworkManagre/NetworkManager.conf: No such file or directory
```
was a mistake on my part, a typo. Please use the corrected command -
```
cat /etc/NetworkManager/NetworkManager.conf
```

For now, please try these -
[LIST]
[*]Make sure IPv6 is set to "Ignore" in Network Manager settings for the connection.
[*]Disable (uncheck the checkbox) "Connect Automatically" option for the Ethernet connection in Network Manager.
[/LIST]
Then see if disconnecting the cable still freezez. Try it after a reboot too.

---

### Post by StuartCarter on 2013-10-25
Wired network is the only way I can use my laptop, so it's more or less a desktop substitute.

machine:~$ cat /etc/NetworkManager/NetworkManager.conf  [main] plugins=ifupdown,keyfile dns=dnsmasq  no-auto-default=38:60:77:A9:28:5B,AA:74:66:11:A5:8B,  [ifupdown] managed=false stuart@ThinkDrinkLocal:~$                        

IPV6 was already disabled. I disabled "connect automatially" and rebooted, machine locked up just after I entered my login password.

---


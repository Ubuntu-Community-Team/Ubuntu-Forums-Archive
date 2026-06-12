---
title: "wireless hard blocked fujitsu siemens laptop"
date: 2014-02-14
forum: Networking &amp; Wireless
---

### Post by jjk2 on 2014-02-14
[B]Solution for others with this problem:

update the bios!!

---------------------------------------------------------------------------[/B]

Hey guys, 

I recently got a new laptop, it used to run xp, but was actually too slow to run it. So I installed backbox linux (an ubuntu derivative for hacking, in case you dont know).
It works like a breeze now, but,
The wireless doesn't work. It is hard blocked, and the button to unblock it doesnt work. below a list of information about the laptop, and a couple of solutions I tried (which didn't work ofcourse, else i wouldnt post here...).

1. Laptop info
Fujitsu Siemens amilo pro 8210

lspci and lsmod:
```
jjk@jjk-laptop:~$ lspci | grep -i wireless
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
jjk@jjk-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            17268  1 
arc4                   12509  2 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek    50304  1 
snd_hda_intel          43326  4 
iwl3945                64640  0 
snd_hda_codec         169534  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
iwlegacy               88342  1 iwl3945
snd_hwdep              13276  1 snd_hda_codec
mac80211              534884  2 iwl3945,iwlegacy
snd_pcm                94597  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28930  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 55837  0 
joydev                 17329  0 
yenta_socket           44614  0 
snd                    61270  19 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
pcmcia_rsrc            18495  1 yenta_socket
cfg80211              416271  3 iwl3945,iwlegacy,mac80211
lpc_ich                16987  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
irda                  108020  0 
pcmcia_core            22396  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                92648  0 
ppdev                  17423  0 
parport_pc             32114  1 
serio_raw              13189  0 
crc_ccitt              12627  1 irda
mac_hid                13077  0 
lp                     13359  0 
parport                40930  3 ppdev,parport_pc,lp
i915                  615640  2 
drm_kms_helper         47306  1 i915
ahci                   25703  2 
sdhci_pci              18588  0 
drm                   247722  3 i915,drm_kms_helper
sdhci                  37958  1 sdhci_pci
libahci                30834  1 ahci
i2c_algo_bit           13316  1 i915
sky2                   53656  0 
video                  19046  1 i915
zram                   18239  1 

```

ifconfig and iwconfig:
```
jjk@jjk-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:ba:a1:42  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:feba:a142/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6950546 (6.9 MB)  TX bytes:869971 (869.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

jjk@jjk-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


```

dmesg: (the part about wireless)
```
[   12.561741] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   12.561748] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   12.561816] iwl3945 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   12.602561] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   12.602569] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   12.602650] iwl3945 0000:04:00.0: irq 44 for MSI/MSI-X
[   12.622477] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   12.683539] autoconfig: line_outs=1 (0xb/0x0/0x0/0x0/0x0) type:line
[   12.683546]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.683549]    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.683551]    mono: mono_out=0x0
[   12.683553]    inputs:
[   12.683556]      Internal Mic=0x10
[   12.683559]      Mic=0xd
[   12.683562] realtek: Enabling init ASM_ID=0x1205 CODEC_ID=10ec0861
[   12.732368] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   12.853954] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   12.855469] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   12.892212] cfg80211: World regulatory domain updated:
[   12.892219] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.892222] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.892226] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.892229] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.892232] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.892235] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.337083] type=1400 audit(1392399478.000:2): apparmor="STATUS" operation="profile_load" parent=750 profile="unconfined" name="/sbin/dhclient" pid=771 comm="apparmor_parser"
[   13.337098] type=1400 audit(1392399478.000:3): apparmor="STATUS" operation="profile_load" parent=750 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=771 comm="apparmor_parser"
[   13.337107] type=1400 audit(1392399478.000:4): apparmor="STATUS" operation="profile_load" parent=750 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=771 comm="apparmor_parser"
[   13.337126] type=1400 audit(1392399478.000:5): apparmor="STATUS" operation="profile_replace" parent=767 profile="unconfined" name="/sbin/dhclient" pid=772 comm="apparmor_parser"
[   13.337140] type=1400 audit(1392399478.000:6): apparmor="STATUS" operation="profile_replace" parent=767 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=772 comm="apparmor_parser"
[   13.337149] type=1400 audit(1392399478.000:7): apparmor="STATUS" operation="profile_replace" parent=767 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=772 comm="apparmor_parser"
[   13.338073] type=1400 audit(1392399478.000:8): apparmor="STATUS" operation="profile_replace" parent=750 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=771 comm="apparmor_parser"
[   13.338083] type=1400 audit(1392399478.000:9): apparmor="STATUS" operation="profile_replace" parent=750 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=771 comm="apparmor_parser"
[   13.338112] type=1400 audit(1392399478.000:10): apparmor="STATUS" operation="profile_replace" parent=767 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=772 comm="apparmor_parser"
[   13.338122] type=1400 audit(1392399478.000:11): apparmor="STATUS" operation="profile_replace" parent=767 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=772 comm="apparmor_parser"
[   14.492117] init: failsafe main process (862) killed by TERM signal
[   21.038383] sky2 0000:02:00.0 eth0: enabling interface
[   21.038865] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.041312] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.070604] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   21.842456] init: anacron main process (1057) killed by TERM signal
[   22.785794] sky2 0000:02:00.0 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   22.785833] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  927.193189] cfg80211: Calling CRDA to update world regulatory domain
[  927.203755] cfg80211: World regulatory domain updated:
[  927.203762] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  927.203765] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  927.203769] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  927.203772] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  927.203775] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  927.203779] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  927.268421] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  927.268427] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  927.268491] iwl3945 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[  927.308848] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[  927.308854] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  927.308932] iwl3945 0000:04:00.0: irq 44 for MSI/MSI-X
[  927.309630] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[  927.479260] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
[  927.479499] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch
[  927.479718] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  927.572747] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch
[  927.573339] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch


```

lshw -C network:
```
root@jjk-laptop:/home/jjk# lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:0a:e4:ba:a1:42
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.38 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:d2000000-d2003fff ioport:2000(size=256) memory:d0000000-d001ffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan1
       version: 02
       serial: 00:13:02:e3:7c:e3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.11.0-15-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:d4000000-d4000fff
```

ubuntu version:
```
root@jjk-laptop:/home/jjk# lsb_release -d
Description:    Ubuntu 12.04.4 LTS
```

kernel:
```
root@jjk-laptop:/home/jjk# uname -mr
3.11.0-15-generic i686
```

Restarting network:
```
root@jjk-laptop:/home/jjk# service networking restart
stop: Unknown instance: 
networking stop/waiting

```

--------------------------------------------------------------------------------------

Solutions I tried:

after doing:
modprobe -r iwl3945
modprobe iwl3945
rfkill unblock all

it looks like this:
```
root@jjk-laptop:/home/jjk# rfkill list
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@jjk-laptop:/home/jjk# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
root@jjk-laptop:/home/jjk# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:ba:a1:42  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:feba:a142/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6995404 (6.9 MB)  TX bytes:1324382 (1.3 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

root@jjk-laptop:/home/jjk# ifconfig wlan1 up
SIOCSIFFLAGS: No such device


```

[B]Solution 2:
#modprobe wistron_btns 

it gave an error, which i can't reproduce now, anyway it has no support for my laptop yet.
The following patch should add the support. Any idea's to how i can get this patch?

[https://groups.google.com/forum/#!topic/linux.kernel/Mgi_mTgcT5s](https://groups.google.com/forum/#!topic/linux.kernel/Mgi_mTgcT5s)[/B]

Solution 3:
I saw something about fsam7400 but i cant find the package anywhere :( 
might be an solution though.

Solution 4:
compiling the package acerhk might help too. It didn't work, but i dont know why atm (if you need it just tell me)

I hope you are able to help me, any help is apreciated.
The actual problem is:
the wireless card is turned off, it should be turned on by a wireless button, which doesn't work in linux.
turning the hardblock off with rfkill seems to work but as you can see above the interface can't be put up.

it also doesn't work on the latest lubuntu

JJK

---

### Post by jjk2 on 2014-02-15
Bump

---

### Post by chili555 on 2014-02-15
This is the first and, I hope, last of a possibly increasingly complex techniques. Let's cross our fingers:```
gksudo gedit /etc/rc.local
```Right above the line exit 0 add a new line:```
rfkill unblock all
```Proofread, save and close gedit. Reboot with the ethernet detached and tell us if it's working as expected. If not, post:```
dmesg | grep -e iwl -e 80211
```Thanks.

---

### Post by jjk2 on 2014-02-16
hey chili,

thx for the reaction,

i tried what you said, same result as when i tried "rfkill unblock all" before :(

here's the output:
```
jjk@jjk-laptop:~$ sudo rfkill list
[sudo] password for jjk: 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
jjk@jjk-laptop:~$ dmesg | grep -e iwl -e 80211
[   10.943679] cfg80211: Calling CRDA to update world regulatory domain
[   11.876636] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   11.876642] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   11.876699] iwl3945 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.917407] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   11.917415] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   11.917520] iwl3945 0000:04:00.0: irq 44 for MSI/MSI-X
[   12.110812] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   12.452664] cfg80211: World regulatory domain updated:
[   12.452671] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.452675] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.452678] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.452682] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.452685] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.452688] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
jjk@jjk-laptop:~$ 


```

---

### Post by chili555 on 2014-02-16
> same result as when i tried "rfkill unblock all" beforeBut didn't you get it to work?> after doing:
modprobe -r iwl3945
modprobe iwl3945
rfkill unblock all

it looks like this:

```
root@jjk-laptop:/home/jjk# rfkill list
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked:[COLOR="#FF0000"] no[/COLOR]
```Is unloading and reloading iwl3945 perhaps the key?```
gksudo gedit /etc/rc.local
```Right above the line exit 0 change to:


```
modprobe -r iwl3945
modprobe iwl3945
rfkill unblock all
```Proofread, save and close gedit. Reboot with the ethernet detached and tell us if it's working as expected.

---

### Post by jjk2 on 2014-02-16
I tried it, the results where exactly the same as in my first post:

rfkill list shows its unblocked, but i cant put the interface up (is it really unblocked?)

thanks for your help 

JJK

---

### Post by chili555 on 2014-02-16
Please show us:```
cat /etc/network/interfaces
nm-tool
```Thanks.

---

### Post by jjk2 on 2014-02-16
the results (without ethernet connected)

```
root@jjk-laptop:/home/jjk# cat /etc/network/interfaces
auto lo
iface lo inet loopback

root@jjk-laptop:/home/jjk# nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unavailable
  Default:           no
  HW Address:        00:13:02:E3:7C:E3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:0A:E4:BA:A1:42

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


root@jjk-laptop:/home/jjk# 

```

---

### Post by chili555 on 2014-02-16
Boo hoo hoo! Why do I draw all the hard cases, mommie?? 

Let's have a peek at some additional items:```
rfkill list all
iwconfig
dmesg | grep iwl
```This is my favorite kind of problem; everything looks perfect but it won't start!

---

### Post by jjk2 on 2014-02-17
here it is:
```
root@jjk-laptop:/home/jjk# rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@jjk-laptop:/home/jjk# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
root@jjk-laptop:/home/jjk# dmesg | grep iwl
[   11.745043] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   11.745049] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   11.745106] iwl3945 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.785591] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   11.785598] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   11.785677] iwl3945 0000:04:00.0: irq 44 for MSI/MSI-X
[   12.026487] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   22.872200] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   22.872207] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   22.872262] iwl3945 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   22.912560] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   22.912566] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   22.912643] iwl3945 0000:04:00.0: irq 44 for MSI/MSI-X
[   22.913100] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   23.014057] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
[   23.014200] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch
[   23.090239] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch
[   23.090483] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch


```

as you can see rfkill says its unblocked but iwl3945 says its blocked.

---

### Post by jjk2 on 2014-02-18
could it be that this line is the problem
[   22.872262] iwl3945 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control

---

### Post by jjk2 on 2014-02-18
I think the best solution is to try and patch wistron_btns.
can anyone help me with how to do this....

I searched a lot, but I am not experienced enough with linux to do this.

if you know how to do this please react.

btw: I am on linux kernel version 3.11.0.

JJK

---


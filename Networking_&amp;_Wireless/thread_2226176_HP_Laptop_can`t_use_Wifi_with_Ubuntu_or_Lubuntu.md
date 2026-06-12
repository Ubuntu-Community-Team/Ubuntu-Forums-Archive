---
title: "HP Laptop can`t use Wifi with Ubuntu or Lubuntu"
date: 2014-05-25
forum: Networking &amp; Wireless
---

### Post by Fabzil on 2014-05-25
Hello everyone!

I have a **HP laptop** that was using **Lubuntu** but the **Wifi was not working from time to time** so I tried to install **Ubuntu** instead. I know the difference is almost just the GUI but anyway.

So I downloaded the lastest Ubuntu version, run the **md5sum** (which was successful) and install from USB to another USB (current harddrive is dead and non-replaceable).

But I have the same problem that with Lubuntu : 90% of the time when I boot the computer, I can't use internet. 10%, it works just fine.



Following "[HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?p=6183681")"...

**1 ) Machine Brand and Model (PC/Laptop)**:
```
Laptop : HP Elitebook 2540p
```


**2 ) Wireless Brand, Model and Wireless Chipset:**
$ lspci
$ lsusb
```

fabzil@fabzil-HP-EliteBook-2540p:~$ lspci | grep "Wireless"
fabzil@fabzil-HP-EliteBook-2540p:~$ lspci | grep "net"
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)


fabzil@fabzil-HP-EliteBook-2540p:~$ lsusb
Bus 002 Device 003: ID 13fe:5100 Kingston Technology Company Inc. Flash Drive
Bus 002 Device 004: ID 174c:5106 ASMedia Technology Inc. Transcend StoreJet 25M3
Bus 002 Device 005: ID 8564:1000  
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b163 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 138a:0007 Validity Sensors, Inc. VFS451 Fingerprint Reader
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

**3 ) check interface:**
Code:
$ ifconfig
$ iwconfig
```

fabzil@fabzil-HP-EliteBook-2540p:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b4:99:ba:e4:e5:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:d4600000-d4620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1353 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111359 (111.3 KB)  TX bytes:111359 (111.3 KB)

fabzil@fabzil-HP-EliteBook-2540p:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

**4 ) Check for modules:**
Code:
$ lsmod
```

fabzil@fabzil-HP-EliteBook-2540p:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
snd_hda_codec_hdmi     45303  1 
snd_hda_codec_idt      48877  1 
pata_pcmcia            16945  1 
uvcvideo               71309  0 
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
intel_powerclamp       14239  0 
coretemp               13195  0 
kvm                   388083  0 
pcmcia                 51828  1 pata_pcmcia
snd_hda_intel          42730  3 
crc32_pclmul           12967  0 
snd_hda_codec         164067  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
aesni_intel            18156  0 
snd_hwdep              13272  1 snd_hda_codec
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
cryptd                 15578  1 ablk_helper
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
joydev                 17101  0 
serio_raw              13230  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
intel_ips              18217  0 
snd_timer              28584  2 snd_pcm,snd_seq
yenta_socket           40201  0 
pcmcia_rsrc            18319  1 yenta_socket
snd                    60871  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
lpc_ich                16864  0 
soundcore              12600  1 snd
i915                  705396  3 
wmi                    18673  1 hp_wmi
tpm_infineon           17164  0 
drm_kms_helper         46907  1 i915
hp_accel               25756  0 
drm                   243792  4 i915,drm_kms_helper
lis3lv02d              19500  1 hp_accel
parport_pc             31981  0 
video                  18903  1 i915
i2c_algo_bit           13197  1 i915
mei_me                 14099  0 
input_polldev          13648  1 lis3lv02d
ppdev                  17391  0 
mei                    66735  1 mei_me
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
usb_storage            48417  4 
ahci                   25579  0 
e1000e                223034  0 
firewire_ohci          35529  0 
psmouse                91033  0 
sdhci_pci              18535  0 
firewire_core          61867  1 firewire_ohci
ptp                    18445  1 e1000e
libahci                26754  1 ahci
sdhci                  37779  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
pps_core               18799  1 ptp
fabzil@fabzil-HP-EliteBook-2540p:~$ lsmod | grep "wlan"
fabzil@fabzil-HP-EliteBook-2540p:~$

```


**5 ) Kernel boot messages**
Code:
$ dmesg
```

fabzil@fabzil-HP-EliteBook-2540p:~$ dmesg | grep "wlan"
fabzil@fabzil-HP-EliteBook-2540p:~$ dmesg | grep "network"
fabzil@fabzil-HP-EliteBook-2540p:~$ dmesg | grep "wire"
[    0.816127] pci 0000:43:06.0: proprietary Ricoh MMC controller disabled (via firewire function)
[    2.078742] firewire_ohci 0000:43:06.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    2.578808] firewire_core 0000:43:06.0: created device fw0: GUID 5566778811223344, S400
fabzil@fabzil-HP-EliteBook-2540p:~$ 

```


**6 ) Network configuration**
Code:
$ sudo lshw -C network
```

fabzil@fabzil-HP-EliteBook-2540p:~$ sudo lshw -C network
[sudo] password for fabzil: 
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: b4:99:ba:e4:e5:96
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:d4600000-d461ffff memory:d462a000-d462afff ioport:5020(size=32)
fabzil@fabzil-HP-EliteBook-2540p:~$ 

```

**7 ) Scan for networks:**
Code:
$ iwlist scan
```

fabzil@fabzil-HP-EliteBook-2540p:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

fabzil@fabzil-HP-EliteBook-2540p:~$ 

```



**8 ) Ubuntu Version: **
Code:
$ lsb_release -d
```

fabzil@fabzil-HP-EliteBook-2540p:~$ lsb_release -d
Description:	Ubuntu 14.04 LTS

```


**9 ) Kernel/architecture (including 32 vs. 64 bit): **
Code:
$ uname -mr
```

fabzil@fabzil-HP-EliteBook-2540p:~$ uname -mr
3.13.0-24-generic i686

```



**10 ) Restarting the network:**
Code:
$ sudo service networking restart
```

fabzil@fabzil-HP-EliteBook-2540p:~$ sudo service networking restart
stop: Job failed while stopping
start: Job is already running: networking
fabzil@fabzil-HP-EliteBook-2540p:~$ sudo service networking restart
stop: Job failed while stopping
start: Job is already running: networking
fabzil@fabzil-HP-EliteBook-2540p:~$ 

```

**11 - Bonus from me**
Code:
$ rfkill list
```

fabzil@fabzil-HP-EliteBook-2540p:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```


I hope we can found a solution to my problem :(


Thx you for your time and have a nice day!

---

### Post by UngusOptonline.ne on 2014-05-25
I have a Toshiba C55-A, standard computer, no upgrades etc that I dual boot with Win8. I've been having problems with Ubuntu not connecting to my wireless router-- Linksys E1000. It would recognize my home network and try to connect but it would fail over and over. At the same time Win8 would connect with no problem.

What has worked for me, and don't ask me why, is changing the boot order in the Bios (F2 while booting) First go around the USB was first in the boor order (b/c I had just installed Ubuntu off of a stick and had not changed it back yet) So I changed it to the Hard Drive, restart and laptop connects in Ubuntu, no problem. Works fine for a few days and then same problem. Restart after restart does nothing to solve it. So I go back into the BIos and make the USB first in the boot order (No stick in any USB port) Restart and it connects right away.

I've doen this about three times already and it's worked every time. I'm posting this so if any programmer working on bugs needs a lead to follow, well this may be it.

---

### Post by Hadaka on 2014-05-25
Hi, please post the output of,,
```
lspci -nnk | egrep '0200|0280'
```
thanks.

---

### Post by UngusOptonline.ne on 2014-05-25
> **Hadaka said:**
> Hi, please post the output of,,
```
lspci -nnk | egrep '0200|0280'
```
thanks.

Don't know if you asking for my results, but here they are

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)

---

### Post by Hadaka on 2014-05-25
hi, please follow this thread
[http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281)

your computer is different, but the wireless driver is the same,,this is correct for you also.
take your time..follow directions,

***  @ 				 				 					 						 	[**[COLOR=#000000]UngusOptonline.ne[/COLOR]**]("http://ubuntuforums.org/member.php?u=1909470")
I just now realized you hijacked the thread 
those directions are indeed for your machine and not the original poster
in the future please dont do this,,,.it causes confusion...start your own thread .

@ 				 				 					 						 	[**[COLOR=#000000]GoLookAndKill[/COLOR]**]("http://ubuntuforums.org/member.php?u=765788")
I am very sorry i missed this and it took time away from your post
please also post the out put of the code in post #3
thanks.

---

### Post by Fabzil on 2014-05-26
Hello ereryone!

Once again, I'm please with the quickness of answers one can enjoy on this forum :)

*I must first apologize for the img I posted in the original post, it contained profanities that have no place here. But the img was funny trust me :D ! *


Then, let's go in three points : 
-1- UngusOptonline.ne
Thx for the advice, I will try this the next time I shutdown the computer. Another voodoo-magic stuff I heard was to wait for Ubuntu to have started, and to suspend it and un-suspend it, and then the wifi may work :D ! For me this hadn't work but why not for you ^^


-2- THE WIFI IS WORKING AGAIN :)
I will now post the same command lines as in the original post and you guys will be able to compare the results and maybe it will help :) :)
[B]
2 ) Wireless Brand, Model and Wireless Chipset:[/B]
$ lspci
$ lsusb
```

fabzil@fabzil-HP-EliteBook-2540p:~$ lspci | grep "Net"
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
43:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)

fabzil@fabzil-HP-EliteBook-2540p:~$ lsusb
Bus 002 Device 003: ID 13fe:5100 Kingston Technology Company Inc. Flash Drive
Bus 002 Device 004: ID 174c:5106 ASMedia Technology Inc. Transcend StoreJet 25M3
**Bus 002 Device 005: ID 192f:0916 Avago Technologies, Pte. **
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b163 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 138a:0007 Validity Sensors, Inc. VFS451 Fingerprint Reader
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


**3 ) check interface:**

```

fabzil@fabzil-HP-EliteBook-2540p:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b4:99:ba:e4:e5:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:d4700000-d4720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:291653 (291.6 KB)  TX bytes:291653 (291.6 KB)

wlan0     Link encap:Ethernet  HWaddr 18:3d:a2:19:70:74  
          inet addr:192.168.1.77  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1a3d:a2ff:fe19:7074/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11876514 (11.8 MB)  TX bytes:1854026 (1.8 MB)


fabzil@fabzil-HP-EliteBook-2540p:~$ iwconfig
wlan0     IEEE 802.11abgn  ESSID:"GaneshaPosada"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:51:0C:15:D1   
          Bit Rate=36 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:706   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

```

**4 ) Check for modules:**
Code:
$ lsmod
```

fabzil@fabzil-HP-EliteBook-2540p:~$ lsmod
Module                  Size  Used by
hid_generic            12492  0 
usbhid                 47035  0 
hid                    87604  2 hid_generic,usbhid
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
snd_hda_codec_hdmi     45303  1 
snd_hda_codec_idt      48877  1 
pata_pcmcia            16945  1 
arc4                   12536  2 
iwldvm                214950  0 
mac80211              545990  1 iwldvm
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
snd_hda_intel          42730  5 
intel_powerclamp       14239  0 
snd_hda_codec         164067  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
coretemp               13195  0 
hp_wmi                 13702  0 
snd_hwdep              13272  1 snd_hda_codec
sparse_keymap          13708  1 hp_wmi
pcmcia                 51828  1 pata_pcmcia
kvm                   388083  0 
snd_pcm                85501  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
crc32_pclmul           12967  0 
aesni_intel            18156  0 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
cryptd                 15578  1 ablk_helper
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  705396  8 
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
joydev                 17101  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
serio_raw              13230  0 
snd                    60871  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
intel_ips              18217  0 
drm_kms_helper         46907  1 i915
iwlwifi               147953  1 iwldvm
lpc_ich                16864  0 
yenta_socket           40201  0 
pcmcia_rsrc            18319  1 yenta_socket
cfg80211              409394  3 iwlwifi,mac80211,iwldvm
drm                   243792  4 i915,drm_kms_helper
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
soundcore              12600  1 snd
mei_me                 14099  0 
mei                    66735  1 mei_me
i2c_algo_bit           13197  1 i915
wmi                    18673  1 hp_wmi
tpm_infineon           17164  0 
hp_accel               25756  0 
video                  18903  1 i915
parport_pc             31981  0 
lis3lv02d              19500  1 hp_accel
input_polldev          13648  1 lis3lv02d
ppdev                  17391  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
usb_storage            48417  3 
ahci                   25579  0 
sdhci_pci              18535  0 
e1000e                223034  0 
sdhci                  37779  1 sdhci_pci
psmouse                91033  0 
firewire_ohci          35529  0 
libahci                26754  1 ahci
ptp                    18445  1 e1000e
firewire_core          61867  1 firewire_ohci
pps_core               18799  1 ptp
crc_itu_t              12627  1 firewire_core


```


5 ) Kernel boot messages
Code:
$ dmesg
```

fabzil@fabzil-HP-EliteBook-2540p:~$  dmesg | grep "wlan"
[   24.444763] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.445153] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.918471] wlan0: authenticate with 00:23:51:0c:15:d1
[   27.922008] wlan0: send auth to 00:23:51:0c:15:d1 (try 1/3)
[   27.924286] wlan0: authenticated
[   27.924556] iwlwifi 0000:43:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   27.924560] iwlwifi 0000:43:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   27.924562] iwlwifi 0000:43:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   27.924565] wlan0: waiting for beacon from 00:23:51:0c:15:d1
[   27.939699] wlan0: associate with 00:23:51:0c:15:d1 (try 1/3)
[   27.942084] wlan0: RX AssocResp from 00:23:51:0c:15:d1 (capab=0x431 status=0 aid=2)
[   27.944438] wlan0: associated
[   27.944484] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

fabzil@fabzil-HP-EliteBook-2540p:~$ dmesg | grep "Network"
[    2.027905] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    2.201802] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[   21.444855] type=1400 audit(1401072828.009:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=425 comm="apparmor_parser"
[   21.445694] type=1400 audit(1401072828.009:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=425 comm="apparmor_parser"
[   21.448296] type=1400 audit(1401072828.013:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=424 comm="apparmor_parser"
[   21.449074] type=1400 audit(1401072828.013:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=424 comm="apparmor_parser"

fabzil@fabzil-HP-EliteBook-2540p:~$ dmesg | grep "Wire"
[   20.965688] Intel(R) Wireless WiFi driver for Linux, in-tree:

```


**6 ) Network configuration**
Code:
$ sudo lshw -C network
```
fabzil@fabzil-HP-EliteBook-2540p:~$ sudo lshw -C network
[sudo] password for fabzil: 
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: b4:99:ba:e4:e5:96
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.12-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d4700000-d471ffff memory:d472a000-d472afff ioport:5020(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:43:00.0
       logical name: wlan0
       version: 35
       serial: 18:3d:a2:19:70:74
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-24-generic firmware=9.221.4.1 build 25532 ip=192.168.1.77 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:d0500000-d0501fff

```

7 ) Scan for networks:
Code:
$ iwlist scan
```

fabzil@fabzil-HP-EliteBook-2540p:~$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:23:51:0C:15:D1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"GaneshaPosada"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bf1cad1f3
                    Extra: Last beacon: 11148ms ago
                    IE: Unknown: 000D47616E65736861506F73616461
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

**11 - Bonus from me**
Code:
$ rfkill list
```

fabzil@fabzil-HP-EliteBook-2540p:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


```


-3- Hadaka 
Here is the result of the command line. Keep in mind that now the wifi is working again
```

fabzil@fabzil-HP-EliteBook-2540p:~$ lspci -nnk | egrep '0200|0280'
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
43:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)

```



Thank you guys, together we can do this :)

---

### Post by Hadaka on 2014-05-26
Hi, please do..
COPY  and paste
```
echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
BOOT <- Must do
does that help it stay lit a little longer?
thanks.

---

### Post by Fabzil on 2014-05-26
Thank you Hadaka :)

Well tonight the net is working so I will try and do all the stuff I couldn't in the past 4 days but tomorrow morning I will defintly try your stuff
Could you please explain to me what it will do? It's been some time I stopped using Linux so I'm slowy going back to it ^^
It's like it will add a line in some file right?

---

### Post by Hadaka on 2014-05-26
hi, it disables the N speed which sometimes causes problems.
you can view that paramater with..
```
modinfo iwlwifi
```
and then research the options
be sure to boot after you enter the command.
thanks.

---


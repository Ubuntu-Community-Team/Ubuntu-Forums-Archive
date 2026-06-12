---
title: "Wireless connection has disappeared - again! Ubuntu 12.04 LTS on Advent T1600"
date: 2014-04-05
forum: Networking &amp; Wireless
---

### Post by T Bone on 2014-04-05
Hi all, 

My wireless connection has dropped off (for the third time in 12 months) this week. Last time I posted here 

[HTML]http://ubuntuforums.org/showthread.php?t=2203285[/HTML]

and found that running 13.04 off a USB boot stick brought it back to life, even when I reverted back to 12.04. I have no idea why that happened, but I was happy that it worked and just went with it.

Now it has happened again, and my ethernet has also failed, so I cannot access the net at all on that device. I'll not post the outputs again, as they are the same as on the original thread, unless it would help to have them all here?

Can anyone help or provide any ideas?

Thanks

---

### Post by mörgæs on 2014-04-06
13.04 is out of support. 
In stead of going further with this one I suggest a fresh install of 13.10. Remember to use wired internet access while installing.

---

### Post by T Bone on 2014-04-07
Thanks. I've tried 13.10 and no joy. I also tried running LinuxMint from a USB, just to see if there was some sort of compatibility error with newer versions of Ubuntu, but it didn't see any networks there, and went into the same cycle of repeatedly requesting authentication when I tried to "connect to a hidden wireless network". 

I will confess my poor technical knowledge, but logically if there is the same issue with Ubuntu and LinuxMint, would this suggest a hardware problem rather than software? Or do the two systems have enough of a crossover that the same problem could apply to both? I'm looking at buying a little USB wifi dongle to see if that solves the issues.

---

### Post by mörgæs on 2014-04-07
I wasn't expecting 13.10 to work wirelessly in first attempt. The idea was installing a stable and updated system which people with more knowledge than me could use for further troubleshooting.

Yes, a wifi dongle could be a good solution if everything else fails.

---

### Post by T Bone on 2014-04-08
Thanks. I hadn't been able to connect via ethernet previously, so I've run the 13.10 trial install again with it tethered to my mobile phone - but no change unfortunately. 

Are there any further things I should be trying? I've noticed lots of other networking problems which seem to be affecting people in the same way (cycling through requests for authentication) but they all seem to be very device-specific and I can't see any guides which I could try by myself without the assistance of someone much more knowledgable.

Thanks again, 

C

---

### Post by T Bone on 2014-04-12
Bought a TRENDnet N150 USB adapter based on other posts which indicated plug & play capability. Ubuntu is recognising it and I can select it to make an attempt to connect, but the same cycle of requiring authentication is happening! 

There isn't any issue with the router itself, as I have another laptop running 12.04 which connects without any issues, and all my other mobile devices are working (mobile phones and Android tablet). I can connect this laptop using my mobile telephone via USB tethering, but nothing seems to be working when I connect via Ubuntu itself. 

I am totally stumped, any help would be appreciated!

---

### Post by praseodym on 2014-04-12
Please show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
```
Does LAN work?

---

### Post by T Bone on 2014-04-12
Hello, and thanks...

No connection to the internet is available except via USB tethering. 

uname -a gives:

```
Linux chris-DIXONSXP 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:55:18 UTC 2014 i686 i686 i386 GNU/Linux 
```

lspci -nnk | grep -iA2 net gives:

```
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199]
    Kernel driver in use: r8180
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Elitegroup Computer Systems Device [1019:90b3]
    Kernel driver in use: r8169 
```

lsusb gives:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
Bus 002 Device 003: ID 0fce:71a7 Sony Ericsson Mobile Communications AB 
```

lsmod gives:

```
Module                  Size  Used by
rndis_host             13560  0 
cdc_ether              13312  1 rndis_host
usbnet                 25214  2 rndis_host,cdc_ether
pci_stub               12550  1 
vboxpci                22911  0 
vboxnetadp             25616  0 
vboxnetflt             27240  0 
vboxdrv               285013  3 vboxpci,vboxnetadp,vboxnetflt
joydev                 17393  0 
snd_hda_codec_hdmi     31823  1 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
r8712u                163880  0 
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                96744  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r8187se               157152  0 
eeprom_93cx6           12687  1 r8187se
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
bluetooth             158447  10 bnep,rfcomm
ppdev                  12849  0 
i915                  428282  4 
drm_kms_helper         45466  1 i915
drm                   197641  5 i915,drm_kms_helper
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
usb_storage            39646  1 ums_realtek
r8169                  56396  0 
```

ifconfig -a gives:

```
eth0      Link encap:Ethernet  HWaddr 00:03:0d:ba:b3:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x8000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88415 (88.4 KB)  TX bytes:88415 (88.4 KB)


usb0      Link encap:Ethernet  HWaddr 02:1b:1b:03:0c:7a  
          inet addr:192.168.42.234  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::1b:1bff:fe03:c7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2099306 (2.0 MB)  TX bytes:686881 (686.8 KB)


wlan0     Link encap:Ethernet  HWaddr 00:22:5f:48:2a:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f8458000-f8458100 


wlan1     Link encap:Ethernet  HWaddr d8:eb:97:22:89:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:152 errors:0 dropped:1 overruns:0 frame:0
          TX packets:68 errors:0 dropped:26 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23137 (23.1 KB)  TX bytes:10540 (10.5 KB) 
```

iwconfig gives:

```
lo        no wireless extensions.


usb0      no wireless extensions.


wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


eth0      no wireless extensions. 
```

cat /etc/resolv.conf gives:

```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
```

iwlist chan gives:

```
lo        no frequency information.


usb0      no frequency information.


wlan1     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Channel:3


eth0      no frequency information. 
```

sudo iwlist scan gives: 

```
lo        Interface doesn't support scanning.


usb0      Interface doesn't support scanning.


wlan1     Failed to read scan data : Invalid argument


wlan0     No scan results


eth0      Interface doesn't support scanning. 
```

C

---


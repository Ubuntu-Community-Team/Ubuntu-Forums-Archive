---
title: "PCMCIA Wifi Card Cannot Connect To Internet on Dell Latitude"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by johny why on 2011-08-27
Hi

Cannot get my pcmcia wifi card to work. 

Running Ubuntu 11.04 on a Dell Latitude laptop.

Notes below based on [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) 

I plugged in a linksys 802.11b card. But Not getting Internet. 

lshw shows the device. 

I saw both hostap and Orinoco listed, so I blacklisted Orinoco and rebooted in effort to let hostap driver take over, but no joy. I used blacklist.conf, because I could not find a file called blacklist without the conf extension. 

When I do lsmod, I see hostap listed. 

Iwconfig seems to detect the device. It does not say "not ready". 

iwlist scan says "no scan results."

The wireless icon in the panel has an exclamation, and in the dropdown, it says "wireless networks disconnected". 

Rfkill list returns nothing. 

Lshw does not say "disabled" or "radio off". 

I downloaded a Linux driver for my linksys PCMCIA card, but no idea how to make/install it.
[http://homesupport.cisco.com/en-us/support/adapters/WPC11](http://homesupport.cisco.com/en-us/support/adapters/WPC11)

When i run the following with the card unplugged--

	sudo tail -f /var/log/messages

--and then plug in the card, i get wlan1: link is not ready.

i tried pressing with wireless on/off button on my keyboard before and after plugging in the card, but does not help.

any suggestions?

please help!

---

### Post by wildmanne39 on 2011-08-27
Hi, I will try to help you, I know you ran several commands but I need you to run these and post all the results here so I can see them.
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by johny why on 2011-08-27
here are the results
```
admin@Latitude-C640:~$ sudo lshw -C network
[sudo] password for admin: 
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 78
       serial: 00:08:74:98:38:03
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:f9000000-f901ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:04:5a:cc:4e:e1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap firmware=0.8.0 multicast=yes wireless=IEEE 802.11b

-------------

admin@Latitude-C640:~$ lspci -nn | grep 0280
admin@Latitude-C640:~$ 

-------------

admin@Latitude-C640:~$ lsusb
Bus 001 Device 002: ID 05dc:a813 Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
admin@Latitude-C640:~$ 

-------------

admin@Latitude-C640:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-90 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:1350  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:85101   Missed beacon:0

admin@Latitude-C640:~$ 

---------------

admin@Latitude-C640:~$ rfkill list all
admin@Latitude-C640:~$ 

---------------

admin@Latitude-C640:~$ lsmod
Module                  Size  Used by
usb_storage            40172  1 
binfmt_misc             6599  1 
hostap_cs              47856  3 
hostap                100441  1 hostap_cs
lib80211                5058  2 hostap_cs,hostap
snd_intel8x0           25632  2 
radeon                828445  3 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
joydev                  8767  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 35973  1 hostap_cs
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
yenta_socket           21518  0 
snd                    49038  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi_aio            1733  0 
intel_agp              26694  1 
i2c_algo_bit            5168  1 radeon
dcdbas                  5402  0 
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                59033  0 
soundcore                880  1 snd
shpchp                 29886  0 
agpgart                32011  3 ttm,drm,intel_agp
ppdev                   5556  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
serio_raw               4022  0 
video                  18712  0 
parport_pc             26058  1 
output                  1883  1 video
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
3c59x                  32011  0 
floppy                 54311  0 
mii                     4425  1 3c59x
admin@Latitude-C640:~$ 



```

---

### Post by wildmanne39 on 2011-08-27
Hi run this commands please and post the results:
```
dmesg | grep wlan1
```
```
dmesg | grep wifi0
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
nm-tool
```
```
dmesg | grep hostap
```
```
lsmod | grep hostap
```
Thank you

---

### Post by chili555 on 2011-08-27
Wild Man will also like to see:```
sudo pccardctl ident
```

---

### Post by wildmanne39 on 2011-08-27
Thank you chili555.

---

### Post by johny why on 2011-08-27
```
admin@Latitude-C640:~$ dmesg | grep wlan1
[   19.235585] udev[320]: renamed network interface wlan0 to wlan1
[   19.260707] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   19.273295] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
admin@Latitude-C640:~$ 

admin@Latitude-C640:~$ dmesg | grep wifi0
[   18.750500] hostap_cs: Registered netdevice wifi0
[   19.004071] wifi0: NIC: id=0x8002 v1.0.0
[   19.004218] wifi0: PRI: id=0x15 v0.3.0
[   19.004361] wifi0: STA: id=0x1f v0.8.0
[   19.005379] wifi0: defaulting to bogus WDS frame as a workaround for firmware bug in Host AP mode WDS
[   19.009363] wifi0: registered netdevice wlan0
[   19.260519] ADDRCONF(NETDEV_UP): wifi0: link is not ready
[   19.273806] wifi0: LinkStatus=2 (Disconnected)
[   19.294905] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
admin@Latitude-C640:~$ 

admin@Latitude-C640:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wifi0     No scan results

wlan1     No scan results

admin@Latitude-C640:~$ 

admin@Latitude-C640:~$ iwlist chan
lo        no frequency information.

eth1      no frequency information.

wifi0     14 channels in total; available frequencies :
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
          Current Frequency:2.427 GHz (Channel 4)

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
          Current Frequency:2.427 GHz (Channel 4)

admin@Latitude-C640:~$ 


admin@Latitude-C640:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            3c59x
  State:             unavailable
  Default:           no
  HW Address:        00:08:74:98:38:03

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            hostap_cs
  State:             disconnected
  Default:           no
  HW Address:        00:04:5A:CC:4E:E1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

admin@Latitude-C640:~$ 


admin@Latitude-C640:~$ dmesg | grep hostap
[   18.749123] hostap_cs: setting Vcc=33 (constant)
[   18.750500] hostap_cs: Registered netdevice wifi0
[   18.790451] hostap_cs: index 0x01: , irq 3, io 0xe100-0xe13f
admin@Latitude-C640:~$ 


admin@Latitude-C640:~$ lsmod | grep hostap
hostap_cs              47856  3 
hostap                100441  1 hostap_cs
lib80211                5058  2 hostap_cs,hostap
pcmcia                 35973  1 hostap_cs
admin@Latitude-C640:~$ 


admin@Latitude-C640:~$ sudo pccardctl ident
Socket 0:
  no product info available
Socket 1:
  product info: "Instant Wireless ", " Network PC CARD", "Version 01.02", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)



```

---

### Post by wildmanne39 on 2011-08-27
Hi, please turn off encryption and see if you can connect, also you need to unplug your wired connection then restart your computer.
Thank you

---

### Post by johny why on 2011-08-27
> **wildmanne39 said:**
>  turn off encryption 

how?

---

### Post by wildmanne39 on 2011-08-27
Hi, enter this into your web broswer 192.168.0.1 with the wired connection connected and see if that takes you to your routers configuratiuon page, then look for security settings under wireless.

---

### Post by johny why on 2011-08-27
But I do not have a wired connection.

---

### Post by wildmanne39 on 2011-08-28
Hi, how did you setup your router?

---

### Post by johny why on 2011-08-28
At the moment, trying to connect at public wifi. At home,  with another computer.

---

### Post by wildmanne39 on 2011-08-28
Hi, I am not sure that your card is capable of connecting to a router that is using wep/wpa/wpa2 like the one in your post.

We need to try to get it working at your house first where you can change your encryption settings to see if that is the problem.

---


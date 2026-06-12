---
title: "wifi ralink rt5370 usb connected but cant browse"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by jhay2 on 2013-09-15
hello im here again ..

heres my  problem im using ralink rt5370 wifi usb .. 

when im using the generic rt2800usb it works fine but very slow internet 
so id decided to install the drivers of my usb wifi .

when i already installed the driver . and try to connect 

wifi Connected but i cant browse and cant ping as well

No data received in browse .. 

and Host unreachable when pinging any website 



is there anyone here can help me to this problem .. 

im using ubuntu 13.04 with lxde desktop 
:(

---

### Post by jhay2 on 2013-09-15
please help :'(

---

### Post by praseodym on 2013-09-15
Please show
```

lsusb
lsmod
iwconfig
ifconfig -a
route -n
cat /etc/resolv.conf
```

---

### Post by jhay2 on 2013-09-15
> **praseodym said:**
> Please show
```

lsusb
lsmod
iwconfig
ifconfig -a
route -n
cat /etc/resolv.conf
```

thanks for reply sir .. 


heres what ive got

> 
jhay@xfirebase:~$ lsusb
Bus 001 Device 011: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 002 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

jhay@xfirebase:~$ lsmod
Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27261  0 
vboxdrv               285137  3 vboxnetadp,vboxnetflt,vboxpci
rndis_host             13567  0 
cdc_ether              13245  1 rndis_host
usbnet                 26567  2 rndis_host,cdc_ether
usb_storage            47684  0 
dm_crypt               22321  1 
zram                   18071  1 
joydev                 17097  0 
ppdev                  12817  0 
rt5370sta             730493  1 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
snd_intel8x0           33096  2 
microcode              18286  0 
snd_ac97_codec        105692  1 snd_intel8x0
ac97_bus               12670  1 snd_ac97_codec
pcmcia                 39544  0 
psmouse                81038  0 
snd_pcm                80890  2 snd_ac97_codec,snd_intel8x0
serio_raw              13031  0 
binfmt_misc            17260  1 
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
irda                  107316  0 
snd_seq_midi           13132  0 
crc_ccitt              12627  1 irda
parport_pc             27504  1 
snd_seq_midi_event     14475  1 snd_seq_midi
yenta_socket           27095  0 
snd_rawmidi            25114  1 snd_seq_midi
pcmcia_rsrc            18191  1 yenta_socket
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
mac_hid                13037  0 
snd                    56485  11 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
lpc_ich                16925  0 
shpchp                 32129  0 
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
radeon                870822  2 
i2c_algo_bit           13197  1 radeon
ttm                    71289  1 radeon
drm_kms_helper         47545  1 radeon
drm                   228750  4 ttm,drm_kms_helper,radeon
e100                   35903  0 
floppy                 55441  0 


jhay@xfirebase:~$ iwconfig
ra0       Ralink STA  ESSID:"mendoza"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.417 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

jhay@xfirebase:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:a5:be:05:d7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:603807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:603807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47103206 (47.1 MB)  TX bytes:47103206 (47.1 MB)

ra0       Link encap:Ethernet  HWaddr 78:44:76:aa:9e:af  
          inet addr:192.168.254.100  Bcast:192.168.254.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51480 (51.4 KB)  TX bytes:38708 (38.7 KB)




jhay@xfirebase:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.254.254 0.0.0.0         UG    0      0        0 ra0
192.168.254.0   0.0.0.0         255.255.255.0   U     9      0        0 ra0



jhay@xfirebase:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1



---

### Post by praseodym on 2013-09-15
Try pure WPA2-AES encryption (router manual) and set the bandwidth to 20 MHz instead of 20/40MHz

---

### Post by jhay2 on 2013-09-15
> **praseodym said:**
> Try pure WPA2-AES encryption (router manual) and set the bandwidth to 20 MHz instead of 20/40MHz


my router was already set in pure wpa2 with aes encryption .. so i only change the bandwidth from 20/40 i set in to 20 ..


and saveit.. andthen i try to connect .. but no luck it doesnt connect to router :(

---

### Post by praseodym on 2013-09-15
Check the above commands after using rt2800usb

---

### Post by jhay2 on 2013-09-15
> **praseodym said:**
> Check the above commands after using rt2800usb


what do you mean sir ?? 

i already list rt2800usb in my blacklist.. i am using rt5370sta now .

---

### Post by praseodym on 2013-09-15
That doesnt matter. By hand:
```

sudo modprobe -rfv rt5370sta
sudo modprobe -v rt2800usb nohwcrypt=1
```
re-plug the stick

---

### Post by kurt18947 on 2013-09-16
My generic RT5370 device works using the RT2800usb driver on Ubuntu 13.10.  The connection is stable but speeds indicated in  iwconfig are modest, typically 28mb./sec. to 72 mb./sec. depending on location and machine.

---

### Post by praseodym on 2013-09-16
Try

```
sudo iwconfig wlan0 rate auto
```
or
```
sudo iwconfig wlan0 rate 130M
```
Check with
```
iwconfig
```

---

### Post by jhay2 on 2013-09-17
> **praseodym said:**
> That doesnt matter. By hand:
```

sudo modprobe -rfv rt5370sta
sudo modprobe -v rt2800usb nohwcrypt=1
```
re-plug the stick

heres what ive got ..

Dont confuse with route -n , because when im using rt2800usb it doesnt connect to router directly . and i dont know why so im using wireless hotspot using my android phone. 


but when i switched to ra0 which is my wireless driver it connects to router but no browse and cant ping .. 


so please dont be confused to my gateway ip .. 


jhay@xfirebase:~$ lsusb
Bus 001 Device 017: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 002 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


jhay@xfirebase:~$ lsmod
Module                  Size  Used by
arc4                   12543  2 
rt2800usb              22366  0 
rt2x00usb              19979  1 rt2800usb
rt2800lib              60947  1 rt2800usb
rt2x00lib              48522  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              526519  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              436177  2 mac80211,rt2x00lib
rndis_host             13567  0 
cdc_ether              13245  1 rndis_host
usbnet                 26567  2 rndis_host,cdc_ether
usb_storage            47684  0 
dm_crypt               22321  1 
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               285210  3 vboxnetadp,vboxnetflt,vboxpci
zram                   18071  1 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
ppdev                  12817  0 
joydev                 17097  0 
binfmt_misc            17260  1 
microcode              18286  0 
snd_intel8x0           33096  2 
snd_ac97_codec        105692  1 snd_intel8x0
ac97_bus               12670  1 snd_ac97_codec
irda                  107316  0 
crc_ccitt              12627  2 irda,rt2800lib
parport_pc             27504  1 
snd_pcm                80890  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
pcmcia                 39544  0 
mac_hid                13037  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
yenta_socket           27095  0 
pcmcia_rsrc            18191  1 yenta_socket
snd_timer              24411  2 snd_pcm,snd_seq
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
snd                    56485  11 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
psmouse                81038  0 
lpc_ich                16925  0 
lp                     13299  0 
soundcore              12600  1 snd
serio_raw              13031  0 
parport                40753  3 lp,ppdev,parport_pc
shpchp                 32129  0 
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
radeon                870822  2 
i2c_algo_bit           13197  1 radeon
ttm                    71289  1 radeon
floppy                 55441  0 
drm_kms_helper         47545  1 radeon
e100                   35903  0 
drm                   228750  4 ttm,drm_kms_helper,radeon

jhay@xfirebase:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"jhay"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 02:08:22:16:68:DB   
          Bit Rate=28.9 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:28   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

jhay@xfirebase:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"jhay"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 02:08:22:16:68:DB   
          Bit Rate=28.9 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:28   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

jhay@xfirebase:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:a5:be:05:d7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31459 (31.4 KB)  TX bytes:31459 (31.4 KB)

wlan0     Link encap:Ethernet  HWaddr 78:44:76:aa:9e:af  
          inet addr:192.168.43.146  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::7a44:76ff:feaa:9eaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58686 (58.6 KB)  TX bytes:47748 (47.7 KB)

jhay@xfirebase:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 wlan0
192.168.43.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0


jhay@xfirebase:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

---

### Post by praseodym on 2013-09-17
Deactivate the power management:
```

sudo iwconfig wlan0 power off
```

---

### Post by jhay2 on 2013-09-18
> **praseodym said:**
> Deactivate the power management:
```

sudo iwconfig wlan0 power off
```

i've done with that sir.. but i'd noticed a difference between the generic driver and ra0 


when im using generic driver the signal always in weak even i am 1 meter away from my router ..

so that gives me a decision to change my driver into rt5370sta and this give me a very strong signal 

but it cant ping and browse the net .. 

Is there any chance sir that i can use my rt5370sta driver to browse the internet ? :(

---

### Post by praseodym on 2013-09-18
Maybe I am repeating myself, but check the following:

[LIST]
[*]Router firmware is up-to-date?
[*]MAC-address filter in your router is turned off?
[*]Channel fixed, e.g. to "1"?
[*]Bandwidth set to 20MHz?
[*]IPv6-settings in the network-manager set to "Ignore"?
[/LIST]

---

### Post by jhay2 on 2013-09-19
thanks for your help sir .. i really appreciate it .. i think it is working now .. i change my router setting from 802.11b/g/nb into 802.11 b and it is working now .. but i dont know the reason behind that .. but thanks for you help.. 


but sir one more thing i want to ask this ..my laptop has defect keyboard .. my windows key has a defect function .. my laptop detcts that this key is always run even i am not clicking it.. i knew it because when i click only "r" the run prompt of lubuntu-desktop appear.. and that is because the laptop detect windows key was clicked without clicking it ..

iwant to disable it .. how can i do that in lubuntu-desktop ? 

sorry for my very bad english .. i cant explain it very well b.. i hope you can understand it :)

---

### Post by praseodym on 2013-09-19
Check the keyboard layout and try another one, not "detect automatically"

---

### Post by jhay2 on 2013-09-19
> **praseodym said:**
> Check the keyboard layout and try another one, not "detect automatically"

how can i do that sir ? im using lubuntu-desktop (lxde)

---

### Post by praseodym on 2013-09-19
Check: Settings-> Keyboard&Mouse

---


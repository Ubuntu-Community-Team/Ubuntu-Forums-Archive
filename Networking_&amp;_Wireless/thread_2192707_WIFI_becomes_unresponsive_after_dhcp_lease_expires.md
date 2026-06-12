---
title: "WIFI becomes unresponsive after dhcp lease expires"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by chrisbmo2000 on 2013-12-09
As the title says once the lease expires the laptop has no inet. If you disconnect and try to reconnect it will prompt you for the wifi password but it never auths.
Here are the commands I ran both while wifi was working and while it was not: lsmod, cat /etc/resolv.conf, and sudo iwlist scan.

Here are the results of those commands while wifi IS working:
```

cbarron@cbarron-worklaptop:~$ lsmod
Module                  Size  Used by
arc4                   12509  2 
lib80211_crypt_wep     12746  1 
pci_stub               12550  1 
vboxpci                22910  0 
vboxnetadp             13328  0 
vboxnetflt             27240  0 
vboxdrv               252210  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17852  2 
rfcomm                 38400  12 
parport_pc             27612  0 
ppdev                  12849  0 
nvidia              10287220  52 
snd_intel8x0           33458  2 
snd_ac97_codec        110254  1 snd_intel8x0
ac97_bus               12670  1 snd_ac97_codec
ipw2200               142022  0 
snd_pcm                85934  2 snd_intel8x0,snd_ac97_codec
hid_generic            12484  0 
snd_seq_midi           13132  0 
libipw                 33469  1 ipw2200
btusb                  17951  0 
snd_rawmidi            25157  1 snd_seq_midi
bluetooth             211552  24 bnep,rfcomm,btusb
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
joydev                 17329  0 
usbhid                 46125  0 
snd_timer              28931  2 snd_pcm,snd_seq
hid                    87362  2 hid_generic,usbhid
cfg80211              453919  2 ipw2200,libipw                                                                                                                                                                                                                                 
dell_laptop            17209  0                                                                                                                                                                                                                                                
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq                                                                                                                                                                                                               
dm_multipath           22754  0                                                                                                                                                                                                                                                
snd                    57014  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device                                                                                                                                                              
soundcore              12600  1 snd                                                                                                                                                                                                                                            
lib80211               14040  3 lib80211_crypt_wep,ipw2200,libipw                                                                                                                                                                                                              
microcode              18433  0                                                                                                                                                                                                                                                
dcdbas                 14065  1 dell_laptop                                                                                                                                                                                                                                    
scsi_dh                14418  1 dm_multipath                                                                                                                                                                                                                                   
gpio_ich               13278  0                                                                                                                                                                                                                                                
pcmcia                 39854  0                                                                                                                                                                                                                                                
snd_page_alloc         18398  2 snd_intel8x0,snd_pcm                                                                                                                                                                                                                           
psmouse                82769  0                                                                                                                                                                                                                                                
lpc_ich                17048  0                                                                                                                                                                                                                                                
yenta_socket           27427  0                                                                                                                                                                                                                                                
mac_hid                13077  0                                                                                                                                                                                                                                                
serio_raw              13031  0                                                                                                                                                                                                                                                
pcmcia_rsrc            18367  1 yenta_socket                                                                                                                                                                                                                                   
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc                                                                                                                                                                                                                
video                  19116  0                                                                                                                                                                                                                                                
usbserial              27633  0                                                                                                                                                                                                                                                
lp                     17455  0                                                                                                                                                                                                                                                
parport                40930  3 parport_pc,ppdev,lp                                                                                                                                                                                                                            
firewire_ohci          35914  0                                                                                                                                                                                                                                                
b44                    31223  0                                                                                                                                                                                                                                                
ssb                    51554  1 b44                                                                                                                                                                                                                                            
firewire_core          62086  1 firewire_ohci                                                                                                                                                                                                                                  
crc_itu_t              12627  1 firewire_core                                                                                                                                                                                                                                  
sdhci_pci              18265  0                                                                                                                                                                                                                                                
sdhci                  32339  1 sdhci_pci                                                                                                                                                                                                                                      
cbarron@cbarron-worklaptop:~$ iwconfig                                                                                                                                                                                                                                         
lo        no wireless extensions.                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                                               
eth0      no wireless extensions.                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                                               
eth1      IEEE 802.11bg  ESSID:"BarronHome"                                                                                                                                                                                                                                    
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:AF:A3:05                                                                                                                                                                                                   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0                                                                                                                                                                                                                 
          Retry limit:7   RTS thr: off   Fragment thr: off                                                                                                                                                                                                                       
          Power Management: off                                                                                                                                                                                                                                                 
          Link Quality=84/100  Signal level=-44 dBm  Noise level=-85 dBm                                                                                                                                                                                                       
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0                                                                                                                                                                                                             
          Tx excessive retries:0  Invalid misc:0   Missed beacon:23


cbarron@cbarron-worklaptop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
cbarron@cbarron-worklaptop:~$ sudo iwlist scan
[sudo] password for cbarron: 
lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


eth1      Scan completed :
          Cell 01 - Address: 00:1C:10:AF:A3:05
                    ESSID:"BarronHome"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=44/100  Signal level=-47 dBm  
                    Extra: Last beacon: 28ms ago
          Cell 02 - Address: 40:8B:07:72:45:35
                    ESSID:"2WIRE317"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=44/100  Signal level=-74 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 20ms ago
          Cell 03 - Address: 1C:AF:F7: DA:26:C3
                    ESSID:"BarronHome"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-37 dBm  
                    Extra: Last beacon: 68ms ago
          Cell 04 - Address: 00:23:97:BB:FE:5A
                    ESSID:"CenturyLink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=79/100  Signal level=-50 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 88ms ago

```

And now the results of the commands while wifi IS NOT working:
```

cbarron@cbarron-worklaptop:~$ lsmod
Module                  Size  Used by
arc4                   12509  2 
lib80211_crypt_wep     12746  1 
pci_stub               12550  1 
vboxpci                22910  0 
vboxnetadp             13328  0 
vboxnetflt             27240  0 
vboxdrv               252210  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17852  2 
rfcomm                 38400  12 
parport_pc             27612  0 
ppdev                  12849  0 
nvidia              10287220  52 
snd_intel8x0           33458  2 
snd_ac97_codec        110254  1 snd_intel8x0
ac97_bus               12670  1 snd_ac97_codec
ipw2200               142022  0 
snd_pcm                85934  2 snd_intel8x0,snd_ac97_codec
hid_generic            12484  0 
snd_seq_midi           13132  0 
libipw                 33469  1 ipw2200
btusb                  17951  0 
snd_rawmidi            25157  1 snd_seq_midi
bluetooth             211552  24 bnep,rfcomm,btusb
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
joydev                 17329  0 
usbhid                 46125  0 
snd_timer              28931  2 snd_pcm,snd_seq
hid                    87362  2 hid_generic,usbhid
cfg80211              453919  2 ipw2200,libipw
dell_laptop            17209  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
dm_multipath           22754  0 
snd                    57014  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
lib80211               14040  3 lib80211_crypt_wep,ipw2200,libipw
microcode              18433  0 
dcdbas                 14065  1 dell_laptop
scsi_dh                14418  1 dm_multipath
gpio_ich               13278  0 
pcmcia                 39854  0 
snd_page_alloc         18398  2 snd_intel8x0,snd_pcm
psmouse                82769  0 
lpc_ich                17048  0 
yenta_socket           27427  0 
mac_hid                13077  0 
serio_raw              13031  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  19116  0 
usbserial              27633  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35914  0 
b44                    31223  0 
ssb                    51554  1 b44
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18265  0 
sdhci                  32339  1 sdhci_pci
cbarron@cbarron-worklaptop:~$ sudo iwlist scan
[sudo] password for cbarron: 
lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


eth1      Scan completed :
          Cell 01 - Address: A0:B3:CC: D3:ED:10
                    ESSID:"HP-Print-10-Photosmart 5520"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    Extra: Last beacon: 1096ms ago
          Cell 02 - Address: 0C:EE:E6:21:3A: DD
                    ESSID:"home"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-79 dBm  
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 236ms ago
          Cell 03 - Address: 00:1C:10:AF:A3:05
                    ESSID:"BarronHome"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-52 dBm  
                    Extra: Last beacon: 36ms ago
          Cell 04 - Address: 28:C6:8E:02:97: D7
                    ESSID:"NETGEAR49"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 56ms ago
          Cell 05 - Address: CC:7D:37:EC:19:99
                    ESSID:"MOTOROLA-32EE8"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 768ms ago
          Cell 06 - Address: 40:8B:07:72:45:35
                    ESSID:"2WIRE317"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=41/100  Signal level=-76 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 11208ms ago
          Cell 07 - Address: 1C:AF:F7: DA:26:C3
                    ESSID:"BarronHome"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-40 dBm  
                    Extra: Last beacon: 0ms ago
          Cell 08 - Address: 00:23:97:BB:FE:5A
                    ESSID:"CenturyLink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 40ms ago
          Cell 09 - Address: 84:1B:5E:E5:E2:5E
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=50/100  Signal level=-71 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 780ms ago
          Cell 10 - Address: 58:6D:8F:C4:39:7E
                    ESSID:"Charmed"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=41/100  Signal level=-76 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 240ms ago
          Cell 11 - Address: 28:C6:8E:6D: DF:E4
                    ESSID:"NETGEAR13"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=58/100  Signal level=-66 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 224ms ago
          Cell 12 - Address: 4C:60: DE:E6:57:C1
                    ESSID:"NETGEAR59"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key : on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 188ms ago
          Cell 13 - Address: 3C:75:4A:68:C0:81
                    ESSID:"Wireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key 0 :n
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 11436ms ago

```

```

cbarron@cbarron-worklaptop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
cbarron@cbarron-worklaptop:~$ 

```

Any Ideas?

---

### Post by chrisbmo2000 on 2013-12-10
ANY Ideas?  ANYONE?

---

### Post by 7182818 on 2013-12-10
The contents /etc/resolv.conf seem weird to me in both cases:  In the first one, why would your nameserver be at 127.0.0.1?  Are you running a nameserver on your machine?  In the second one, it's just weird because there is nothing there.

As a test, can you add the line 'nameserver 8.8.8.8' to the file and see if you can then ping [www.google.com](www.google.com)

Also, can you provide the output of ifconfig for both cases?

---

### Post by steeldriver on 2013-12-10
A nameserver of 127.0.0.1 in /etc/resolv.conf is normal for 12.04+ desktop systems (which run dnsmasq as a caching DNS server) - but having en empty /etc/resolv.conf will be a problem (although may be a symptom rather than a cause)

I agree posting ifconfig might be helpful - also PLEASE post the outputs in ```
 tags, probably one reason you are getting so little response is it's very hard to read otherwise.

It would also be useful to post what wireless card you have - you can use

[CODE]sudo lshw -C network
```

It would also be a good idea to check for error messages related to the interface in the dmesg log

```
dmesg | grep eth1
```

The one thing I noticed was you appear to have 2 access points (2 cells in the iwlist) with the same SSID - that can cause problems, you might want to try choosing the strongest one and fixing to it by setting the BSSID field equal to its MAC

---

### Post by chrisbmo2000 on 2013-12-10
Thanks for the replies.
The 2 AP's are are set on diffrent channels and are at diffrent sides of the house so I can move freely through the house and not have to reconnect at any point. That is probably not the issue, however I agree that the resolv.conf having loopback or blank IS an issue. Just not sure where the issue lies. I can tell you that this is related to Ubuntu only. I dont have this issue when I boot into Windows (bad word I know) ( yes this is a dual boot machine)
the output of sudo lshw -C network is:

```
  *-network:0                    description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:e4:f3:85
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:18 memory:dcffe000-dcffffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:15:00:1b:73:cd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=10.10.2.8 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dcffd000-dcffdfff
```

The output of dmesg | grep eth1

```
 cbarron@cbarron-worklaptop:~$ sudo dmesg | grep eth0[    1.560730] b44 ssb0:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:12:3f:e4:f3:85
[    6.177196] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.309694] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.310129] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
cbarron@cbarron-worklaptop:~$                                       ]

```

more ideas?

(I also edited the original post to make it easier to read)

---

### Post by steeldriver on 2013-12-10
... looks like you grepped the wrong interface (eth0 not eth1) - can you try again with eth1 (the wireless interface) please?

Why do you think roaming between APs is probably not the issue?

---

### Post by chrisbmo2000 on 2013-12-11
```

cbarron@cbarron-worklaptop:~$ sudo dmesg | grep eth1
cbarron@cbarron-worklaptop:~$ 

```

That is what a grep of eth1 does...Nothing...lol

As far as roaming between AP's is concerned, here is how it is set up
AP1 has dhcp enabled
AP2 is set to forward dhcp requests to AP1
So basically there is no "real" AP2 it is just a radio extension. Plus like I said in a previous post, this only happens in Ubuntu. When I boot into Windows, things are just fine between AP's, no disconnects or failures.
(Both AP's are running DD-WRT if that is any help as well)

Its probably something simple that I am missing.

UPDATE.............
I unplugged AP2 just to test and see if the issue still exists.....and it does. The times seem to be random as to when it fails, but it still does.

More Ideas?

---

### Post by steeldriver on 2013-12-11
Maybe the relevant log info got rotated out - you could try looking further back e.g.

```

grep 'eth1' /var/log/dmesg.0

zgrep 'eth1' /var/log/dmesg.?.gz

```

If authentication is failing, there should be stuff like

```

eth1: authenticate with xx:xx:xx:xx:xx:xx (try 1)
eth1: authenticate with xx:xx:xx:xx:xx:xx (try 2)
eth1: authenticate with xx:xx:xx:xx:xx:xx (try 3)
.
.
.

```

and there *may* be other info giving clues as to why

---

### Post by chrisbmo2000 on 2013-12-11
```

cbarron@cbarron-worklaptop:~$ sudo zgrep 'eth1' /var/log/dmesg.?.gz
cbarron@cbarron-worklaptop:~$ sudo grep 'eth1' /var/log/dmesg.0
cbarron@cbarron-worklaptop:~$ 

```

Looks like the grep issue is an issue as well. I am going to start manually digging in the logs.

---

### Post by chrisbmo2000 on 2013-12-11
```

Dec 11 16:51:49 cbarron-worklaptop NetworkManager[980]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 11 16:51:49 cbarron-worklaptop avahi-daemon[931]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::215:ff:fe1b:73cd.
Dec 11 16:51:49 cbarron-worklaptop avahi-daemon[931]: New relevant interface eth1.IPv6 for mDNS.
Dec 11 16:51:49 cbarron-worklaptop avahi-daemon[931]: Registering new address record for fe80::215:ff:fe1b:73cd on eth1.*.
Dec 11 16:51:49 cbarron-worklaptop NetworkManager[980]: <info> Activation (eth1) Beginning IP6 addrconf.
Dec 11 16:51:49 cbarron-worklaptop avahi-daemon[931]: Withdrawing address record for fe80::215:ff:fe1b:73cd on eth1.
Dec 11 16:51:49 cbarron-worklaptop avahi-daemon[931]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::215:ff:fe1b:73cd.
Dec 11 16:51:49 cbarron-worklaptop avahi-daemon[931]: Interface eth1.IPv6 no longer relevant for mDNS.
Dec 11 16:51:49 cbarron-worklaptop NetworkManager[980]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Dec 11 16:51:50 cbarron-worklaptop dhclient: Listening on LPF/eth1/00:15:00:1b:73:cd
Dec 11 16:51:50 cbarron-worklaptop NetworkManager[980]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Dec 11 16:51:50 cbarron-worklaptop dhclient: Sending on   LPF/eth1/00:15:00:1b:73:cd
Dec 11 16:51:50 cbarron-worklaptop dhclient: DHCPREQUEST of 10.10.2.8 on eth1 to 255.255.255.255 port 67
Dec 11 16:51:50 cbarron-worklaptop NetworkManager[980]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Dec 11 16:51:50 cbarron-worklaptop NetworkManager[980]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 11 16:51:50 cbarron-worklaptop NetworkManager[980]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Dec 11 16:51:50 cbarron-worklaptop avahi-daemon[931]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.10.2.8.
Dec 11 16:51:50 cbarron-worklaptop avahi-daemon[931]: New relevant interface eth1.IPv4 for mDNS.
Dec 11 16:51:50 cbarron-worklaptop avahi-daemon[931]: Registering new address record for 10.10.2.8 on eth1.IPv4.
Dec 11 16:51:51 cbarron-worklaptop avahi-daemon[931]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::215:ff:fe1b:73cd.
Dec 11 16:51:51 cbarron-worklaptop avahi-daemon[931]: New relevant interface eth1.IPv6 for mDNS.
Dec 11 16:51:51 cbarron-worklaptop avahi-daemon[931]: Registering new address record for fe80::215:ff:fe1b:73cd on eth1.*.
Dec 11 16:51:51 cbarron-worklaptop NetworkManager[980]: <info> (eth1): removing resolv.conf from /sbin/resolvconf

```

I see several things "wrong" here. Correct me if Im wrong but ```
 Dec 11 16:51:51 cbarron-worklaptop NetworkManager[980]: <info> (eth1): removing resolv.conf from /sbin/resolvconf
```  is not good. And why is ```
 Dec 11 16:51:50 cbarron-worklaptop dhclient: DHCPREQUEST of 10.10.2.8 on eth1 to 255.255.255.255 port 67
```...happening, the subnet on the network is 255.255.255.0.

This came from the current syslog. dmesg just doesnt have anything about eth1.

More Ideas?

---

### Post by steeldriver on 2013-12-11
Well having an empty /etc/resolv.conf is certainly a problem, messages about removing / writing the file are normal I think. If the underlying wireless connection is failing to associate / authenticate then that would be the thing to fix first - what exactly are your symptoms?
 

[LIST]
[*]Can you see a valid IPv4 address for the interface using ifconfig?
[*]Can you ping the gateway device (router) by IP address?
[*]Can you ping external hosts by IP address (e.g. Google DNS 8.8.8.8)
[*]Can you ping external hosts by name?
[/LIST]

If you are not actually using IPv6 I would disable it at least for now (edit the connection from the network manager applet, and set the Method to 'Ignore' in the IPv6 tab)

I'm no expert but the DHCPREQUEST looks fine to me (DHCP is a broadcast protocol, so it goes to 255.255.255.255 and waits for a server to respond)

---

### Post by chrisbmo2000 on 2013-12-11
> **steeldriver said:**
> Well having an empty /etc/resolv.conf is certainly a problem, messages about removing / writing the file are normal I think. If the underlying wireless connection is failing to associate / authenticate then that would be the thing to fix first - what exactly are your symptoms?
 

[LIST]
[*]Can you see a valid IPv4 address for the interface using ifconfig?
[*]Can you ping the gateway device (router) by IP address?
[*]Can you ping external hosts by IP address (e.g. Google DNS 8.8.8.8)
[*]Can you ping external hosts by name?
[/LIST]

If you are not actually using IPv6 I would disable it at least for now (edit the connection from the network manager applet, and set the Method to 'Ignore' in the IPv6 tab)

I'm no expert but the DHCPREQUEST looks fine to me (DHCP is a broadcast protocol, so it goes to 255.255.255.255 and waits for a server to respond)

Ok so, here is how this goes:
Power on laptop
Choose Ubuntu from Grub
Log in to Ubuntu
Open Browser and surf for a while
Then one of 2 senarios happens,
Senario 1
Surf just fine until I leave the laptop idle
Then when I come back to the laptop I still show I am connected to the wifi
I can ping ANYTHING local but can not go beyond the LAN
Disconnect from wifi and try to reconnect
association fails, the only way to make it reconnect is to reboot the machine and everything starts over
I even tried to restart networking in the CLI

Senario 2
Power on laptop
Choose Ubuntu from Grub
Log in to Ubuntu
Open Browser and surf for a while
then out of the blue I can not surf
I can ping ANYTHING local but can not go beyond the LAN
Disconnect from wifi and try to reconnect
association fails, the only way to make it reconnect is to reboot the machine and everything starts over

I have a conky desk top running so I can see my LAN and WAN IP
when I get a "no surf" condition
conky does not report a wan ip.

A valid ipv4 address is present at all times.

> 
I'm no expert but the DHCPREQUEST looks fine to me (DHCP is a broadcast protocol, so it goes to 255.255.255.255 and waits for a server to respond)

DUH...LOL I knew that and remembered as soon as I read it :)

---


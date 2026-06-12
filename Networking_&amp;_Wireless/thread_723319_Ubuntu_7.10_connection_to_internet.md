---
title: "Ubuntu 7.10 connection to internet"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by acad1 on 2008-03-13
What do I have to do to get a connection using 7.10 please.

Using Ubuntu 7.10 - no connection to internet

andy@andy-desktop:~$ sudo iwconfig
[sudo] password for andy:
Sorry, try again.
[sudo] password for andy:
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"G604T-WIRELESS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:72:75:A8   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:66DA-3A39-17E7-609E-E14C-14A3-B2
          Link Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

andy@andy-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:5B:D1:DB:0B
                    ESSID:"BT Fusion-2561"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz
                    Signal level=-86 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000053d76a6181U]Using Ubuntu 7.10 - no connection to internet
[/U]

andy@andy-desktop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: ATM network controller
       product: AccessRunner PCI ADSL Interface Device
       vendor: Conexant
       physical id: 2.1
       bus info: pci@0000:01:02.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:46:63:1e:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.3 multicast=yes wireless=IEEE 802.11g
andy@andy-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wireless-key **************************  (This is a WEP Key which I have removed)
wireless-essid G604T-WIRELESS

auto wlan0
andy@andy-desktop:~$


I also have Ubuntu 7.04 installed on the same computer, and have no problem to connect to the internet using the same computer, and Wireless USB D-Link DWL  G122 Rev B, although this is identified as rausb1 in 7.04

Has anyone managed to get this to work with 7.10?
Any help would be appreciated. Thanks

---


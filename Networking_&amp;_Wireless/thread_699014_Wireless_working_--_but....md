---
title: "Wireless working -- but..."
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by Allus on 2008-02-16
Just got Gutsy working on this computer a couple of days ago and was amazed at how well it interfaced with my hardware setup.

Now, I have the broadcom wireless internally in this computer, but in the past I was never able to get it working with my wireless network downstairs.  The connection was too intermittent.  But I have a Linksys wireless adapter I'd used for another computer so I have that stuck in the PCMCIA slot.

Well, I was unable to connect to the web but used another computer to download the fwcutter-i386.deb pkg and the wl_apsta firmware.  With the help of the wonderful tutorial at:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm-43xxx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm-43xxx/Gutsy)

       I was able to connect to a neighbor's unsecured network. So, now the job was to configure my own wireless again, (It had been sitting fallow for over 3 years).  So I was on Linksys forums all day and finally got to where I could connect to my own network with amazing connectivity and speed.  

But... here is my problem.

I figured that it was the Broadcom device connecting and so I pulled the Linksys adapter out of the computer. Bam!  I lost connectivity and the ability to see the networks available.   So, I rebooted with the card back in and I got my connectivity back along with a the list of available networks.  So, I figured it was the Linksys card doing all the work. So, I disabled the restricted drivers and rebooted. No connectivity and no list of available networks!   Nor was I able to just re-enable the driver.  I had to re-install the packages all over again. 

So, here I am with wonderful connectivity and speed, but I really don't understand why I need both cards.  This makes me way too resistant to tinker with the system anymore, but I have to because my network is unsecured -- Anybody can log on and leech from me.

Can anyone offer an explanation as to what is going on?

Thanks.

---

### Post by jan quark on 2008-02-18
hmm weird

run these terminal commands and post the output to shed some light on your network status

```

iwconfig
```
```

ifconfig
```

```
sudo iwlist scan
```
```

lshw -C network
```

```
cat /etc/network/interfaces
```

---

### Post by Allus on 2008-02-18
Hello there.  I ran all those commands and pasted the results in a forum post, but I get errors when I try to post it.  Something about how I have too many images in the messages.  It says I'm using 20 images.   I'm not using any, so I don't know how to correct the message to post it.

---

### Post by Allus on 2008-02-19
Hi again.  I thought I'd post the results one command at a time to see if they get through that way:

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Pablo"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0C:41:77:7D:36   
          Bit Rate=24 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=68/100  Signal level=-53 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:9  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth2      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Allus on 2008-02-19
Okay, now it's a bit easier to see what is happening.   Each little face is actually a colon followed by the lower case letter 'o'.  :o  is ":o"

Since HTML code is off I don't know what I can do about that.:confused:

Here is the next command:

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:02:3F:6C:2C:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x2800 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:4D:BD:99  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe4d:bd99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3290 errors:0 dropped:41 overruns:0 frame:0
          TX packets:3271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2920023 (2.7 MB)  TX bytes:396360 (387.0 KB)
          Interrupt:5 

eth2      Link encap:Ethernet  HWaddr 00:0C:41:2E:83:EC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:268 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:7392 (7.2 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Allus on 2008-02-19
The results from this command generate 15 images.  I'm sure this is cause by characters following a colon.  But there are so many possibilities I don't where to edit.

So, I'm removing the colons and replacing them with dashes.  This seems mainly to occur in MAC addresses.




sudo iwlist scan-

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed -
          Cell 01 - Address- 00-1B-36-2B-9D-17
                    ESSID-"XIV"
                    Protocol-IEEE 802.11bg
                    Mode-Master
                    Channel-1
                    Frequency-2.412 GHz (Channel 1)
                    Encryption key-on
                    Bit Rates-1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-47 dBm  Noise level=-68 dBm
                    IE- WPA Version 1
                        Group Cipher - WEP-40
                        Pairwise Ciphers (1) - WEP-40
                        Authentication Suites (1) - PSK
                    IE- IEEE 802.11i/WPA2 Version 1
                        Group Cipher - WEP-40
                        Pairwise Ciphers (2) - TKIP WEP-40
                        Authentication Suites (1) - PSK
                    Extra- Last beacon- 336ms ago
          Cell 02 - Address- 00-1C-16-10-D0-91
                    ESSID-"AKA"
                    Protocol-IEEE 802.11bg
                    Mode-Master
                    Channel-6
                    Frequency-2.437 GHz (Channel 6)
                    Encryption key-on
                    Bit Rates-1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-54 dBm  Noise level=-68 dBm
                    Extra- Last beacon- 160ms ago
          Cell 03 - Address- 00-1D-7E-32-9B-9C
                    ESSID-"mike"
                    Protocol-IEEE 802.11bg
                    Mode-Master
                    Channel-6
                    Frequency-2.437 GHz (Channel 6)
                    Encryption key-off
                    Bit Rates-1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=82/100  Signal level=-67 dBm  Noise level=-68 dBm
                    Extra- Last beacon- 192ms ago
          Cell 04 - Address- 00-0C-41-66-6E-36
                    ESSID-"Pablo"
                    Protocol-IEEE 802.11bg
                    Mode-Master
                    Channel-11
                    Frequency-2.462 GHz (Channel 11)
                    Encryption key-on
                    Bit Rates-1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-47 dBm  Noise level=-68 dBm
                    IE- WPA Version 1
                        Group Cipher - WEP-40
                        Pairwise Ciphers (2) - TKIP WEP-40
                        Authentication Suites (1) - PSK
                    IE- IEEE 802.11i/WPA2 Version 1
                        Group Cipher - WEP-40
                        Pairwise Ciphers (2) - TKIP WEP-40
                        Authentication Suites (1) - PSK
                    Extra- Last beacon- 76ms ago
          Cell 05 - Address- 00-26-7D-05-F6-C2
                    ESSID-"NETGEAR"
                    Protocol-IEEE 802.11bg
                    Mode-Master
                    Channel-11
                    Frequency-2.462 GHz (Channel 11)
                    Encryption key-off
                    Bit Rates-1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-83 dBm  Noise level=-68 dBm
                    Extra- Last beacon- 2184ms ago
          Cell 06 - Address- 00-1B-2F-73-CD-66
                    ESSID-"Bear Cake"
                    Protocol-IEEE 802.11bg
                    Mode-Master
                    Channel-11
                    Frequency-2.462 GHz (Channel 11)
                    Encryption key-on
                    Bit Rates-1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-83 dBm  Noise level=-68 dBm
                    IE- IEEE 802.11i/WPA2 Version 1
                        Group Cipher - TKIP
                        Pairwise Ciphers (1) - TKIP
                        Authentication Suites (1) - PSK
                       Preauthentication Supported
                    Extra- Last beacon- 2856ms ago

eth2      Scan completed -
          Cell 01 - Address- 00-1B-36-2B-9D-17
                    ESSID-"XIV"
                    Protocol-IEEE 802.11bg
                    Mode-Master
                    Channel-1
                    Frequency-2.412 GHz (Channel 1)
                    Encryption key-on
                    Bit Rates-1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-49 dBm  Noise level=-68 dBm
                    IE- WPA Version 1
                        Group Cipher - WEP-40
                        Pairwise Ciphers (1) - WEP-40
                        Authentication Suites (1) - PSK
                    IE- IEEE 802.11i/WPA2 Version 1
                        Group Cipher - WEP-40
                        Pairwise Ciphers (2) - TKIP WEP-40
                        Authentication Suites (1) - PSK
                    Extra- Last beacon- 288ms ago
          Cell 02 - Address- 00-1C-16-10-D0-91
                    ESSID-"AKA"
                    Protocol-IEEE 802.11bg
                    Mode-Master
                    Channel-6
                    Frequency-2.437 GHz (Channel 6)
                    Encryption key-on
                    Bit Rates-1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=85/100  Signal level=-63 dBm  Noise level=-68 dBm
                    Extra- Last beacon- 200ms ago
          Cell 03 - Address- 00-1D-7E-32-9B-9C
                    ESSID-"mike"
                    Protocol-IEEE 802.11bg
                    Mode-Master
                    Channel-6
                    Frequency-2.437 GHz (Channel 6)
                    Encryption key-off
                    Bit Rates-1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=80/100  Signal level=-68 dBm  Noise level=-68 dBm
                    Extra- Last beacon- 216ms ago
          Cell 04 - Address- 00-0C-41-66-6E-36
                    ESSID-"Pablo"
                    Protocol-IEEE 802.11bg
                    Mode-Master
                    Channel-11
                    Frequency-2.462 GHz (Channel 11)
                    Encryption key-on
                    Bit Rates-1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-45 dBm  Noise level=-68 dBm
                    IE- WPA Version 1
                        Group Cipher - WEP-40
                        Pairwise Ciphers (2) - TKIP WEP-40
                        Authentication Suites (1) - PSK
                    IE- IEEE 802.11i/WPA2 Version 1
                        Group Cipher - WEP-40
                        Pairwise Ciphers (2) - TKIP WEP-40
                        Authentication Suites (1) - PSK
                    Extra- Last beacon- 24ms ago
          Cell 05 - Address- 00-1B-2F-73-CD-66
                    ESSID-"Bear Cake"
                    Protocol-IEEE 802.11bg
                    Mode-Master
                    Channel-11
                    Frequency-2.462 GHz (Channel 11)
                    Encryption key-on
                    Bit Rates-1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=70/100  Signal level=-80 dBm  Noise level=-68 dBm
                    IE- IEEE 802.11i/WPA2 Version 1
                        Group Cipher - TKIP
                        Pairwise Ciphers (1) - TKIP
                        Authentication Suites (1) - PSK
                       Preauthentication Supported
                    Extra- Last beacon- 40ms ago

---

### Post by Allus on 2008-02-19
lshw -C network:

  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:4d:bd:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.1.102 latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:6c:2c:44
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 02
       serial: 00:0c:41:2e:83:ec
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

---

### Post by Allus on 2008-02-19
cat /etc/network/interfaces:

auto lo
iface lo inet loopback

---


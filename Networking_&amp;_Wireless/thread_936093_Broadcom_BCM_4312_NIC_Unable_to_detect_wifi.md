---
title: "Broadcom BCM 4312 NIC Unable to detect wifi"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by keyshawn on 2008-10-02
Hi, 

I have an Acer Extensa 5620z, purchased about 2 weeks ago. Immediately after install, I installed drivers to have the wifi enabled on it (I frankly forget how I did it). 
I do know that if you click 'system > administration > hardware drivers' 
an entry named 'wl' appeared. 

This configuration worked fine until 2 or 3 days ago, when I was on my wifi and began to have problems accessing my wifi connection 
(the phrase. 'waiting for network key for the wireless network '....' would
hang there continually. 

(I have a router, D-Link model WBR-2310, firmware 1.02 )(WPA encrypted). My housemates, 
who have macbooks and a compaq with windows on it, have not noticed had any trouble with the router, save the occasional disconnect (which I blame on a poor router, the d-link)  

here is information on my wifi card: 

lspci -n | grep '14e4:43': 
```
04:00.0 0280: 14e4:4315 (rev 01)
```lspci: 
```
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```
I figured somehow my configuration was borked. 


I decided to follow the directions on [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff:](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff:)

I followed step. one. 

Before step 2, 
I issued the following command (as recommended) to properly identify 
my NIC card: 

```
lspci -n | grep '14e4:43'
```
and I received: 
```
04:00.0 0280: 14e4:4315 (rev 01)
```


However, according to that page [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202:%20Download%20and%20Extract%20Drivers]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202:%20Download%20and%20Extract%20Drivers"), the lspci results above 
indicate that I have a BCM4310 (rev 01) card, and to continue with step 2e. 

Following the page, I completed step 2e, and followed the directions, 
and these results were returned. 

skorasaurus@skorasaurus-lappy:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

got this after issuing sudo ndiswrapper -m: 


```
************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************
```
echo 'ndiswrapper' | sudo tee -a /etc/modules: 
```
ndiswrapper
odules
```issuing echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant 
returned: 


```
ENABLED=0
```
issuing the last command: 

korasaurus@skorasaurus-lappy:~/bcm43xx$ lshw -C network 
```
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:c5:76:ad
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 ip=192.168.0.107 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:0a:ef:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/200
```7, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
=================================================

After rebooting, my wifi was still not working, so I found the thread at 

[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

and followed those directions. 

Unfortunately, my wifi is still not able to pick up any signal. 


=============================================================

Right now, 

I am at a loss of what to do, and not sure if I should try the ndiswrapper 
troubleshooting guide .

Also, the wl driver (see my first paragraph) is still there and enabled, but no wireless access points 
are showing up in gnome's network manager and it is labelled as 
''not in use'.

Phew. Thank you for reading and any help,
keyshawn

---

### Post by Idefix82 on 2008-10-02
But did you include ndiswrapper into the modules file for it to be loaded upon boot? I am asking because the output from your last lshw looked promising but you are saying that you rebooted after that. Did you try the WiFi before rebooting? Was the output from lshw the same after rebooting? If not then you might just have to make sure you start ndiswrapper upon boot by adding it to /etc/modules.

Having said that, I don't know why your previous configuration could have stopped working.

---

### Post by Ayuthia on 2008-10-02
> **keyshawn said:**
> Hi, 

I have an Acer Extensa 5620z, purchased about 2 weeks ago. Immediately after install, I installed drivers to have the wifi enabled on it (I frankly forget how I did it). 
I do know that if you click 'system > administration > hardware drivers' 
an entry named 'wl' appeared. 

This configuration worked fine until 2 or 3 days ago, when I was on my wifi and began to have problems accessing my wifi connection 
(the phrase. 'waiting for network key for the wireless network '....' would
hang there continually. 

(I have a router, D-Link model WBR-2310, firmware 1.02 )(WPA encrypted). My housemates, 
who have macbooks and a compaq with windows on it, have not noticed had any trouble with the router, save the occasional disconnect (which I blame on a poor router, the d-link)  

here is information on my wifi card: 

lspci -n | grep '14e4:43': 
```
04:00.0 0280: 14e4:4315 (rev 01)
```lspci: 
```
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```
I figured somehow my configuration was borked. 


I decided to follow the directions on [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff:](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff:)

I followed step. one. 

Before step 2, 
I issued the following command (as recommended) to properly identify 
my NIC card: 

```
lspci -n | grep '14e4:43'
```
and I received: 
```
04:00.0 0280: 14e4:4315 (rev 01)
```


However, according to that page [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202:%20Download%20and%20Extract%20Drivers]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202:%20Download%20and%20Extract%20Drivers"), the lspci results above 
indicate that I have a BCM4310 (rev 01) card, and to continue with step 2e. 

Following the page, I completed step 2e, and followed the directions, 
and these results were returned. 

skorasaurus@skorasaurus-lappy:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

got this after issuing sudo ndiswrapper -m: 


```
************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************
```
echo 'ndiswrapper' | sudo tee -a /etc/modules: 
```
ndiswrapper
odules
```issuing echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant 
returned: 


```
ENABLED=0
```
issuing the last command: 

korasaurus@skorasaurus-lappy:~/bcm43xx$ lshw -C network 
```
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:c5:76:ad
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 ip=192.168.0.107 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:0a:ef:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/200
```7, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
=================================================

After rebooting, my wifi was still not working, so I found the thread at 

[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

and followed those directions. 

Unfortunately, my wifi is still not able to pick up any signal. 


=============================================================

Right now, 

I am at a loss of what to do, and not sure if I should try the ndiswrapper 
troubleshooting guide .

Also, the wl driver (see my first paragraph) is still there and enabled, but no wireless access points 
are showing up in gnome's network manager and it is labelled as 
''not in use'.

Phew. Thank you for reading and any help,
keyshawn

Let's start by checking to see if we can see anything with the wl driver:
```
sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe wl
sudo ifconfig eth1 up
sudo ifconfig wlan0 up
sudo iwlist scan
```
This will remove any conflicting wireless drivers and then load the wl driver.  It will then try to turn on the card.  One of the ifconfig commands is going to fail.  I just used both because I am not for sure which one is your card.  If it does not show any wireless, you might check dmesg to see if there are any errors out there for the wl module.

---

### Post by keyshawn on 2008-10-02
> **Ayuthia said:**
> Let's start by checking to see if we can see anything with the wl driver:
```
sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe wl
sudo ifconfig eth1 up
sudo ifconfig wlan0 up
sudo iwlist scan
```This will remove any conflicting wireless drivers and then load the wl driver.  It will then try to turn on the card.  One of the ifconfig commands is going to fail.  I just used both because I am not for sure which one is your card.  If it does not show any wireless, you might check dmesg to see if there are any errors out there for the wl module.

i did the first line of that and nothing was returned :confused:

---

### Post by Ayuthia on 2008-10-02
> **keyshawn said:**
> i did the first line of that and nothing was returned :confused:

Yes.  I forgot to mention that.  The modprobe and ifconfig commands do not return anything unless there is an error.  Please go ahead and try the commands again.  One of the ifconfig commands should create an error, but that is ok.

---

### Post by keyshawn on 2008-10-02
None of them returned an error except: 

skorasaurus@skorasaurus-lappy:~$ sudo iwlist scan:
```
eth1: ERROR while getting interface flags: No such device

```

I also received the following output from sudo iwlist scan: 

[code]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0B:85:74:0A:9C
                    ESSID:"Admin"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-17 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:0B:85:74:0A:9A
                    ESSID:"Academic"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-17 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:0B:85:74:0A:99
                    ESSID:"ResNet"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-17 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:1C:F0:54:12:A9
                    ESSID:"gary_motel"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-26 dBm  Noise level:-4 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:0F:66:A1:28:1F
                    ESSID:"crown vic"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-4 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 00:1C:10:87:C7:42
                    ESSID:"BRANDO"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/5  Signal level:-91 dBm  Noise level:-91 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 07 - Address: 00:22:6B:4A:66:76
                    ESSID:"Day Man"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-90 dBm  Noise level:-4 dBm
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031483836363139371054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 08 - Address: 00:0F:B5:1E:B1:58
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-25 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
[code]

I included all of the scanned entries, although "gary_motel" is the name of my router.

---

### Post by keyshawn on 2008-10-05
I'm politely bumping this thread.

---

### Post by keyshawn on 2008-10-05
I have resolved this problem (for now) by removing ndiswrapper, reinstalling the wl driver. 

So far, the wifi seems to be functioning.

---


---
title: "I can't connect to my AP, but I see (iwlist scan)"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by trifold on 2008-03-21
Hardware:
HP Pavilion tx1120us
Kubuntu 7.10 amd 64
 sudo lshw -C network
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:51:60:e3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

Output from iwlist:

sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:0C:76:CC:A1:CC
                    ESSID:"Z1LNet"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=84/100  Signal level=-68 dBm  Noise level=-66 dBm
                    Extra: Last beacon: 56ms ago
Then I enter:
sudo iwconfig eth1 mode managed
sudo iwconfig eth1 channel 2
sudo iwconfig eth1 ap 00:0C:76:CC:A1:CC
sudo iwconfig eth1 essid Z1LNet
and when I want to obtain  ip from dhcp a get
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
iwconfig eth1 gives me:

eth1      IEEE 802.11b/g  ESSID:"Z1LNet"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.417 GHz  Access Point: 00:0C:76:CC:A1:CC
          Bit Rate=1 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

From this looks like I am connected to AP, but it says that Link Quality is 0! When I log to AP I see that number of active clients is 0! This means I am not assosiated with AP. My ap gives adresses in range 192.168.100.100-192.168.100.200. I tried to set manually adress with sudo ifconfig eth1 inet 192.168.100.101 but still I can't ping anyting!

Any help is welcome!

Regards

---

### Post by jan quark on 2008-03-22
oh dear
the BCM94311MCG wlan mini-PCI can be the hell on earth...

try to configure the network manually setting up a static IP

besides, I had to remove my BCM94311MCG wlan mini-PCI completely from my machine and buy a usb wlan stick to be able to write this to you :(

---

### Post by trifold on 2008-03-25
I already tried it but it doesn't work... What wifi card did you buy?

---


---
title: "RaLink RT2600 SIOCSIFFLAGS Error Ater Upgrade to Hardy"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Schiz0 on 2008-05-03
I have a PCI wireless network card. It worked perfectly fine in Gusty. I got a new HDD recently and installed Hardy from scratch, and now the wireless card isn't working. Whenever I try to bring up the interface, I get the error "SIOCSIFFLAGS: No such file or directory". I configure everything from the command line, and NetworkManager is disabled.

Here's the output from multiple commands:

sudo lscpi:
03:02.0 Network controller: RaLink RT2600 802.11 MIMO

sudo lshw -C network:
 *-network DISABLED
      description: Wireless interface
      product: RT2600 802.11 MIMO
      vendor: RaLink
      physical id: 2
      bus info: pci@0000:03:02.0
      logical name: wmaster0
      version: 00
      serial: 00:50:18:4e:7b:29
      width: 32 bits
      clock: 33MHz
      capabilities: pm bus_master cap_list logical ethernet physical wireless
      configuration: broadcast=yes driver=rt61pci ip=192.168.1.234
latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g

sudo lsmod | grep rt:
parport_pc             41128  0
parport                44300  2 parport_pc,lp
rt61pci                27648  0
rt2x00pci              12800  1 rt61pci
rt2x00lib              25344  2 rt61pci,rt2x00pci
rfkill                 10128  1 rt2x00lib
input_polldev           6928  1 rt2x00lib
crc_itu_t               3584  1 rt2x00lib
mac80211              192532  3 rt61pci,rt2x00pci,rt2x00lib
iTCO_vendor_support     5764  1 iTCO_wdt
eeprom_93cx6            3840  1 rt61pci

cat /etc/network/interfaces:
iface wlan0 inet static
       address 192.168.1.243
       netmask 255.255.255.0
       gateway 192.168.1.1
       wireless-key s:InsertASCIIPassHere
       wireless-essid InsertSSIDHere
auto wlan0

sudo iwconfig:
lo        no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11g  ESSID:""
         Mode:Managed  Channel:0  Access Point: Not-Associated
         Tx-Power=0 dBm
         Retry min limit:7   RTS thr:off   Fragment thr=2346 B
         Encryption key:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo ifconfig wlan0 up:
SIOCSIFFLAGS: No such file or directory

---


---
title: "Edimax EW-7728In 802.11n PCI card wireless config issue"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by jumpslu7 on 2007-11-11
I've spent far too long trying to get this wireless card working, so I thought I'd ask in the forums.  I hope I'm just missing something silly.

The wireless card is an Edimax EW-7728In, which is an 802.11n draft 2 compliant PCI card.

I followed the procedure of compiling & installing ndiswrapper and the windows driver for the card which went fine.

beaver kernel:  ndiswrapper version 1.49 loaded (smp=no, preempt=no)
beaver kernel:  ndiswrapper: driver rt2860 (Ralink Technology, Corp.,03/12/2007, 1.00.02.0000) loaded
beaver kernel:  ndiswrapper: using IRQ 21

jts@beaver:~$ ndiswrapper -l
rt2860 : driver installed
        device (1814:0601) present

jts@beaver:~$ lspci -nn | grep Network
00:08.0 Network controller [0280]: RaLink Unknown device [1814:0601]

jts@beaver:~$ dmesg | grep wlan0

[   27.944000] wlan0: ethernet device 00:18:23:22:AB:47 using serialized NDIS driver: rt2860, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11n Wireless Card.', 1814:0601.5.conf

[   27.944000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

jts@beaver:~$ sudo lcpci -v:
00:08.0 Network controller: RaLink Unknown device 0601
        Subsystem: RaLink Unknown device 2860
        Flags: bus master, slow devsel, latency 32, IRQ 11
        Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 3

jts@beaver:~$ sudo lshw -C network
  *-network:0
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: wlan0
       version: 00
       serial: 00:18:23:22:FA:47
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2860 driverversion=1.45+Ralink Technology, Corp.,03 ip=192.168.1.80 latency=32 link=no maxlatency=4 mingnt=2 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

There are two other ethernet interfaces built into the motherboard, both are RTL-8110SC/8169SC Gigabit Ethernet and I have no problems with them.
        
My wireless AP is configured as follows:
jts@beaver:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:23:22:FA:47
                    ESSID:"ILoveBeaver"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=1000
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
        
My /etc/network/interfaces file contains the following config for the wireless card:

auto wlan0
iface wlan0 inet static
      address 192.168.1.80
      netmask 255.255.255.0
      broadcast 192.168.1.255
      gateway 192.168.1.1

wpa-driver wext
wpa-mode managed
wpa-ssid ILoveBeaver
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <mybiglonghexstringhere>
	
my iwconfig version information is as follows:
jts@beaver:~$ sudo iwconfig --version
iwconfig  Wireless-Tools version 29
          Compatible with Wireless Extension v11 to v21.

Kernel    Currently compiled with Wireless Extension v22.

wlan0     Recommend Wireless Extension v18 or later,
          Currently compiled with Wireless Extension v22.

It seems that wpa supplicant is started by ifupdown.sh in /etc/wpa_supplicant and daemonised.  However, I'm unable to set a config file for this to override the content of /etc/network/interfaces (the config details in the interfaces file fails to associate to my AP)

After a /etc/init.d/networking restart, I get the following:

jts@beaver:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and the daemonised process for wpa_supplicant can be found:
jts@beaver:~$ ps aux | grep wpa_sup
root      5189  0.0  0.0   3844   716 ?        Ss   14:54   0:00 /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant

When I kill this process and call wpa supplicant manually, as in:

jts@beaver:~$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/sup.conf -dd &

Connection succeeds, telling me that there's nothing wrong with my config file sup.conf, only the /etc/network/interfaces content which I've supplied (and is then parsed for my WPA settings - seemingly unsuccessfully.)

On successful connection, I get:

jts@beaver:/etc/wpa_supplicant$ sudo iwconfig wlan0

wlan0     IEEE 802.11g  ESSID:"ILoveBeaver"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:18:23:22:FA:47
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:off   Fragment thr:off
          Encryption key:9260-etcetcetc   Security mode:restricted
          Power Management:off
          Link Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

But I'd really like this config problem solved, so that I don't have to manually kill the daemonised wpa_supplicant process and call it from the command line myself each time.  That's not feasible, as I'd like to locate the box (which is a mini-itx based machine) remotely.  (its currently connected to the router via ethernet patch cable).

Finally, here's my sup.conf file which I supply to wpa_supplicant manually (this config works!)
jts@beaver:~$ cat /etc/wpa_supplicant/sup.conf
ctrl_interface=/var/run/wpa_supplicant
network={
  ssid="ILoveBeaver"
  psk="yourmotherchasestrucksandeatsfromtrashcans"
  key_mgmt=WPA-PSK
  proto=WPA
}

Any help greatly appreciated!
jts

---

### Post by jumpslu7 on 2008-01-01
I happily found the solution to my problem. It was an issue in my /etc/network/interfaces file.  My solution can be read at [http://belfastgeek.net/2007/12/26/edimax-80211n-wireless-card-on-ubuntu-linux-with-ndiswrapper-and-wpa_supplicant/](http://belfastgeek.net/2007/12/26/edimax-80211n-wireless-card-on-ubuntu-linux-with-ndiswrapper-and-wpa_supplicant/)

Hope this helps someone.  If not, leave a comment on my blog, I'll try to help if I can!

cheers,
j

---

### Post by BobCFC on 2008-01-03
Hi, I am glad you got it working.  If you had an N router do you think it would connect in N mode under Linux?

I'm looking to replace my old bluetooth setup now that 802.11n has come down in price but I thought 802.11n was poorly supported by the kernel.  Do they just mean native drivers?  I'm happy using ndiswrapper

I tried to post on your blog but it said comments were disabled.


EDIT: I just looked on the [Edimax site]("http://www.edimax.com/en/produce_detail.php?pd_id=225&pl1_id=1&pl2_id=44") and they have source code for linux! It seems to have the Ralink  RT2860 chipset

---


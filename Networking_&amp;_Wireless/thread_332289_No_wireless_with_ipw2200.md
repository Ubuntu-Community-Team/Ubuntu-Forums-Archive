---
title: "No wireless with ipw2200"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by mspendlo on 2007-01-05
Hi folks

This is must first Ubuntu / Linux install and I'm not having much joy with getting on to a wifi network.

I installed 6.06lts originally and i could see my essid in network-manager but I couldn't connect (or wasn't assigned dhcp). I have little control over the network in which I am trying to connect, I know it has a passphrase WPA so I followed various help guides to set up wpa_supplicant but no success. I also tried to access the wireless access point on the network to switch off the WPA but the supplied software is playing up. I am being very cautious changing things on the router end as it's not my network and it's essential to other peoples business.

In an effort for resolution I downloaded and installed 6.10 hoping that things might have been updated. Unfortunately it seems to have regressed ! Now I can't even see the essid in network-manager.

I have followed the  [WirelessTroubleshootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")
 and seem to be unable to connect to the router (although it is displayed in iwlist) and certainly have no DHCP.

I have included a log of commands from the guide and their output.

Please help if you can. I am supposed to be spending this time playing with Ruby yet this wireless is killing me - I am nearly at the point of reverting to my Windows installation :(

TIA

Matt

------------------------------------------------------------------------
matt@matt-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:80:52:ca
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half link=no multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:a000-a0ff iomemory:b0002000-b00020ff irq:233
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:bf:5b:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=unassociated
       resources: iomemory:b0001000-b0001fff irq:50

matt@matt-laptop:~$ sudo lsmod | grep ipw
ipw2200               115652  0 
ieee80211              35272  1 ipw2200

matt@matt-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

matt@matt-laptop:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:13:46:74:08:22
                    ESSID:"Boyles Network"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-75 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 244ms ago

# now try and force the connection, no essid showing in network-admin. 
# iwconfig says it doesn't support passphrase. I tried `key s:my-secret-ascii-key' but
# the command failed with : Error : unrecognised wireless request "s:my-scret-ascii-key"

matt@matt-laptop:~$ sudo iwconfig eth1 essid "Boyles Network" ap 00:13:46:74:08:22 commit
matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Boyles Network"  
          Mode:Managed  Channel=0  Access Point: 00:13:46:74:08:22   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

matt@matt-laptop:~$ ping google.com
ping: unknown host google.com
matt@matt-laptop:~$ ping 10.1.1.1
connect: Network is unreachable

------------------------------------------------------------------------

---

### Post by BOBSONATOR on 2007-01-05
A quick use of the search button brought this upon my eyes...

[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by zmuth734 on 2007-01-05
I use this driver on my laptop and this is what I do to get mine to work when it's acting up (I only have WEP though).

```

sudo iwconfig essid network-name-here
sudo iwconfig key restricted wep-key-here
sudo ifconfig eth1 up
sudo dhclient eth1

```

Also the driver is set to 802.11b and also 802.11g.  If its a 802.11b network you can use

```
sudo iwpriv eth1 set_mode 2
``` to use only 802.11b and sometimes it works better.

I'm sorry that I don't know anything about using WPA in ubuntu. ](*,)

---

### Post by mspendlo on 2007-01-06
> **BOBSONATOR said:**
> A quick use of the search button brought this upon my eyes...

[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

Ah, but a quick read of my original post said that I had tried various tutorials on wpa_supplicant (including the later version of your link).

That said, and with no other options I went back and tried again from [http://www.ubuntuforums.org/showthread.php?t=263136]("http://www.ubuntuforums.org/showthread.php?t=263136")

After setting this up and refering back to [WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") I was able to ping the router and other boxes on the network. Unfortunately still no internet though.

After trying all the suggestions my last ditch was to reboot - sure enough it worked :)

I think what's perhaps is a little confusing to newbies like myself is that lack of synchronization between the backend config files and the network-manager gui (the gui still shows my wireless as disconnected even as i write this). I had also wrongly assumed that if network-manager didn't auto display my network I'd have no chance of connecting to it.

Anyways, thanks for the hints folks.

Matt

---

### Post by darkmediator on 2007-01-07
@mespendlo : Can u post the contents of "/etc/network/interfaces"?

---

### Post by mspendlo on 2007-01-07
**Just to be crystal my wifi IS now working so no more problems.**

Maybe you want this for yourself tho :

--------------------------
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


--------------------------

---


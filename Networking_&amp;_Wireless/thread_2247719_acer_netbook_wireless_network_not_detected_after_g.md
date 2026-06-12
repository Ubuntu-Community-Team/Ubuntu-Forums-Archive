---
title: "acer netbook wireless network not detected after getting new router (current OS)"
date: 2014-10-09
forum: Networking &amp; Wireless
---

### Post by nbloomis on 2014-10-09
I posted a thread a while back on this issue, but a forum moderator asked me to update my OS in order to get support.  I've done that now, so...can anyone help me with this issue? (see below)
I got a new router recently, and I think I may have deleted the  connection in lubuntu's network preferences.  I am not sure if my  wireless card is even responding right now (acer netbook with lubuntu on  external hd).  I know it isn't the router because I have other  computers connecting to it.  I'm thinking maybe I can 'Add' new  connection, maybe fill in some info on the bottom of the router?  I wish  I could just detect the network and connect...
Any help is much appreciated!
Nate

---

### Post by weatherman2 on 2014-10-09
What kind of router is it?  (Make/Model?)  Is it set to allow 802.11n and 802.11g wireless connections?  If your Acer is older and has only a G wireless card, it would be able to connect to a new router only if it allows the older 802.11g connections.  (It's possible to set a router not to allow 802.11g connections.)

On your Acer, open a terminal window and type:

```

sudo lshw -C network

```

You might also run the "wireless script" linked at the top of this forum in the "sticky" post and post the results from that here.

---

### Post by Vladlenin5000 on 2014-10-09
You should start this new thread by posting an updated result of the same script you were asked to run in the other thread. That and also give the info you should have given before to the answers that emerged from the other thread, namely, has it worked before? And, did it work in the live session?

---

### Post by nbloomis on 2014-10-09
sorry let me try that again
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

nathan-AOA110 3.13.0-36-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
Memory : 1495 MB
Uptime : 21:11:27 up  1:25,  2 users,  load average: 0.14, 0.32, 0.27


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:015b]
    Kernel driver in use: r8169
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e008]
    Kernel driver in use: ath5k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 0bc2:2100 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211
wmi                    18673  0 


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | ath5k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | r8169  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             209.18.47.61
    DNS:             209.18.47.62
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

belkin.789           : ssid=belkin.789 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Brewbakers           : ssid=Brewbakers | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Brewbakers_Guest     : ssid=Brewbakers_Guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Fairpoint6E6F        : ssid=Fairpoint6E6F | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Fairpoint6E6F 1      : ssid=Fairpoint6E6F | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.568/0.858/1.149/0.291 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.107/0.114/0.122/0.013 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     No scan results


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=eb4c8660-a3e2-4f47-8e73-9124219efbe7 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.140741] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.141498] audit: initializing netlink socket (disabled)
[    1.774522] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   23.827392] wmi: Mapper loaded
[   24.937260] ath5k 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   24.937605] ath5k 0000:03:00.0: registered as 'phy0'
[   26.494147] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.341889] ath: EEPROM regdomain: 0x65
[   28.341901] ath: EEPROM indicates we should expect a direct regpair map
[   28.341910] ath: Country alpha2 being used: 00
[   28.341915] ath: Regpair used: 0x65
[   28.463862] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   29.178115] acer_wmi: Acer Laptop ACPI-WMI Extras
[   29.178130] acer_wmi: Blacklisted hardware detected - not loading
[   34.235329] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.237153] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  253.640948]  [<c15d8821>] ? inet_gro_receive+0x1d1/0x200
[  253.640960]  [<c1575656>] ? __netif_receive_skb+0x16/0x60
[  253.641059]  [<f8667985>] ? rtl8169_poll+0x115/0x4c0 [r8169]
[  253.641074]  [<c1575990>] ? net_rx_action+0x110/0x1f0

    ======== Done ========


```

---

### Post by nbloomis on 2014-10-09
```

nathan@nathan-AOA110:~$ sudo lshw -C network
  *-network               [B^[[D
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:43:18:b4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:71010000-71010fff memory:71000000-7100ffff memory:71020000-7103ffff
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2b:0c:b5:46
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.13.0-36-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:75200000-7520ffff


```

---

### Post by Vladlenin5000 on 2014-10-09
```
[   29.178130] acer_wmi: [COLOR=#ff0000]Blacklisted hardware detected - not loading[/COLOR]
```

So the problem originally detected is still there...
Now that you have a supported version varunendra or others will be able to help you. I have zero experience with Atheros chips.

---

### Post by nbloomis on 2014-10-15
I recently got a new modem from Time Warner (which my landlord pays for), and poof, I can't connect wirelessly anymore.  Time Warner tech support was of little help, since they are not trained for Linux.  Any ideas?
Thanks!
Nate

---

### Post by varunendra on 2014-10-22
Hi nbloomis, sorry for not replying to your PM earlier. Sorry to Vladlenin5000 too if I shook your trust in me, but am as clueless as you might be with the above "blacklisted hardware" error. I usually love digging and tinkering but wasn't in a good enough mood to do that. You can find the reason here : [http://ubuntuforums.org/showpost.php?p=13149033](http://ubuntuforums.org/showpost.php?p=13149033)

Anyway, not being able to find any useful references to the above error, I can only 'guess' some possible fixes.

@nbloomis,
Please try these if you are still looking for help on this -

**1)** Try manually loading "acer-wmi" driver -
```
sudo modprobe -v acer_wmi
```
and report back if it returns any errors. If not, can the wifi scan available networks now? Try with -
```
sudo iwlist scan
```

**2)** If you get any errors above, or wifi doesn't work after loading acer_wmi, try blacklisting it so the kernel doesn't even bother loading it -
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and run the "sudo iwlist scan" command again. Can it detect networks now?

If these don't help, please post back a fresh wireless_script report and a full output of -
```
lsmod
```
..and hope someone else can pick it up from there in case I happen to go 'missing' again.

Just so you know, chili555 is the best wireless troubleshooter here, and there are some others as well who are much better and more knowledgeable than me. Feel free to bump your post every 24 hours (or more) if you don't get any replies to your posts.

---

### Post by bapoumba on 2014-10-22
Threads merged.

---

### Post by nbloomis on 2014-10-24
Hi Varun,
Sounds like you are having lots of fun smashing things over there...funny, you never recommend that solution to anyone else?...

Thank you for getting back to me after all, I too am losing patience with my machine, so much so that I pulled out my old IBM Thinkpad and connected it to the internet - bad idea...

Anyway, as to my wireless adapter, I can now see the network I would like to connect to (WLAN-3652F), but still can't connect.  I have the password in correctly...Also, the light next to the wireless button on my keyboard blinks yellow when I try to connect.

Here is the latest wireless_script
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

nathan-AOA110 3.13.0-37-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
Memory : 1495 MB
Uptime : 12:27:41 up 7 min,  2 users,  load average: 0.33, 0.53, 0.34


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:015b]
    Kernel driver in use: r8169
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e008]
    Kernel driver in use: ath5k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 0bc2:2100 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211
wmi                    18673  0 


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | ath5k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    WLAN-3652F:      Infra, <MAC C-02 WLAN-3652F>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | r8169  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             209.18.47.61
    DNS:             209.18.47.62
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

belkin.789           : ssid=belkin.789 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Brewbakers           : ssid=Brewbakers | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Brewbakers_Guest     : ssid=Brewbakers_Guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Fairpoint6E6F        : ssid=Fairpoint6E6F | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Fairpoint6E6F 1      : ssid=Fairpoint6E6F | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
i1                   : ssid=i1 | autoconnect=false | mac-address=<MAC wlan0> | ipv4=shared | ipv6=auto 
WLAN-3652F           : ssid=WLAN-3652F | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.620/0.959/1.298/0.339 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.064/0.075/0.087/0.014 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 WLAN-3652F>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"WLAN-3652F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000232f798f1b
                    Extra: Last beacon: 60ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 WLAN-3652F>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"WLAN-3652F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000232f7a1184
                    Extra: Last beacon: 584ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist acer_wmi

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=eb4c8660-a3e2-4f47-8e73-9124219efbe7 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.134187] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.134947] audit: initializing netlink socket (disabled)
[    1.771520] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   19.745521] wmi: Mapper loaded
[   22.159969] ath5k 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   22.160350] ath5k 0000:03:00.0: registered as 'phy0'
[   23.118629] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.985870] ath: EEPROM regdomain: 0x65
[   23.985882] ath: EEPROM indicates we should expect a direct regpair map
[   23.985891] ath: Country alpha2 being used: 00
[   23.985896] ath: Regpair used: 0x65
[   24.085579] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   28.800904] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.801832] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   82.657235] wlan0: authenticate with <MAC C-01 WLAN-3652F>
[   82.665374] wlan0: send auth to <MAC C-01 WLAN-3652F> (try 1/3)
[   82.680350] wlan0: send auth to <MAC C-01 WLAN-3652F> (try 2/3)
[   82.692848] wlan0: send auth to <MAC C-01 WLAN-3652F> (try 3/3)
[   82.709968] wlan0: authentication with <MAC C-01 WLAN-3652F> timed out
[   82.849365] wlan0: authenticate with <MAC C-02 WLAN-3652F>
[   82.849726] wlan0: direct probe to <MAC C-02 WLAN-3652F> (try 1/3)
[   83.052195] wlan0: direct probe to <MAC C-02 WLAN-3652F> (try 2/3)
[   83.256139] wlan0: direct probe to <MAC C-02 WLAN-3652F> (try 3/3)
[   83.460139] wlan0: authentication with <MAC C-02 WLAN-3652F> timed out
[  119.266066] wlan0: authenticate with <MAC C-01 WLAN-3652F>
[  119.272604] wlan0: send auth to <MAC C-01 WLAN-3652F> (try 1/3)
[  119.285369] wlan0: send auth to <MAC C-01 WLAN-3652F> (try 2/3)
[  119.302907] wlan0: send auth to <MAC C-01 WLAN-3652F> (try 3/3)
[  119.314384] wlan0: authentication with <MAC C-01 WLAN-3652F> timed out
[  120.362766] wlan0: authenticate with <MAC C-02 WLAN-3652F>
[  120.363340] wlan0: direct probe to <MAC C-02 WLAN-3652F> (try 1/3)
[  120.564169] wlan0: direct probe to <MAC C-02 WLAN-3652F> (try 2/3)
[  120.768114] wlan0: direct probe to <MAC C-02 WLAN-3652F> (try 3/3)
[  120.972165] wlan0: authentication with <MAC C-02 WLAN-3652F> timed out

    ======== Done ========


```

No worries if this is just becoming hogwash and super tedious for you.  This may be the universe telling me I need to suck it up and buy a real computer.  But what fun would that be?!
Regards,
Nate

---

### Post by nbloomis on 2014-10-24
...and the lsmod:
```

nathan@nathan-AOA110:~$ lsmod
Module                  Size  Used by
sparse_keymap          13708  0 
zram                   18032  2 
arc4                   12536  2 
bnep                   18895  2 
acerhdf                14178  0 
rfcomm                 53664  0 
snd_hda_codec_realtek    55163  1 
bluetooth             342208  10 bnep,rfcomm
snd_hda_intel          42730  1 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
ath5k                 134977  0 
coretemp               13195  0 
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               71309  0 
snd_rawmidi            25135  1 snd_seq_midi
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
ath                    23922  1 ath5k
binfmt_misc            13140  1 
videobuf2_core         39258  1 uvcvideo
joydev                 17101  0 
videodev              108503  2 uvcvideo,videobuf2_core
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
mac80211              546051  1 ath5k
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
lpc_ich                16864  0 
serio_raw              13230  0 
jmb38x_ms              18222  0 
i915                  709755  2 
cfg80211              409394  3 ath,ath5k,mac80211
drm_kms_helper         48868  1 i915
memstick               16174  1 jmb38x_ms
snd                    60939  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   244037  3 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
parport_pc             31981  0 
wmi                    18673  0 
video                  18903  1 i915
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
mac_hid                13037  0 
usb_storage            48417  2 
psmouse                91329  0 
sdhci_pci              18535  0 
sdhci                  37779  1 sdhci_pci
r8169                  61562  0 
mii                    13654  1 r8169


```

---


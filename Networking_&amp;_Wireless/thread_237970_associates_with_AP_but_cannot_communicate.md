---
title: "associates with AP but cannot communicate"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by zoggop on 2006-08-17
Hey,I just installed ubuntu on a thinkpad T20 (previously it ran debian), and am having issues with the Lucent Orinoco Silver wireless card.  The card appears to be detected and the modules are installed properly.  It even associates with the access point and ubuntu's swanky GUI network monitor icon shows signal strength, but is also says "Disconnected".  And it can't get a DHCP lease, nor ping the gateway if I set a static IP.  The system log all looks good when I insert the card except for "ADDRCONF(NETDEV_UP): eth1: link is not ready", the meaning of which I can't decipher.

Any ideas of what's going on here?

dmesg:
```

[  193.404271] pccard: PCMCIA card inserted into slot 0
[  193.404297] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[  193.411765] pcmcia: registering new device pcmcia0.0
[  193.821319] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pav el Roskin <proski@gnu.org>, et al)
[  193.833113] orinoco_cs 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[  193.915481] eth1: Hardware identity 0001:0001:0004:0000
[  193.915809] eth1: Station identity  001f:0001:0008:000a
[  193.915999] eth1: Firmware determined as Lucent/Agere 8.10
[  193.916008] eth1: Ad-hoc demo mode supported
[  193.916029] eth1: IEEE standard IBSS ad-hoc mode supported
[  193.916037] eth1: WEP supported, 104-bit key
[  193.916122] eth1: MAC address 00:02:2D:0D:E0:46
[  193.916219] eth1: Station name "HERMES I"
[  193.916678] eth1: ready
[  193.917226] eth1: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f
[  194.009090] ieee80211_crypt: registered algorithm 'NULL'
[  194.064200] hostap_cs: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[  194.242593] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"La Grange"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:CB:F6:91:A5
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/92  Signal level=-53 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig:
```

eth1      Link encap:Ethernet  HWaddr 00:02:2D:0D:E0:46
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100

```

dhclient in syslog:
```

Aug 16 22:03:44 localhost dhclient:
Aug 16 22:03:44 localhost kernel: [13737.125351] ADDRCONF(NETDEV_UP): eth1: link is
not ready
Aug 16 22:03:45 localhost dhclient: Listening on LPF/eth1/00:02:2d:0d:e0:46
Aug 16 22:03:45 localhost dhclient: Sending on   LPF/eth1/00:02:2d:0d:e0:46
Aug 16 22:03:45 localhost dhclient: Sending on   Socket/fallback
Aug 16 22:03:46 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67
interval 3
Aug 16 22:03:49 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67
interval 8
Aug 16 22:03:57 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67
interval 14
Aug 16 22:04:11 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67
interval 10
Aug 16 22:04:21 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67
interval 12
Aug 16 22:04:33 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67
interval 13
Aug 16 22:04:46 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67
interval 1
Aug 16 22:04:47 localhost dhclient: No DHCPOFFERS received.
Aug 16 22:04:47 localhost dhclient: No working leases in persistent database - sleeping.

```

---

### Post by solarcide on 2007-01-01
Hi there - I have the exact same problem on my IBM thinkpad T20. I use an Orinoco Gold card. Did you receive anything as a response?

Linux tells me that I am using the 0.15c driver series (which come installed with the OS).

One thing I have never seen mentioned is that the Wifi works flawlessly when you boot from the Ubuntu livecd/livedvd. It boggles my mind. I've searched google for two weeks trying to find an answer. These range from blacklisting hostap drivers to changing udev rules. Nothing has solved it, and yet every single time the livedvd loads, the WiFi works wonderfully.

My router: linsys wrtg54, open (for linux hassle reasons), default channels/fre,ssid broadbast.

Eth1 is the card's device name, and I continuously see Disconnected when you view the Network manager's settings.

Running the gnome network manager applet does not fix the issue.

One other thing: plugging in a regular network cable works fine, also.

---

### Post by aDOT on 2007-01-01
Hello,

tr y to do next for static IP
I have to sure that 
/etc/modprobe.d/ndiswraper
/etc/network/interfaces
/ect/iftab
have eth1 notice as device

second
sudo ifconfig eth1 192.168.1.2 netmask 255.255.255.0 broadcast 192.168.1.255
sudo route add default gw 192.168.1.1

third
/ect/resolv.conf must contain your DNSs
like next:
nameserver 212.188.1.4
namesever 195.34.32.122

Please change below addresses according to your settings: 
192.168.1.1 address of your gateway 
192.168.1.2 address of your wifi-card (eth1)

---


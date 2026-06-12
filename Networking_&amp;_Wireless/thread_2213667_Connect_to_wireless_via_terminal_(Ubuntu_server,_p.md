---
title: "Connect to wireless via terminal (Ubuntu server, partially connected)"
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by Turbine1991 on 2014-03-27
```
[CODE]
```[/CODE]Hello, after attempting to get this done for more than 24 hrs of reading forum threads and hammering in commands, I've decided to come here.

What I'm trying to achieve is connecting to a WPA2 access point, without a desktop environment.

So far I've installed wpa-supplicant, and wpa_passphrase  to generate /etc/wpa_supplicant/wpa_supplicant.conf:
```
network={        ssid="DOOM_NETCOMM"
        scan_ssid=1
        key_mgmt=WPA-PSK
        #psk="C297DC2A9F" #Commented by wpa_passphrase
        psk=cd8553e6b25b719ffdc110c687ded93eaf186dfe542342e5acb1cebda94f8993
}
```

To get it to affect the computer on boot, I've added this to /etc/rc.local:
```
wpa_supplicant -D wext -i wlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -B
sleep 5
```

My iwconfig displays it's connected to the access point upon reboot:
```
wlan0     IEEE 802.11bgn  ESSID:"DOOM_NETCOMM"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:60:64:32:E6:2C
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0
```

Then I request an address:
dhclient wlan0

And display the new ip address:
dhclient -v eth0

```
Listening on LPF/wlan0/1c:65:9d:66:a0:fdSending on   LPF/wlan0/1c:65:9d:66:a0:fd
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x7ab63596)
DHCPREQUEST of 192.168.20.105 on wlan0 to 255.255.255.255 port 67 (xid=0x7ab6359            6)
DHCPOFFER of 192.168.20.105 from 192.168.20.1
DHCPNAK from 192.168.1.1 (xid=0x7ab63596)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x2d3858c7)
DHCPREQUEST of 192.168.20.105 on wlan0 to 255.255.255.255 port 67 (xid=0x2d3858c            7)

```

Yet when I try to ping any computer in the house or google, it says host not found/unreachable. But when I plug a cable in, it works.

I tried using /etc/network/interfaces the other day, but adding wlan0 stopped it booting properly. I have neither of these network daemons running (network-manager or wicd).

You'd think there would be such an easy to use terminal utility for connecting to wireless access points. But I'm unable to find any.

---

### Post by chili555 on 2014-03-28
I suggest the far simpler arrangement for /etc/network/interfaces. I also suggest, so that you can ssh and ftp into the server, that you use a static IP address. I'd change /etc/network/interfaces to:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.20.100
netmask 255.255.255.0
gateway 192.168.20.1
wpa-ssid <your_router>
wpa-psk <your_secret_key>
dns-nameservers 8.8.8.8 192.168.20.1
```Of course, pick an address outside the DHCP pool in the router and substitute your details. Get the system to read and use the changes:

```
sudo ifdown wlan0 && sudo ifup wlan0

```
It may take a reboot.

---

### Post by Turbine1991 on 2014-03-29
Bingo, thanks it worked.

---

### Post by chili555 on 2014-03-29
Glad it's working. Please use thread tools at the top to mark Solved.

---


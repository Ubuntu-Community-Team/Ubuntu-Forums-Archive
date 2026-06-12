---
title: "wireless card associates with AP but does not get IP from DHCP"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by LordRaiden on 2006-10-04
I'm running kubuntu edgy with a custom kernel and madwifi-ng drivers from subversion. (Note I also tried the edgy kernel and madwifi in the restricted drivers but got the same result).

I am using KNetworkManager to manage the connection. I get all the way upto "57% IP Configuration" then the applet asks for my WPA password again. I tried using wpa_supplicant alone (killed all NetworkManager processes) and I get the same result.

iwconfig says that I am associated:

```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Frosted Flakes"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:A3:6A:25:E8
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:1B3B-6154-00D0-059E-19E5-BAC3-E138-DB3C   Security mode:restricted
          Power Management:off
          Link Quality=59/94  Signal level=-36 dBm  Noise level=-95 dBm
          Rx invalid nwid:5314  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

dhclient3
```
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:13:46:98:4e:ec
Sending on   LPF/ath0/00:13:46:98:4e:ec
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
receive_packet failed on ath0: Network is down
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I am highly against the idea of this being a driver problem since I can associate fine. Somewhere in the process (wpa_supplicant or dhclient) I can't get an IP. However, I also have an Ethernet connection with DHCP and I can get the connection fine. By the way, the card is a desktop (PCI) WLAN adapter - DLink DWL-G520.

Any help or direction will be greatly appreciated.

---

### Post by wieman01 on 2006-10-04
Have you installed a firewall (Firestarter) or any kind of wireless assistant (e.g. wifi-radar, wireless assistant) recently that possibly interfers with NetworkManager?

---

### Post by LordRaiden on 2006-10-04
Kubuntu Edgy comes with wlassistant (part of kubuntu desktop) but I am pretty sure it is not interfering (doesn't pop up or anything). I don't have any firewalls on the computer. I'm sort of at a loss because the set up did work with kernel 2.6.17-7 and 2.6.17-8, and both were using madwifi drivers from subversion.

---

### Post by wieman01 on 2006-10-04
If I were you I'd disable/uninstall wlassistant and try again. 

Could you also show us the contents of this file?
> sudo kwrite /etc/network/interfaces
Perhaps that's the problem.

---

### Post by LordRaiden on 2006-10-05
I got rid off wlassistant but it is the same.

/etc/network/interfaces - my wireless card is ath0
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.14
netmask 255.255.255.0
gateway 192.168.2.1
```

---

### Post by wieman01 on 2006-10-05
I'd edit your "interfaces" file so that it looks like this (2 lines only):
> auto lo
iface lo inet loopback
Either delete or uncomment the rest. What's the result?

---


---
title: "[SOLVED] Newbie cannot connect to Internet"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by eamann on 2006-08-03
Hello all!

I have just migrated from Windows and installed Kubuntu 6.06. My new-found enthusiasm has been dented by the problems I have encountered in trying to connect to Internet. I would be very grateful if someone could help me to understand the information below and suggest what I need to do to solve the problem(s). 

I have an Acer Travelmate 800 with an Intel Pro Wireless LAN 2100 3B and a Netopia router.

Thank you very much to whoever takes the time to read and reply!!!

Reply to iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Bealach runda"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Reply to “sudo pppoeconf”:

Sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond. Please    check your network and modem cables. Another reason for the scan failure may also be another running pppoe  process which controls the modem. 

 Reply to “dpkg -s pppoeconf”:

Package: pppoeconf
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 308
Maintainer: Debian QA Group <packages@qa.debian.org>
Architecture: all
Version: 1.8ubuntu2
Depends: whiptail-provider | whiptail, ppp (>= 2.4.2+20040428-2) | pppoe (>= 3.0), ppp (>= 2.4.1.uus2-4), gettext-base (>= 0.13), sed (>= 3.95)
Recommends: locales
Suggests: xdialog
Description: configures PPPoE/ADSL connections
 Userfriendly tool for initial configuration of a DSL (PPPoE) connection.

Reply to dhclinet:

Listening on LPF/eth1/00:04:23:59:3b:99
Sending on   LPF/eth1/00:04:23:59:3b:99
Listening on LPF/eth0/00:c0:9f:28:13:18
Sending on   LPF/eth0/00:c0:9f:28:13:18
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database – sleeping.

Contents of etc/network/interfaces:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Bealach runda
wireless-key s:8c3e3103ec

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider

---


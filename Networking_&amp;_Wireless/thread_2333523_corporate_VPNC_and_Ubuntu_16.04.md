---
title: "corporate VPNC and Ubuntu 16.04"
date: 2016-08-10
forum: Networking &amp; Wireless
---

### Post by capn.caveman on 2016-08-10
I've got a Lenovo W520, i'm trying to connect to a cisco VPN with it and having no luck at all.  I had this working on an older version of ubuntu (can't remember which version now) but it stopped after an upgrade.

Intel Corporation Centrino Advanced-N 6205
Ubuntu 16.04 LTS 64-bit

I have tried vpnc and network-manager-vpnc with no luck.  

here's the syslog output when i attempt vpnc:
> Aug 10 20:41:53 lenovo-laptop NetworkManager[6583]: <info>  [1470876113.6420] manager: (tun0): new Tun device (/org/freedesktop/NetworkManager/Devices/4)
Aug 10 20:41:53 lenovo-laptop NetworkManager[6583]: <info>  [1470876113.6460] devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 10 20:41:53 lenovo-laptop NetworkManager[6583]: <info>  [1470876113.6460] device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Aug 10 20:41:57 lenovo-laptop NetworkManager[6583]: <info>  [1470876117.4490] devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 10 20:41:57 lenovo-laptop gnome-session[1615]: Gjs-Message: JS LOG: Removing a network device that was not added


here's the syslog output from gnome UI
> Aug 10 20:44:16 lenovo-laptop NetworkManager[6583]: <info>  [1470876256.8371] audit: op="connection-activate" uuid="8a4cd773-de03-4a06-96b5-f219228abcc5" name="VPN 1" pid=1791 uid=1000 result="success"
Aug 10 20:44:16 lenovo-laptop NetworkManager[6583]: <info>  [1470876256.8402] vpn-connection[0x26d35d0,8a4cd773-de03-4a06-96b5-f219228abcc5,"VPN 1",0]: Saw the service appear; activating connection
Aug 10 20:44:41 lenovo-laptop NetworkManager[6583]: <error> [1470876281.9637] vpn-connection[0x26d35d0,8a4cd773-de03-4a06-96b5-f219228abcc5,"VPN 1",0]: Failed to request VPN secrets #3: No agents were available for this request.

From the log output the UI seems more successful but it still doesn't connect.  Any help or advice would be greatly appreciated...

ah also, and i dont know if this is helpful info or just noise, but i needed libgcrypt11 for some applications i need for work so i installed some random package off the internet.  good news is, eclipse and brackets work fine.  i dont know if it would impact vpn or not.  it didn't work before i installed all that either but i didn't capture logs before.  

Thanks
Capn'

---


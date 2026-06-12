---
title: "Can't create WiFi access point"
date: 2023-10-11
forum: Networking &amp; Wireless
---

### Post by dikh2 on 2023-10-11
Good day.
I got Orange Pi3 LTS and it's running Ubuntu 22.04.3 LTS.
I want to be my Orange Pi3 LTS good old wifi hotspot. But it seems nearly impossible.
```
orangepi3-lts:~$ nmcli con show
NAME                UUID                                  TYPE      DEVICE
Wired connection 1  e0dab8d3-b9a2-3762-b775-d192d19347c4  ethernet  enx667b3b7eab28
Wired connection 2  9aada3a9-dd92-3502-b9c4-7e5e5a131529  ethernet  eth0
Hotspot             93a3024d-8bf7-4128-87c0-1b157c6fabba  wifi      --
Hotspot-1           49338ae9-7647-48bf-b805-162c71ed2f28  wifi      --
Ifupdown (wlan0)    5391eba4-6426-faca-338e-5828034ff9d1  ethernet  --
SNR_Router           9b6ad970-785b-40cb-b8d6-d088ee09480b  wifi      --

```
and
```
h@orangepi3-lts:~$ nmcli d
DEVICE           TYPE      STATE         CONNECTION
enx667b3b7eab28  ethernet  connected     Wired connection 1
eth0             ethernet  connected     Wired connection 2
wlan0            wifi      disconnected  --
p2p-dev-wlan0    wifi-p2p  disconnected  --
lo               loopback  unmanaged     --

```
I try to create connection point, but got this message:
```
@orangepi3-lts:~$ nmcli d wifi hotspot ifname wlan0 ssid MyAP password 12345678Error: Connection activation failed: (11) 802.1X supplicant took too long to authenticate.

```
I try a lot, last two solutions were [https://variwiki.com/index.php?title=Wifi_NetworkManager#Configuring_WiFi_Access_Point](https://variwiki.com/index.php?title=Wifi_NetworkManager#Configuring_WiFi_Access_Point) and [https://askubuntu.com/a/180734/1736439](https://askubuntu.com/a/180734/1736439), no result at all. "sudo journalctl -xe NM_DEVICE=wlan0" give me next:
```
Oct 11 15:12:45 orangepi3-lts NetworkManager[783]: <info>  [1697037165.5267] device (wlan0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')Oct 11 15:12:46 orangepi3-lts NetworkManager[783]: <info>  [1697037166.0391] device (wlan0): Activation: starting connection 'SNR_Dima' (9b6ad970-785b-40cb-b8d6-d088ee09480b)
Oct 11 15:12:46 orangepi3-lts NetworkManager[783]: <info>  [1697037166.0395] device (wlan0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Oct 11 15:12:46 orangepi3-lts NetworkManager[783]: <info>  [1697037166.0409] device (wlan0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Oct 11 15:12:46 orangepi3-lts NetworkManager[783]: <info>  [1697037166.0418] device (wlan0): Activation: (wifi) access point 'SNR_Dima' has security, but secrets are required.
Oct 11 15:12:46 orangepi3-lts NetworkManager[783]: <info>  [1697037166.0419] device (wlan0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Oct 11 15:12:46 orangepi3-lts NetworkManager[783]: <info>  [1697037166.0426] sup-iface[525a2e8593c56e64,0,wlan0]: wps: type pbc start...
Oct 11 15:12:46 orangepi3-lts NetworkManager[783]: <info>  [1697037166.0463] device (wlan0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Oct 11 15:12:46 orangepi3-lts NetworkManager[783]: <info>  [1697037166.0476] device (wlan0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Oct 11 15:12:46 orangepi3-lts NetworkManager[783]: <info>  [1697037166.0488] device (wlan0): Activation: (wifi) connection 'SNR_Dima' has security, and secrets exist.  No new secrets needed.
Oct 11 15:13:11 orangepi3-lts NetworkManager[783]: <warn>  [1697037191.5202] device (wlan0): Activation: (wifi) association took too long, failing activation
Oct 11 15:13:11 orangepi3-lts NetworkManager[783]: <info>  [1697037191.5204] device (wlan0): state change: config -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')

```
Is it any way to deal with this problem?

---


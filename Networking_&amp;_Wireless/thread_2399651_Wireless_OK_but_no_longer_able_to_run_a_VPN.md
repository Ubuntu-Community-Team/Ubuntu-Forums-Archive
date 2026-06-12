---
title: "Wireless OK but no longer able to run a VPN"
date: 2018-08-28
forum: Networking &amp; Wireless
---

### Post by isagarran2 on 2018-08-28
Ubuntu 16.04 / Mobility connect
Freebox as router and as Wireless endpoint (network 192.168.**0**.XX) then a firewall/switch that act as a gateway (network 192.168.**1**.xx wired network 192.168.**1**.9 is the gateway)
Note that this problem occurs with other wireless network. I don't think it is related to my wireless network configuration.

Hello 

I worked on this problem during a long time and I need your advices and help.

I think I did something wrong on mly wireless connection. On my ethernet connection, I didn't have any problem to open a VPN using Mobility connect.
I did some changes on Network Manager, requested by a new implementation of VPN (with certificates that don't work for now). they requested to set DNS servers and domain names.
[LIST]
[*]I added a list of dns servers in a file in /etc/NetworkManager/dnsmasq.d/
[*]I added domain names in /etc/network/interfaces
[/LIST]
These modifications seem to work as I didn't encounter resolution names or IP problems on the VPN with certificates. I have other problems but it is another story.

I don't know if these changes are related or not but using my Wireless connection , I'm unable to start my standad VPN that works fine before.

the main message that I saw from the logs is:
```
4038060864 : device : (2018-08-27 / 21:45:00.784010) : wg_ip_lan_net_mgr_set_conn_mgr_addr: the gw_addr is 0.0.0.0
4038060864 : device : (2018-08-27 / 21:45:00.784123) : wg_ip_lan_dev_connect: The resolved gateway addr is 0.0.0.0.  Not a vaild IP address fail the interface open.


```

route -n seems strange but why not, I'm not a specialist of that.
```
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    600    0        0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp4s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0

```

I ran a command wireless_info and I got the file wireless-info.txt.bak
[ATTACH]280872[/ATTACH]

I took the syslog, wc.log (mobility connect log) and at the end a small trace about mobility connect. They show all the same error
[ATTACH]280873[/ATTACH]

I hope, this will help to understand why my connection is failing.

The same VPN running on Ethernet wired connection runs fine. In this case, route -n is very different

```
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
0.0.0.0         192.168.1.9     0.0.0.0         UG    100    0        0 enp0s31f6
3.129.160.0     9.167.232.1     255.255.255.0   UG    0      0        0 wc0
9.0.0.0         9.167.232.1     255.0.0.0       UG    0      0        0 wc0
9.167.232.0     0.0.0.0         255.255.252.0   U     0      0        0 wc0
12.120.243.0    9.167.232.1     255.255.255.240 UG    0      0        0 wc0
12.120.243.114  9.167.232.1     255.255.255.255 UGH   0      0        0 wc0
12.120.243.118  9.167.232.1     255.255.255.255 UGH   0      0        0 wc0
12.120.243.119  9.167.232.1     255.255.255.255 UGH   0      0        0 wc0
12.120.255.64   9.167.232.1     255.255.255.192 UG    0      0        0 wc0
....
with more lines
...

```
Any help would be veray appreciated
Isagarran

---

### Post by isagarran2 on 2018-08-31
Hello

Very strange,  I continued investigations
here are the network I have and the associated netstat -rn
```

**Wifi 1 SSID=jpsWireless**
jps@HanaYoriDango:/media/jps$ netstat -rn
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic   MSS Fenêtre irtt Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG        0 0          0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlp4s0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlp4s0


**wifi 2 SSID=jps_wireless**
jps@HanaYoriDango:/media/jps$ netstat -rn
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic   MSS Fenêtre irtt Iface
0.0.0.0         192.168.1.9     0.0.0.0         UG        0 0          0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlp4s0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlp4s0


**Wired network **(same vlan as wifi 2  = 192.168.1.xx)
jps@HanaYoriDango:/media/jps$ netstat -rn
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic   MSS Fenêtre irtt Iface
0.0.0.0         192.168.1.9     0.0.0.0         UG        0 0          0 enp0s31f6
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 enp0s31f6
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 enp0s31f6

```

Wifi 1 is the wireless provided by my Internet provider (Freebox) and Wifi2 is the wireless provided by my Firewall/switch

Using Wifi 1, iPhone or other wireless network. I failed to connect my VPN
Using  Wifi 2 and wired network, I'm succesful establishing the VPN.

Any ideas ?
Isagarran

---


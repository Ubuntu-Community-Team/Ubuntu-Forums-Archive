---
title: "Gateway on Ubuntu server 14.04.2 LTS + Hostapd"
date: 2015-05-04
forum: Networking &amp; Wireless
---

### Post by Esmertec on 2015-05-04
[COLOR=#000000]*Hi!*[/COLOR]
[COLOR=#000000]*I want to create a wi-fi access point in the ubuntu server 14.04, ubuntu was originally used as a gateway, so that it is configured nat + dnsmasq + squid3, and it worked fine! But it took the support wi-fi AP, so I installed in the PC wi-fi adapter TP-Link TL-WN851nd and install the package hostapd then configures the settings, but the point is not working ... On your PC, smartphone and it can be seen at certain points but connect to it can not be ... then the point is lost ..please help me! *[/COLOR]
[COLOR=#000000][I]
[/I][/COLOR]```
administrator@ubuntu-server:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:1c:c0:7f:76:5d
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe7f:765d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7484 (7.4 KB)  TX bytes:1164 (1.1 KB)


eth0      Link encap:Ethernet  HWaddr 00:1c:c0:7f:76:5d
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13610 (13.6 KB)  TX bytes:2372 (2.3 KB)


eth1      Link encap:Ethernet  HWaddr 00:e0:41:28:0e:68
          inet addr:192.168.1.146  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:41ff:fe28:e68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84028 errors:4 dropped:90 overruns:4 frame:0
          TX packets:20315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:122323497 (122.3 MB)  TX bytes:1441520 (1.4 MB)


lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:30293 (30.2 KB)  TX bytes:30293 (30.2 KB)


wlan0     Link encap:Ethernet  HWaddr c4:6e:1f:c0:d6:21
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1297 (1.2 KB)  TX bytes:2766 (2.7 KB)

```

```
administrator@ubuntu-server:~$ iwconfig
br0       no wireless extensions.


wlan0     IEEE 802.11bgn  Mode:Master  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


lo        no wireless extensions.


eth0      no wireless extensions.


eth1      no wireless extensions.

```

```
nano /etc/hostapd/hostapd.conf
interface=wlan0
bridge=br0
driver=nl80211
logger_syslog=-1
logger_syslog_level=0
logger_stdout=-1
logger_stdout_level=2
dump_file=/tmp/hostapd.dump
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
ssid=UBUNTU.WLAN
hw_mode=g
channel=6
beacon_int=100
dtim_period=2
max_num_sta=20
rts_threshold=2347
fragm_threshold=2346
preamble=1
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wmm_enabled=1
wmm_ac_bk_cwmin=4
wmm_ac_bk_cwmax=10
wmm_ac_bk_aifs=7
wmm_ac_bk_txop_limit=0
wmm_ac_bk_acm=0
wmm_ac_be_aifs=3
wmm_ac_be_cwmin=4
wmm_ac_be_cwmax=10
wmm_ac_be_txop_limit=0
wmm_ac_be_acm=0
wmm_ac_vi_aifs=2
wmm_ac_vi_cwmin=3
wmm_ac_vi_cwmax=4
wmm_ac_vi_txop_limit=94
wmm_ac_vi_acm=0
wmm_ac_vo_aifs=2
wmm_ac_vo_cwmin=2
wmm_ac_vo_cwmax=3
wmm_ac_vo_txop_limit=47
wmm_ac_vo_acm=0
ieee80211n=1
ht_capab=[HT40+][SHORT-GI-40][DSSS_CCK-40][TX-STBC][RX-STBC1]
eapol_key_index_workaround=0
eap_server=0
own_ip_addr=127.0.0.1
wpa=2
wpa_passphrase=test1234
wpa_key_mgmt=WPA-PSK
wpa_pairwise=CCMP
rsn_pairwise=CCMP

```

```
~$ lspci | grep Network
04:03.0 Network controller: Qualcomm Atheros AR9227 Wireless Network Adapter (rev 01)
~$ lsmod | grep 80211
mac80211              545990  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211


```
[COLOR=#000000]*Thanks in advance for your reply!*[/COLOR]

---


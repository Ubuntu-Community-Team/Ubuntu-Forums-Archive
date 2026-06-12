---
title: "Dlink DWL-G650 disconnects all the time"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by Johtaja_K on 2007-03-07
Hi,

I'm using Compaq laptop where I have installed Ubuntu Egdy. After some miracle moves I got D-link DWL-G650 card to work. I'm using WPA connection, but the connection is disconnecting all the time?!? Connection stays up about 1-5 mins and I can use the internet, but then connection lost's and wlan starts to get a new connection?!? :confused:

Any ideas where to look up the problem?

Here is some information:
iwconfig:
```

ath0      IEEE 802.11g  ESSID:"KopiWebbi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:0A:7B:60
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/94  Signal level=-42 dBm  Noise level=-95 dBm
          Rx invalid nwid:4  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig:
```

ath0      Link encap:Ethernet  HWaddr 00:13:46:6E:1F:D6
          inet addr:192.168.0.183  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe6e:1fd6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:88 dropped:0 overruns:0 frame:88
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:4758 (4.6 KiB)  TX bytes:5556 (5.4 KiB)
          Interrupt:11 Memory:dfb00000-dfb10000

```

lcpci:
```

0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
0000:00:0c.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
0000:02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

---

### Post by spd106 on 2007-03-07
Do you have wifi-radar installed? It plays havoc with my DWL-G650. Network Manager is far better, when it finally connects.

Could you provide a bit more information, such as what you're using to configure it with and any other software you've installed that might be conflicting.

---

### Post by Johtaja_K on 2007-03-07
> **spd106 said:**
> Do you have wifi-radar installed? It plays havoc with my DWL-G650. Network Manager is far better, when it finally connects.

Could you provide a bit more information, such as what you're using to configure it with and any other software you've installed that might be conflicting.

I have wifi-rader installed, but can't make connection through that. :( 

What kind of information do you want? 

If I remember correct, I updated Network-manager to 0.6.2 and set up the connection and wolaa, it start to work. :)

---

### Post by spd106 on 2007-03-07
If you're not using wifi-rader then I suggest that you uninstall it. 

When I used it a while ago on Dapper I remember it has a background daemon that messed with Network Manager. I might be wrong as I've not used it since then.

---

### Post by Johtaja_K on 2007-03-08
> **spd106 said:**
> If you're not using wifi-rader then I suggest that you uninstall it.

No help. Problem continues.. ](*,)

---

### Post by watson540 on 2007-03-08
your iwconfig output doesnt mention anything about encryption being used but you said you use wpa, thats your problem, it sees the router fine but the router aint lettin you log in?? just a guess i never used wpa though but i know with wep iwconfig will show your encryption key. its wierd though cause you say it lets you on the net for a few minutes.
check output of dmesg. also look in /var/log/syslog and all the other logs in /var/log

---

### Post by spd106 on 2007-03-08
Try starting wpa_supplicant from a terminal and watch for problems. See the wpa sticky and this wiki page for help configuring [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---


---
title: "Wifi unable to connect, but can list (ipw2200)"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by rixxon on 2006-09-06
Hello, I'm having problems with wifi on my laptop. It all works fine on Windows, so the hardware is not broken... On dapper, however, I can't connect to any SSID. I can list networks and sniff some traffic, though.

```
sudo lshw -C network
```
>   *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@06:04.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:64:72:5a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.1 firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=unassociated
       resources: iomemory:b0107000-b0107fff irq:169

```
lspci -v |grep Ethernet
```
> 0000:06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```
lsmod |grep ipw2200
```
> ipw2200               107308  0
ieee80211              37064  1 ipw2200

```
cat /etc/modules
```
> [...]
ipw2200

```
iwlist eth1 scanning
```
> eth1      Scan completed :
          Cell 01 - Address: 00:0F:B5:E5:D9:40
                    ESSID:"TPGnet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=31/100  Signal level=-81 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 248ms ago
[...six more cells...]

kismet also works fine. But I just can't connect to any AP. I never get any IP from DHCP... Any ideas?

---

### Post by wieman01 on 2006-09-06
Could you post the content of "/etc/network/interfaces" please? I am using IPW2200 with WPA2 enabled so I might be able to help you out. You're very close.

Is this a WEP-secured network you are trying to connect to?

---

### Post by rixxon on 2006-09-06
I was asked to remove "auto" for each except "lo", when attempting to install NetworkManager. Didn't work, and I made no backup, so i just added auto for every "abcX" line... Not sure if it is right.

I've tried both WPA and WEP networks. Can't even connect to networks without a key!

Anyways, here's /etc/network/interfaces:

> auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





auto eth0

iface eth1 inet dhcp
wireless-essid gymn
wireless-key s:(secret!)

auto eth1


---

### Post by wieman01 on 2006-09-06
Alright, let's tidy up your interfaces file first of all:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid **your_essid**
wireless-key **your_wep_key**

Replace "your_essid" with your network's SID and provide a WEP key ("your_wep_key") given by the router. If you don't need security (i.e. WEP) then delete the last line.

I take it you are using DHCP, correct?

To play safe, restart the computer and see how it goes. What does "iwconfig" say after rebooting?

---

### Post by carlo bolzonello on 2006-09-06
guys,

i am comming in to this late, however i have a similar issue with a netgear wg511t pcmcia card. i can see it, however it wont connect to my network.any ideas please

---

### Post by wieman01 on 2006-09-06
> **carlo bolzonello said:**
> guys,

i am comming in to this late, however i have a similar issue with a netgear wg511t pcmcia card. i can see it, however it wont connect to my network.any ideas please

It's never too late... 

Just check out what we are doing here. Should work for you as well.

---

### Post by carlo bolzonello on 2006-09-06
thanks very much, im new at the whole linux world thing. ill keep a eye on what you say and ill see where we go. I downloaded a file called madwifi the otherday, teh instructions where very shoddy, do i need it still?

onc eagain thanks, and pleas ebe patient, im a windows user trying out this for the first time, and i must say im feeling "hooked"

---

### Post by wieman01 on 2006-09-06
> **carlo bolzonello said:**
> thanks very much, im new at the whole linux world thing. ill keep a eye on what you say and ill see where we go. I downloaded a file called madwifi the otherday, teh instructions where very shoddy, do i need it still?

No problem. Has your wireless card been recognized? Just run "ifconfig" in a terminal and see if it shows up there.

---

### Post by carlo bolzonello on 2006-09-06
ip did not work as command, however i ha a screenshot of my current config

---

### Post by wieman01 on 2006-09-06
> **carlo bolzonello said:**
> ip did not work as command, however i ha a screenshot of my current config

Hi, could you open another thread? Otherwise it will complicate things in here. Thanks, buddy? Please send me the link to the new thread.

BTW: Good news is that your wireless card seems to be recognized by the system.

---

### Post by carlo bolzonello on 2006-09-06
[http://www.ubuntuforums.org/showthread.php?p=1469221#post1469221](http://www.ubuntuforums.org/showthread.php?p=1469221#post1469221)

here it is :) thanks a million

---

### Post by rixxon on 2006-09-06
```
eth1      unassociated  ESSID:"TottiNet"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Didn't work. eth1 doesn't even show up in "Connection Properties". Tried setting it to "Default gateway device" in "Network settings" but it still didn't show up. Also noticed that "Key type" for "Wireless connection Interface properties" was set to "Hexadecimal" while I wrote it in plain text in the interfaces file.

---

### Post by wieman01 on 2006-09-06
Mmm... Can you also run "ifconfig" and post the output? A screenshot of your "connection properties" would be helpful as well.

---

### Post by wieman01 on 2006-09-06
BTW: They key needs to be in "Hexadecimal"... (can also be in plain text but then you need to add a prefix, let's talk about that later).

---

### Post by rixxon on 2006-09-06
OK, set the key in hex and rebooted. Still doesn't work.

```
rixxon@erythro:~$ iwconfig eth1
eth1      unassociated  ESSID:"TottiNet"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rixxon@erythro:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:12:F0:64:72:5A
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0x4000 Memory:b0107000-b0107fff

```

And eth1 still didn't even show up in the Connection Properties list.

---

### Post by wieman01 on 2006-09-06
Eth1 does show in the "network settings". It appears it's up & running, however, are you sure your router is set to WEP? And is DHCP correct as well?

Perhaps post your interfaces file so that I can validate it.

---

### Post by rixxon on 2006-09-06
TottiNet is using WPA-PSK TKIP.

---

### Post by wieman01 on 2006-09-06
Oh... in that case you'll have to user NetworkManager to configure it. Or follow the last page of this thread (WPA-PSK). This should work.

Sadly you cannot configure a WPA network using the standard GNOME tools. You'll have to do it either manually (see thread) or by using NetworkManager (which has certain restrictions).

[http://www.ubuntuforums.org/showthread.php?t=225290&page=11&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=225290&page=11&highlight=wpa2+rsn")

Check it out... I'll continue to help tomorrow if you want to go for the manual approach (which is editing the "interfaces" file).

---

### Post by rixxon on 2006-09-06
So how would i get NetworkManager working and what are the restrictions you're talking about?

---

### Post by rixxon on 2006-09-06
Got NetworkManager working myself, don't ask me how... I've never been this happy in my whole life, linux + wifi is sweet! Thanks for the help.

---

### Post by wieman01 on 2006-09-06
Just to answer your question... NetworkManager has the following constraints:

1. No static IPs.
2. ESSIDs cannot be hidden
3. Cannot connect to unsecured networks

Good to learn it works for you. :-)

---


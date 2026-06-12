---
title: "Intel 4965 and Kubuntu 8.04 (Hardy Heron)"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by nymphnode on 2008-06-08
Hi,
I know there are loads of posts on this, but I can't get my wireless to work on my Dell Inspiron 9400 which has the following wireless network card:

$ lspci -v | grep Wireless
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1121
        Flags: bus master, fast devsel, latency 0, IRQ 219
        Memory at ecffe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

The driver I'm using is iwlwifi-1.0.0-1. The wireless net has an ASCII WEP key.


$ iwconfig
wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


When I do
$ sudo iwlist wlan0 scan

I do get a list of available networks, including the own I want to connect to. I also installed WiFi Radar, which gives me a list of available networks, too. But I'm not getting an IP....

Is this a driver problem? HELP!!!


Thanks

---

### Post by chili555 on 2008-06-08
> Is this a driver problem?Doubtful. Can you connect manually? Open a terminal and do:```
sudo iwconfig wlan0 essid <ur_router>
sudo iwconfig wlan0 key **s:**<ur_ascii_key>
sudo dhclient wlan0
```Do you connect?

---

### Post by nymphnode on 2008-06-09
Yes it worked!!!! THANK YOU THANK YOU THANK YOU, chili555

I had tried the iwconfig command with "key s:" before but not in the sequence of commands you listed.

Thanks again

---

### Post by Gun_Smoke on 2008-08-09
I get the error after trying the above with..
```

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:5c:02:76:61
Sending on LPF/wlan0/00:21:5c:02:76:61
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Any ideas?  It would be attempting to connect to Airport Extreme.

---

### Post by hrodriguez231 on 2008-08-22
> **nymphnode said:**
> Hi,
I know there are loads of posts on this, but I can't get my wireless to work on my Dell Inspiron 9400 which has the following wireless network card:

The driver I'm using is iwlwifi-1.0.0-1. The wireless net has an ASCII WEP key.


$ iwconfig
wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm


When I do
$ sudo iwlist wlan0 scan

I do get a list of available networks, including the own I want to connect to. I also installed WiFi Radar, which gives me a list of available networks, too. But I'm not getting an IP....

Is this a driver problem? HELP!!!


Thanks

I have a question regarding your post, because I saw your **txpower** is 27dBm, don't understand why or how you could reach that txpower because that card like Intel 2200 (ipw2200) the max. output power is 20dBm, can you explained if that 27dBm is true???

Thanks in advance.
Hector.

---


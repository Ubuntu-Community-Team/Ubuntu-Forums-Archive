---
title: "Network manager WEP and HEX key"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by Cutecumber on 2015-02-18
Hey guys,

I've got problems connecting WIFI network using only HEX key. 

Here is the situation:

1) While connecting with ASCII passphrase, everything works well ( DHCP, internet connection,.. )
2) While I try to connect with HEX key, network manager shows "Disconnected" after a while.

So I've tried:
Search for solutions on forums
Connect to WIFI using command line ( [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) ) nothing happend
Set static IP and GW - This is interesting, because network manager shows "Connected to...", but I cant ping GW or connect to the internet ( Double-checked the IPs )
Test more WEP networks with the same result ( ASCII works, HEX, doesn't )
Connect with Windows 7 and HEX key. This is actually working well.
Conect with another WIFI adapter

Can you please help?

Thank you!

---

### Post by steeldriver on 2015-02-18
Hello and welcome to the forums

Are there any helpful messages in the dmesg log after the disconnections? for example if you open a terminal and run

```

dmesg | grep wlan | tail

```

(you may need to change the 'wlan' to something else if your network interfaces do not follow the standard naming scheme)

---

### Post by chili555 on 2015-02-18
I hate to step on toes and steeldriver is tied for the best networking guru we have here, but WEP is about as secure as putting all your money that should be in the bank, instead, in a shoebox on the front porch. I suggest you change your encryption to WPA2-AES immediately.

---

### Post by Cutecumber on 2015-02-18
dmesg | grep wlan1 | tail

[23848.353360] wlan1: authenticate with 00:13:f7:de:d7:53
[23848.776600] wlan1: direct probe to 00:13:f7:de:d7:53 (try 1/3)
[23848.979967] wlan1: send auth to 00:13:f7:de:d7:53 (try 2/3)
[23848.989743] wlan1: authenticated
[23848.990011] ath9k_htc 3-3:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[23848.990018] ath9k_htc 3-3:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[23848.990021] ath9k_htc 3-3:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[23848.991946] wlan1: associate with 00:13:f7:de:d7:53 (try 1/3)
[23849.001133] wlan1: RX AssocResp from 00:13:f7:de:d7:53 (capab=0x431 status=0 aid=2)
[23849.010717] wlan1: associated

But it keeps disconnecting and connecting again..




While connecting with manual IP:
23616.808097] wlan1: direct probe to 00:13:f7:de:d7:53 (try 1/3)
[23617.011168] wlan1: direct probe to 00:13:f7:de:d7:53 (try 2/3)
[23617.215071] wlan1: send auth to 00:13:f7:de:d7:53 (try 3/3)
[23617.219556] wlan1: authenticated
[23617.219828] ath9k_htc 3-3:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[23617.219835] ath9k_htc 3-3:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[23617.219838] ath9k_htc 3-3:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[23617.223046] wlan1: associate with 00:13:f7:de:d7:53 (try 1/3)
[23617.235655] wlan1: RX AssocResp from 00:13:f7:de:d7:53 (capab=0x431 status=0 aid=2)
[23617.245334] wlan1: associated

---

### Post by steeldriver on 2015-02-18
Thanks chili555 - you are absolutely correct (**except** for the part about me being a networking guru lol) - WEP should be avoided of course

---

### Post by Cutecumber on 2015-02-18
Thank you for your recommendation. I know that WEP is obsolete and insecure... But ubuntu users should still be able to connect to it.

---

### Post by Cutecumber on 2015-02-19
I've tried it again and also used another drivers from backports... I'am close to the AP, so there shouldn't be problems with distance and interferences..

lsusb:

Bus 003 Device 004: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n

sudo lshw -C network  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@3:3
       logical name: wlan1
       serial: e8:de:27:12:73:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.13.0-45-generic firmware=1.3 link=no multicast=yes wireless=IEEE 802.11bgn

dmesg | grep wlan1 | tail
[ 1348.151831] wlan1: send auth to 00:13:f7:de:d7:53 (try 3/3)
[ 1348.153873] wlan1: authenticated
[ 1348.154175] ath9k_htc 3-3:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[ 1348.154182] ath9k_htc 3-3:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[ 1348.154185] ath9k_htc 3-3:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[ 1348.155802] wlan1: associate with 00:13:f7:de:d7:53 (try 1/3)
[ 1348.168557] wlan1: RX AssocResp from 00:13:f7:de:d7:53 (capab=0x431 status=0 aid=3)
[ 1348.178371] wlan1: associated
[ 1348.178435] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1393.580960] wlan1: deauthenticating from 00:13:f7:de:d7:53 by local choice (reason=3)

As you can see, if I set the network manager to automatic ( DHCP ) link is established. But it's automatically closed.

Thank you for your help.

---

### Post by steeldriver on 2015-02-19
Maybe try disabling IPv6? (edit connection --> IPv6 --> 'Ignore')

---

### Post by chili555 on 2015-02-19
> [ 1348.154175] ath9k_htc 3-3:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[ 1348.154182] ath9k_htc 3-3:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[ 1348.154185] ath9k_htc 3-3:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the API hope this is helpful: [http://ubuntuforums.org/showthread.php?t=2244010](http://ubuntuforums.org/showthread.php?t=2244010)

---

### Post by Cutecumber on 2015-02-21
Thank you for your help guys. Disabling the ipv6 did the trick...

---


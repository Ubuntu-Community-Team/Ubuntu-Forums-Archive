---
title: "Wireless problems under 8.04 and B43: protected netword unstable"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by Lead Expression on 2008-05-09
Hi
I've a problem with my Broadcom Card under Ubuntu 8.04 with B43 drivers
At university we have a Wi-Fi protected line for access to the net. Obviously, the staff can't say me how to configure the connection, so I deduced the parameters from Windows XP instructions:

WPA/PEAP
TKIP
EAP MSCHAPV2
username
password
no automatic reconnection

When the network is recognized, the connections started. The signal is strong

```
$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:16:9D:44:ED:90
                    ESSID:"Wi-Fi_UniNa"
                    Mode:Master
                    Channel:13
                    Frequency:2.472 GHz
                    Quality=61/100  Signal level=-46 dBm  Noise level=-72 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : Proprietary 802.1x
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000058ac498f6

```

I set security as WPA Business (I think is in english), key type TKIP, Phase2 Type MSCHAPV2, username, password. So I'm connected, but connection is terribly unstable. Signal is high but I've only 31% of signal. Sometimes, iwlist scan tells me 58% of signal but network manager 0%, sometimes with 35% of signal I can't access the net, sometimes, after a few minutes with 0% of signal, it disconnect, trying to reconnect asking me password (without asking some other times) and reconnect.
Wi-Fi card works properly 'cause I can access other network without a problem
Wi-Fi network works properly 'cause my friend can access network under Windows XP or MacOS
Password and username are correct.
I've tried to set key type and Phase2 type to default in many combination, but nothing happens.
I remember that, before installing 8.04, network works fine with ndiswrapper (a little more unstable as in Windows, but worked) so I think it can be a driver problem, maybe a incompatibility or an unsupported type of communication... I don't know...

This is what I read typing dmesg. I don't understand where can be the problem. This cover the intervarl from connection to automatic disconnection.

```
[   65.561350] wlan0: Initial auth_alg=0
[   65.561362] wlan0: authenticate with AP 00:16:c7:44:13:80
[   65.562635] wlan0: RX authentication from 00:16:c7:44:13:80 (alg=0 transaction=2 status=0)
[   65.562642] wlan0: authenticated
[   65.562645] wlan0: associate with AP 00:16:c7:44:13:80
[   65.564366] wlan0: authentication frame received from 00:16:c7:44:13:80, but not in authenticate state - ignored
[   65.567154] wlan0: authentication frame received from 00:16:c7:44:13:80, but not in authenticate state - ignored
[   65.572904] wlan0: RX AssocResp from 00:16:c7:44:13:80 (capab=0x431 status=0 aid=74)
[   65.572912] wlan0: associated
[   65.572918] wlan0: switched to short barker preamble (BSSID=00:16:c7:44:13:80)
[   65.572962] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   65.572965] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   65.572968] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   65.572972] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   65.574485] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   65.577675] wlan0: association frame received from 00:16:c7:44:13:80, but not in associate state - ignored
[   76.408954] wlan0: Initial auth_alg=0
[   76.408965] wlan0: authenticate with AP 00:16:9d:44:ed:90
[   76.607056] wlan0: authenticate with AP 00:16:9d:44:ed:90
[   76.810785] wlan0: authenticate with AP 00:16:9d:44:ed:90
[   77.010604] wlan0: authentication with AP 00:16:9d:44:ed:90 timed out
[   78.948889] wlan0: no IPv6 routers present
[   81.735050] wlan0: Initial auth_alg=0
[   81.735058] wlan0: authenticate with AP 00:16:9d:44:ed:90
[   81.836330] wlan0: authenticate with AP 00:16:9d:44:ed:90
[   81.938244] wlan0: authenticate with AP 00:16:9d:44:ed:90
[   82.038290] wlan0: authentication with AP 00:16:9d:44:ed:90 timed out
[   85.266187] wlan0: Initial auth_alg=0
[   85.266196] wlan0: authenticate with AP 00:16:9d:44:ed:90
[   85.266220] wlan0: Initial auth_alg=0
[   85.266224] wlan0: authenticate with AP 00:16:c7:44:13:80
[   85.269726] wlan0: RX authentication from 00:16:c7:44:13:80 (alg=0 transaction=2 status=0)
[   85.269731] wlan0: authenticated
[   85.269735] wlan0: associate with AP 00:16:c7:44:13:80
[   85.274133] wlan0: authentication frame received from 00:16:c7:44:13:80, but not in authenticate state - ignored
[   85.275688] wlan0: RX deauthentication from 00:16:c7:44:13:80 (reason=2)
[   85.275692] wlan0: deauthenticated
[   85.773752] wlan0: authenticate with AP 00:16:c7:44:13:80
[   85.775065] wlan0: RX authentication from 00:16:c7:44:13:80 (alg=0 transaction=2 status=0)
[   85.775071] wlan0: authenticated
[   85.775074] wlan0: associate with AP 00:16:c7:44:13:80
[   85.779980] wlan0: RX ReassocResp from 00:16:c7:44:13:80 (capab=0x431 status=0 aid=75)
[   85.779986] wlan0: associated
[   85.780050] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   85.780054] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   85.780057] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   85.780060] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   96.932052] wlan0: No ProbeResp from current AP 00:16:c7:44:13:80 - assume out of range
[  104.391116] wlan0: Initial auth_alg=0
[  104.391125] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  104.594469] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  104.798289] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  105.002107] wlan0: authentication with AP 00:16:9d:44:ed:90 timed out
[  109.537193] wlan0: Initial auth_alg=0
[  109.537203] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  109.738158] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  109.936471] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  110.136290] wlan0: authentication with AP 00:16:9d:44:ed:90 timed out
[  112.724755] wlan0: Initial auth_alg=0
[  112.724766] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  112.823922] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  112.923836] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  113.023744] wlan0: authentication with AP 00:16:9d:44:ed:90 timed out
[  115.679767] wlan0: Initial auth_alg=0
[  115.679775] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  115.680174] wlan0: Initial auth_alg=0
[  115.680178] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  115.781494] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  115.883404] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  115.985315] wlan0: authentication with AP 00:16:9d:44:ed:90 timed out
[  119.262030] wlan0: Initial auth_alg=0
[  119.262038] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  119.262217] wlan0: Initial auth_alg=0
[  119.262220] wlan0: authenticate with AP 00:16:9d:44:ed:90
[  119.361767] wlan0: authenticate with AP 00:16:9d:44:ed:90
```

Can someone help me?

Thank you

Nik

---


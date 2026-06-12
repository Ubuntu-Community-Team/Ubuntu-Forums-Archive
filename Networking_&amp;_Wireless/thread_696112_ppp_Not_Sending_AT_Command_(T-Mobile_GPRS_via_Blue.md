---
title: "ppp Not Sending AT Command (T-Mobile GPRS via Bluetooth and the P800)"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by bjc on 2008-02-13
I'm trying to connect to my Sony Ericsson P800 via Bluetooth for use as a GPRS modem. Yesterday I successfully connected to a Sony Ericsson W880 (on Vodafone UK), but try as I might to modify the config files, I can't get the P800 (on T-Mobile UK) to work. 

The error du jour is:

```

Feb 13 22:55:19 localhost hcid[11656]: link_key_request (sba=00:08:1B:05:91:5D, dba=00:0A:D9:5D:C8:93)
Feb 13 22:55:20 localhost chat[3074]: timeout set to 5 seconds
Feb 13 22:55:20 localhost chat[3074]: send (ATZ^M)
Feb 13 22:55:20 localhost chat[3074]: abort on (\nBUSY\r)
Feb 13 22:55:20 localhost chat[3074]: abort on (\nERROR\r)
Feb 13 22:55:20 localhost chat[3074]: abort on (\nNO ANSWER\r)
Feb 13 22:55:20 localhost chat[3074]: abort on (\nNO CARRIER\r)
Feb 13 22:55:20 localhost chat[3074]: abort on (\nNO DIALTONE\r)
Feb 13 22:55:20 localhost chat[3074]: abort on (\nRINGING\r\n\r\nRINGING\r)
Feb 13 22:55:20 localhost chat[3074]: send (^MAT^M)
Feb 13 22:55:20 localhost chat[3074]: timeout set to 45 seconds
Feb 13 22:55:20 localhost chat[3074]: expect (OK)
Feb 13 22:55:20 localhost chat[3074]: ^M
Feb 13 22:55:20 localhost chat[3074]: ERROR^M
Feb 13 22:55:20 localhost chat[3074]:  -- failed
Feb 13 22:55:20 localhost chat[3074]: Failed ( ERROR^M)
Feb 13 22:55:20 localhost pppd[3067]: Connect script failed

```

It appears that the AT command isn't being sent, hence the error message, but I can't see why. My config files have been kept as generic as possible, and I can't find reports of anybody else having this problem.

*/etc/ppp/peers/tmobile*
```

debug
noauth
connect '/usr/sbin/chat -v -f /etc/ppp/chat-tmobile'
usepeerdns
/dev/rfcomm1 115200
defaultroute
persist
noipdefault
nodetach
lcp-echo-failure 0
crtscts

```


*/etc/ppp/chat-tmobile*
```

TIMEOUT 5
ECHO ON
"" 'ATZ'
ABORT '\nBUSY\r'
ABORT '\nERROR\r'
ABORT '\nNO ANSWER\r'
ABORT '\nNO CARRIER\r'
ABORT '\nNO DIALTONE\r'
ABORT '\nRINGING\r\n\r\nRINGING\r'
''    \rAT
TIMEOUT 45
OK      'AT+CGDCONT=1,"IP","general.t-mobile.uk"'
OK ATD*99***1#
TIMEOUT 30
CONNECT ""

```

Any clues? :-)

---


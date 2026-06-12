---
title: "P900 GPRS modem with Kubuntu Edgy."
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by cloakable on 2007-04-16
Hi all.

I've got some access through KPPP on Kubuntu (modem gets initialised, dials out, and pppd connects me).
The output of KPPP while dialing is:
```

ATZ
OK
AT+CGDCONT=1,"IP","orangeinternet"
OK
ATM1L1
OK
ATDT*99***4#
CONNECT

```

I've tried making a /etc/ppp/peers/orange and /etc/chatscripts/orange ppp config, but the chatscript launches, seems to run fine (sets up the modem), but after, pppd just exits. I'd prefer to use this way, as it means my modem can be controlled by KNetworkManager.

Here is the contents of my /etc/ppp/peers/orange file:
```

/dev/ttyUSB0 115200
connect '/usr/sbin/chat -v -f /etc/chatscripts/orange
defaultroute
ipcp-no-addresses
noipdefault
debug
kdebug 4
usepeerdns
lcp-echo-interval 0

```

And the contents of my /etc/chatscripts/orange file:
```

ABORT BUSY
ABORT 'NO CARRIER'
ABORT VOICE
ABORT 'NO DIALTONE'
ABORT 'NO DIAL TONE'
ABORT 'NO ANSWER'
ABORT DELAYED
'' ATZ
OK AT+CGDCONT=4,"IP","orangeinternet"
OK ATM1L1
OK ATDT*99***4#
CONNECT ''

```

Here is the output of 'pon orange && tail -f /var/log/messages':
```

Apr 16 15:48:27 trancendence pppd[15831]: pppd 2.4.4 started by cloakable, uid 1000
Apr 16 15:48:28 trancendence chat[15834]: abort on (BUSY)
Apr 16 15:48:28 trancendence chat[15834]: abort on (NO CARRIER)
Apr 16 15:48:28 trancendence chat[15834]: abort on (VOICE)
Apr 16 15:48:28 trancendence chat[15834]: abort on (NO DIALTONE)
Apr 16 15:48:28 trancendence chat[15834]: abort on (NO DIAL TONE)
Apr 16 15:48:28 trancendence chat[15834]: abort on (NO ANSWER)
Apr 16 15:48:28 trancendence chat[15834]: abort on (DELAYED)
Apr 16 15:48:28 trancendence chat[15834]: send (ATZ^M)
Apr 16 15:48:28 trancendence chat[15834]: expect (OK)
Apr 16 15:48:28 trancendence chat[15834]: ATZ^M^M
Apr 16 15:48:28 trancendence chat[15834]: OK
Apr 16 15:48:28 trancendence chat[15834]:  -- got it
Apr 16 15:48:28 trancendence chat[15834]: send (AT+CGDCONT=4,"IP","orangeinterne                                                                                                  t"^M)
Apr 16 15:48:29 trancendence chat[15834]: expect (OK)
Apr 16 15:48:29 trancendence chat[15834]: ^M
Apr 16 15:48:29 trancendence chat[15834]: AT+CGDCONT=4,"IP","orangeinternet"^M^M
Apr 16 15:48:29 trancendence chat[15834]: OK
Apr 16 15:48:29 trancendence chat[15834]:  -- got it
Apr 16 15:48:29 trancendence chat[15834]: send (ATM1L1^M)
Apr 16 15:48:29 trancendence chat[15834]: expect (OK)
Apr 16 15:48:29 trancendence chat[15834]: ^M
Apr 16 15:48:29 trancendence chat[15834]: ATM1L1^M^M
Apr 16 15:48:29 trancendence chat[15834]: OK
Apr 16 15:48:29 trancendence chat[15834]:  -- got it
Apr 16 15:48:29 trancendence chat[15834]: send (ATDT*99***4#^M)
Apr 16 15:48:29 trancendence chat[15834]: expect (CONNECT)
Apr 16 15:48:29 trancendence chat[15834]: ^M
Apr 16 15:48:31 trancendence chat[15834]: ATDT*99***4#^M^M
Apr 16 15:48:31 trancendence chat[15834]: CONNECT
Apr 16 15:48:31 trancendence chat[15834]:  -- got it
Apr 16 15:48:31 trancendence chat[15834]: send (^M)
Apr 16 15:48:32 trancendence pppd[15831]: Exit.

```
Any help/advice would by appreciated greatly.

(EDIT - the reason for the KPPP errors was dhclient overwriting my resolv.conf. Fixed.)

---


---
title: "CHAP Authentication problem"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by bilbometal on 2008-06-03
I recently installed gutsy and I don't make any updates because I can get my wireless internet connection to work.
My wireless card uses rt61 module (it's a Ralink 2561 card) and the problem is:

To gain access to internet, I have to connect to a wireless network (that have a hidden essid) and then authenticate by a PPPoE connection with user and password.
I can connect to the hidden essid but there's a problem with the PPPoE authentication. Here's the log:

```

andre@andre-desktop:~$ pon dsl-provider debug dump logfd 2 nodetach
Plugin rp-pppoe.so loaded.
pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
persist         # (from /etc/ppp/peers/dsl-provider)
logfd 2         # (from command line)
dump            # (from command line)
plugin rp-pppoe.so              # (from /etc/ppp/peers/dsl-provider)
noauth          # (from /etc/ppp/peers/dsl-provider)
user valdenildo72               # (from /etc/ppp/peers/dsl-provider)
wlan0           # (from /etc/ppp/peers/dsl-provider)
wlan0           # (from /etc/ppp/peers/dsl-provider)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/peers/dsl-provider)
noipdefault             # (from /etc/ppp/peers/dsl-provider)
defaultroute            # (from /etc/ppp/peers/dsl-provider)
replacedefaultroute             # (from /etc/ppp/peers/dsl-provider)
proxyarp                # (from /etc/ppp/options)
usepeerdns              # (from /etc/ppp/peers/dsl-provider)
noipx           # (from /etc/ppp/options)
PADS: Service-Name: 'INCSET2'
PPP session is 109
using channel 5
Using interface ppp0
Connect: ppp0 <--> wlan0
sent [LCP ConfReq id=0x1 <mru 1492> <magic 0xb474b488>]
rcvd [LCP ConfReq id=0x1 <mru 1492> <auth chap MD5> <magic 0x895cd325>]
sent [LCP ConfAck id=0x1 <mru 1492> <auth chap MD5> <magic 0x895cd325>]
rcvd [LCP ConfAck id=0x1 <mru 1492> <magic 0xb474b488>]
sent [LCP EchoReq id=0x0 magic=0xb474b488]
rcvd [LCP EchoReq id=0x0 magic=0x895cd325]
sent [LCP EchoRep id=0x0 magic=0xb474b488]
rcvd [CHAP Challenge id=0xe7 <842974609a67f548163e5a7880d2cb935acb639f>, name = "inocoop"]
sent [CHAP Response id=0xe7 <47fc5638b74cd3a5a38ec5d9c11942d6>, name = "valdenildo72"]
rcvd [LCP EchoRep id=0x0 magic=0x895cd325]
rcvd [CHAP Challenge id=0xe7 <842974609a67f548163e5a7880d2cb935acb639f>, name = "inocoop"]
sent [CHAP Response id=0xe7 <47fc5638b74cd3a5a38ec5d9c11942d6>, name = "valdenildo72"]
rcvd [CHAP Challenge id=0xe7 <842974609a67f548163e5a7880d2cb935acb639f>, name = "inocoop"]
sent [CHAP Response id=0xe7 <47fc5638b74cd3a5a38ec5d9c11942d6>, name = "valdenildo72"]
rcvd [CHAP Challenge id=0xe7 <842974609a67f548163e5a7880d2cb935acb639f>, name = "inocoop"]
sent [CHAP Response id=0xe7 <47fc5638b74cd3a5a38ec5d9c11942d6>, name = "valdenildo72"]
rcvd [CHAP Challenge id=0xe7 <842974609a67f548163e5a7880d2cb935acb639f>, name = "inocoop"]
sent [CHAP Response id=0xe7 <47fc5638b74cd3a5a38ec5d9c11942d6>, name = "valdenildo72"]
rcvd [CHAP Challenge id=0xe7 <842974609a67f548163e5a7880d2cb935acb639f>, name = "inocoop"]
sent [CHAP Response id=0xe7 <47fc5638b74cd3a5a38ec5d9c11942d6>, name = "valdenildo72"]
rcvd [CHAP Challenge id=0xe7 <842974609a67f548163e5a7880d2cb935acb639f>, name = "inocoop"]
sent [CHAP Response id=0xe7 <47fc5638b74cd3a5a38ec5d9c11942d6>, name = "valdenildo72"]
rcvd [CHAP Challenge id=0xe7 <842974609a67f548163e5a7880d2cb935acb639f>, name = "inocoop"]
sent [CHAP Response id=0xe7 <47fc5638b74cd3a5a38ec5d9c11942d6>, name = "valdenildo72"]
rcvd [CHAP Challenge id=0xe7 <842974609a67f548163e5a7880d2cb935acb639f>, name = "inocoop"]
sent [CHAP Response id=0xe7 <47fc5638b74cd3a5a38ec5d9c11942d6>, name = "valdenildo72"]
rcvd [CHAP Challenge id=0xe7 <842974609a67f548163e5a7880d2cb935acb639f>, name = "inocoop"]
sent [CHAP Response id=0xe7 <47fc5638b74cd3a5a38ec5d9c11942d6>, name = "valdenildo72"]
sent [LCP EchoReq id=0x1 magic=0xb474b488]
rcvd [LCP EchoReq id=0x1 magic=0x895cd325]
sent [LCP EchoRep id=0x1 magic=0xb474b488]
rcvd [LCP EchoRep id=0x1 magic=0x895cd325]
rcvd [LCP TermReq id=0x2 "Authentication failed"]
LCP terminated by peer (Authentication failed)
sent [LCP TermAck id=0x2]
Connection terminated.
Modem hangup
Terminating on signal 2

```I called to my ISP and they said that I have a good connection but they're not receiving any packets of PPPoE authentication.

I've tried to reinstall the card's driver, so I downloaded the driver from the railink's site, installed following the install instruction, but with no success.

Anyone knows what can be wrong?

Edit:
Problem SOLVED!!

The link that I followed:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=fullsearch&value=linkto%3A%22WifiDocs%2FDriver%2FRalinkRT61%22&context=180]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=fullsearch&value=linkto%3A%22WifiDocs%2FDriver%2FRalinkRT61%22&context=180")

---


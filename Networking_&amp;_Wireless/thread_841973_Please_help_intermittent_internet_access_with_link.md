---
title: "Please help: intermittent internet access with linksys wusb54gc"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by kkram13 on 2008-06-26
Well, I'm going to give up and live with it. A previous thread did not offer any solutions, so I'll try once more.

System: cobbled together 5 years ago so old-ish: AMD Athlon, 512 Gb RAM. Linksys WUSB54GC with Ubuntu 8.04 (driver: rt73usb). Wireless network is WEP protected (old router... ) Oh and I'm in the basement with the router two floors up so the connection is so-so (generally ~60%).

Problem: wireless internet will connect but after a while, disconnect, then reconnect. This gets progressively worse as the computer is on for longer. Eventually, the connection is very very slow or not there at all!

Diagnostics: often ping will not work (to router or internet) but ifconfig/iwconfig give an IP address and connection to the network. Some websites seem worse than others, gmail is often bad.

Attempted solutions: manual connection does not work, I seem to need roaming mode. Ndiswrapper with driver from Windows CD was no better. Tried to compile a new driver using rt73, didn't work. Wicd did not help other.

Further information: my dmesg shows repeated joining attempts, all quite weird. It's shown below.

Extract from dmesg:
[  129.681318] NET: Registered protocol family 10
[  129.682235] lo: Disabled Privacy Extensions
[  129.683557] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  140.576858] NET: Registered protocol family 17
[  144.708158] wlan0: Initial auth_alg=0
[  144.708178] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  144.711229] wlan0: RX authentication from 00:09:5b:47:ea:7e (alg=0 transaction=2 status=0)
[  144.711243] wlan0: authenticated
[  144.711247] wlan0: associate with AP 00:09:5b:47:ea:7e
[  144.713170] wlan0: RX AssocResp from 00:09:5b:47:ea:7e (capab=0x1 status=0 aid=4)
[  144.713177] wlan0: associated
[  144.713539] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  158.843156] wlan0: no IPv6 routers present
[  165.697310] wlan0: No ProbeResp from current AP 00:09:5b:47:ea:7e - assume out of range
[  169.299570] wlan0: Initial auth_alg=0
[  169.299585] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  169.302584] wlan0: RX authentication from 00:09:5b:47:ea:7e (alg=0 transaction=2 status=0)
[  169.302591] wlan0: authenticated
[  169.302596] wlan0: associate with AP 00:09:5b:47:ea:7e
[  169.305568] wlan0: RX ReassocResp from 00:09:5b:47:ea:7e (capab=0x1 status=0 aid=4)
[  169.305574] wlan0: associated
[  169.453410] wlan0: Initial auth_alg=0
[  169.453431] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  169.456429] wlan0: RX authentication from 00:09:5b:47:ea:7e (alg=0 transaction=2 status=0)
[  169.456436] wlan0: authenticated
[  169.456441] wlan0: associate with AP 00:09:5b:47:ea:7e
[  169.458427] wlan0: RX ReassocResp from 00:09:5b:47:ea:7e (capab=0x1 status=0 aid=4)
[  169.458435] wlan0: associated
[  177.175755] wlan0: No ProbeResp from current AP 00:09:5b:47:ea:7e - assume out of range
[  180.791072] wlan0: Initial auth_alg=0
[  180.791088] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  180.944918] wlan0: Initial auth_alg=0
[  180.944936] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  181.142545] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  181.294594] wlan0: RX authentication from 00:09:5b:47:ea:7e (alg=0 transaction=2 status=0)
[  181.294604] wlan0: authenticated
[  181.294609] wlan0: associate with AP 00:09:5b:47:ea:7e
[  181.297578] wlan0: authentication frame received from 00:09:5b:47:ea:7e, but not in authenticate state - ignored
[  181.298581] wlan0: authentication frame received from 00:09:5b:47:ea:7e, but not in authenticate state - ignored
[  181.494414] wlan0: associate with AP 00:09:5b:47:ea:7e
[  181.497384] wlan0: RX ReassocResp from 00:09:5b:47:ea:7e (capab=0x1 status=0 aid=4)
[  181.497391] wlan0: associated
[  236.096823] wlan0: No ProbeResp from current AP 00:09:5b:47:ea:7e - assume out of range
[  239.713149] wlan0: Initial auth_alg=0
[  239.713165] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  239.866995] wlan0: Initial auth_alg=0
[  239.867012] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  240.063776] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  240.263699] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  240.463634] wlan0: authentication with AP 00:09:5b:47:ea:7e timed out
[  240.541348] wlan0: authentication frame received from 00:09:5b:47:ea:7e, but not in authenticate state - ignored
[  240.543329] wlan0: authentication frame received from 00:09:5b:47:ea:7e, but not in authenticate state - ignored
[  240.546327] wlan0: authentication frame received from 00:09:5b:47:ea:7e, but not in authenticate state - ignored
[  240.547328] wlan0: authentication frame received from 00:09:5b:47:ea:7e, but not in authenticate state - ignored
[  253.352513] wlan0: Initial auth_alg=0
[  253.352528] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  253.506357] wlan0: Initial auth_alg=0
[  253.506374] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  253.702506] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  253.902566] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  253.971931] wlan0: RX authentication from 00:09:5b:47:ea:7e (alg=0 transaction=2 status=0)
[  253.971940] wlan0: authenticated

etc. etc. etc. Then this:
[  468.228657] wlan0: associated
[  571.594352] WEP decrypt failed (ICV)
[  584.173716] WEP decrypt failed (ICV)
[  600.560794] wlan0: No ProbeResp from current AP 00:09:5b:47:ea:7e - assume out of range
[  604.159753] wlan0: Initial auth_alg=0
[  604.159774] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  604.313554] wlan0: Initial auth_alg=0
[  604.313572] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  604.510961] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  604.547614] wlan0: RX authentication from 00:09:5b:47:ea:7e (alg=0 transaction=2 status=0)
[  604.547628] wlan0: authenticated
[  604.547633] wlan0: associate with AP 00:09:5b:47:ea:7e
[  604.548558] wlan0: authentication frame received from 00:09:5b:47:ea:7e, but not in authenticate state - ignored
[  604.550394] wlan0: RX ReassocResp from 00:09:5b:47:ea:7e (capab=0x1 status=0 aid=4)
[  604.550408] wlan0: associated
[  636.534579] wlan0: No ProbeResp from current AP 00:09:5b:47:ea:7e - assume out of range
[  640.169698] wlan0: Initial auth_alg=0
[  640.169715] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  640.337582] wlan0: Initial auth_alg=0
[  640.337607] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  640.360560] wlan0: RX authentication from 00:09:5b:47:ea:7e (alg=0 transaction=2 status=0)
[  640.360574] wlan0: authenticated
[  640.360579] wlan0: associate with AP 00:09:5b:47:ea:7e
[  640.363527] wlan0: authentication frame received from 00:09:5b:47:ea:7e, but not in authenticate state - ignored
[  640.364531] wlan0: RX ReassocResp from 00:09:5b:47:ea:7e (capab=0x1 status=0 aid=4)
[  640.364539] wlan0: associated
[  654.355687] wlan0: No ProbeResp from current AP 00:09:5b:47:ea:7e - assume out of range
[  657.958908] wlan0: Initial auth_alg=0
[  657.958924] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  658.112755] wlan0: Initial auth_alg=0
[  658.112773] wlan0: authenticate with AP 00:09:5b:47:ea:7e
[  658.267647] wlan0: RX authentication from 00:09:5b:47:ea:7e (alg=0 transaction=2 status=0)
[  658.267662] wlan0: authenticated
[  658.267667] wlan0: associate with AP 00:09:5b:47:ea:7e
[  658.268654] wlan0: authentication frame received from 00:09:5b:47:ea:7e, but not in authenticate state - ignored
[  658.271610] wlan0: RX ReassocResp from 00:09:5b:47:ea:7e (capab=0x1 status=0 aid=4)
[  658.271616] wlan0: associated
[  745.923029] WEP decrypt failed (ICV)
[  752.909043] WEP decrypt failed (ICV)
[  760.230764] wlan0: No ProbeResp from current AP 00:09:5b:47:ea:7e - assume out of range

Many thanks for any help!

 Mark

|\/|<

---


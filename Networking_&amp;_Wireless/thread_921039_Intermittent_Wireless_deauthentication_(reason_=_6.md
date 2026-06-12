---
title: "Intermittent Wireless deauthentication (reason = 6)"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by alecz20 on 2008-09-15
A few days ago I started having a strange problem with my wireless connection. It has been working perfectly for months, but a few days ago it just kept asking for the WPA key. I have the correct key, but it just kept asking.

Doing some research I found about wicd. It worked well until I rebooted the router. After that it just wouldn't see the network. After a reboot, it saw the network but failed to connect as well.

I went back to network-manager-gnome, and enabled manual configuration.

The wireless still deauthenticates, but at it reconnects automatically because of the manual configuration. This is still not solved because the connection is intermittent.

Looking in the syslog, I am getting something like this:

```

Sep 15 21:14:36 alex-laptop kernel: [ 3762.977996] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:14:36 alex-laptop kernel: [ 3762.978032] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:14:36 alex-laptop kernel: [ 3762.978041] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:14:36 alex-laptop kernel: [ 3762.978049] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:14:36 alex-laptop kernel: [ 3762.978056] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:14:49 alex-laptop kernel: [ 3775.809988] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:14:49 alex-laptop kernel: [ 3775.810000] eth1: deauthenticated
Sep 15 21:14:49 alex-laptop kernel: [ 3775.810018] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:14:49 alex-laptop kernel: [ 3775.810027] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:14:49 alex-laptop kernel: [ 3775.810035] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:14:49 alex-laptop kernel: [ 3775.810043] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:14:49 alex-laptop kernel: [ 3775.810052] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:14:49 alex-laptop kernel: [ 3775.810931] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:14:49 alex-laptop kernel: [ 3775.811698] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:14:49 alex-laptop kernel: [ 3775.813127] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:14:49 alex-laptop kernel: [ 3775.813134] eth1: authenticated
Sep 15 21:14:49 alex-laptop kernel: [ 3775.813139] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:14:49 alex-laptop kernel: [ 3775.815621] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:14:49 alex-laptop kernel: [ 3775.815630] eth1: associated
Sep 15 21:14:49 alex-laptop kernel: [ 3775.815720] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:15:05 alex-laptop kernel: [ 3791.968627] eth1: Initial auth_alg=0
Sep 15 21:15:05 alex-laptop kernel: [ 3791.968644] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:15:05 alex-laptop kernel: [ 3791.969771] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:15:05 alex-laptop kernel: [ 3791.969780] eth1: authenticated
Sep 15 21:15:05 alex-laptop kernel: [ 3791.969785] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:15:05 alex-laptop kernel: [ 3791.972242] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:15:05 alex-laptop kernel: [ 3791.972251] eth1: associated
Sep 15 21:15:05 alex-laptop kernel: [ 3791.972341] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:15:05 alex-laptop kernel: [ 3791.972372] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:15:05 alex-laptop kernel: [ 3791.972381] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:15:05 alex-laptop kernel: [ 3791.972389] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:15:05 alex-laptop kernel: [ 3791.972397] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:15:15 alex-laptop kernel: [ 3801.996308] eth1: disassociate(reason=3)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773301] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=1)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773313] eth1: deauthenticated
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773323] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773332] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773340] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773350] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773358] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773366] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773374] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773384] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773392] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773401] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773410] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773419] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773428] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.773437] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:15:18 alex-laptop kernel: [ 3804.774395] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.775078] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.775086] eth1: authenticated
Sep 15 21:15:18 alex-laptop kernel: [ 3804.775092] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:15:18 alex-laptop kernel: [ 3804.777535] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:15:18 alex-laptop kernel: [ 3804.777544] eth1: associated
Sep 15 21:15:18 alex-laptop kernel: [ 3804.777639] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:15:26 alex-laptop kernel: [ 3812.969716] eth1: Initial auth_alg=0
Sep 15 21:15:26 alex-laptop kernel: [ 3812.969732] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:15:26 alex-laptop kernel: [ 3812.970946] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:15:26 alex-laptop kernel: [ 3812.970957] eth1: authenticated
Sep 15 21:15:26 alex-laptop kernel: [ 3812.970962] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:15:26 alex-laptop kernel: [ 3812.973424] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:15:26 alex-laptop kernel: [ 3812.973434] eth1: associated
Sep 15 21:15:26 alex-laptop kernel: [ 3812.973545] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:15:26 alex-laptop kernel: [ 3812.973581] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:15:26 alex-laptop kernel: [ 3812.973590] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:15:26 alex-laptop kernel: [ 3812.973598] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:15:26 alex-laptop kernel: [ 3812.973606] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:15:39 alex-laptop kernel: [ 3825.754015] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=0)
Sep 15 21:15:39 alex-laptop kernel: [ 3825.754028] eth1: deauthenticated
Sep 15 21:15:39 alex-laptop kernel: [ 3825.754046] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:39 alex-laptop kernel: [ 3825.754055] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:39 alex-laptop kernel: [ 3825.754063] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:39 alex-laptop kernel: [ 3825.754071] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:15:39 alex-laptop kernel: [ 3825.754552] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:39 alex-laptop kernel: [ 3825.755566] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:15:39 alex-laptop kernel: [ 3825.756583] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:15:39 alex-laptop kernel: [ 3825.756589] eth1: authenticated
Sep 15 21:15:39 alex-laptop kernel: [ 3825.756595] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:15:39 alex-laptop kernel: [ 3825.759054] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:15:39 alex-laptop kernel: [ 3825.759063] eth1: associated
Sep 15 21:15:39 alex-laptop kernel: [ 3825.759158] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:16:19 alex-laptop kernel: [ 3865.984664] eth1: Initial auth_alg=0
Sep 15 21:16:19 alex-laptop kernel: [ 3865.984682] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:16:19 alex-laptop kernel: [ 3865.985815] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:16:19 alex-laptop kernel: [ 3865.985823] eth1: authenticated
Sep 15 21:16:19 alex-laptop kernel: [ 3865.985829] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:16:19 alex-laptop kernel: [ 3865.988605] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:16:19 alex-laptop kernel: [ 3865.988613] eth1: associated
Sep 15 21:16:19 alex-laptop kernel: [ 3865.988703] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:16:19 alex-laptop kernel: [ 3865.988736] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:16:19 alex-laptop kernel: [ 3865.988745] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:16:19 alex-laptop kernel: [ 3865.988753] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:16:19 alex-laptop kernel: [ 3865.988761] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:16:32 alex-laptop kernel: [ 3878.768185] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=0)
Sep 15 21:16:32 alex-laptop kernel: [ 3878.768197] eth1: deauthenticated
Sep 15 21:16:32 alex-laptop kernel: [ 3878.768216] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:16:32 alex-laptop kernel: [ 3878.768225] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:16:32 alex-laptop kernel: [ 3878.768233] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:16:32 alex-laptop kernel: [ 3878.768241] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:16:32 alex-laptop kernel: [ 3878.768676] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:16:32 alex-laptop kernel: [ 3878.769631] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:16:32 alex-laptop kernel: [ 3878.770670] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:16:32 alex-laptop kernel: [ 3878.770677] eth1: authenticated
Sep 15 21:16:32 alex-laptop kernel: [ 3878.770684] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:16:32 alex-laptop kernel: [ 3878.773166] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:16:32 alex-laptop kernel: [ 3878.773174] eth1: associated
Sep 15 21:16:32 alex-laptop kernel: [ 3878.773268] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:16:40 alex-laptop kernel: [ 3886.654411] eth1: Initial auth_alg=0
Sep 15 21:16:40 alex-laptop kernel: [ 3886.654427] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:16:40 alex-laptop kernel: [ 3886.658036] eth1: Initial auth_alg=0
Sep 15 21:16:40 alex-laptop kernel: [ 3886.658049] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:16:40 alex-laptop kernel: [ 3886.658088] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:16:40 alex-laptop kernel: [ 3886.658094] eth1: authenticated
Sep 15 21:16:40 alex-laptop kernel: [ 3886.658101] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:16:40 alex-laptop kernel: [ 3886.660117] eth1: authentication frame received from 00:1c:f0:6a:e2:a6, but not in authenticate state - ignored
Sep 15 21:16:40 alex-laptop kernel: [ 3886.662303] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:16:40 alex-laptop kernel: [ 3886.662313] eth1: associated
Sep 15 21:16:40 alex-laptop kernel: [ 3886.662407] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:16:40 alex-laptop kernel: [ 3886.662449] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:16:40 alex-laptop kernel: [ 3886.667439] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:16:40 alex-laptop kernel: [ 3886.667541] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:16:40 alex-laptop kernel: [ 3886.667633] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:16:40 alex-laptop kernel: [ 3886.990882] eth1: Initial auth_alg=0
Sep 15 21:16:40 alex-laptop kernel: [ 3886.990897] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:16:40 alex-laptop kernel: [ 3886.992041] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:16:40 alex-laptop kernel: [ 3886.992049] eth1: authenticated
Sep 15 21:16:40 alex-laptop kernel: [ 3886.992054] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:16:40 alex-laptop kernel: [ 3886.994515] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:16:40 alex-laptop kernel: [ 3886.994524] eth1: associated
Sep 15 21:16:40 alex-laptop kernel: [ 3886.994613] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:16:40 alex-laptop kernel: [ 3886.994646] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:16:40 alex-laptop kernel: [ 3886.994655] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:16:40 alex-laptop kernel: [ 3886.994663] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:16:40 alex-laptop kernel: [ 3886.994670] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:16:53 alex-laptop kernel: [ 3899.646698] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:16:53 alex-laptop kernel: [ 3899.646709] eth1: deauthenticated
Sep 15 21:16:53 alex-laptop kernel: [ 3899.646727] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:16:53 alex-laptop kernel: [ 3899.646735] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:16:53 alex-laptop kernel: [ 3899.646743] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:16:53 alex-laptop kernel: [ 3899.647610] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:16:53 alex-laptop kernel: [ 3899.647992] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:16:53 alex-laptop kernel: [ 3899.648820] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:16:53 alex-laptop kernel: [ 3899.648826] eth1: authenticated
Sep 15 21:16:53 alex-laptop kernel: [ 3899.648832] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:16:53 alex-laptop kernel: [ 3899.651687] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:16:53 alex-laptop kernel: [ 3899.651698] eth1: associated
Sep 15 21:16:53 alex-laptop kernel: [ 3899.651789] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:17:01 alex-laptop /USR/SBIN/CRON[21533]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 15 21:17:09 alex-laptop kernel: [ 3915.996080] eth1: Initial auth_alg=0
Sep 15 21:17:09 alex-laptop kernel: [ 3915.996096] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:17:09 alex-laptop kernel: [ 3915.997233] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:17:09 alex-laptop kernel: [ 3915.997244] eth1: authenticated
Sep 15 21:17:09 alex-laptop kernel: [ 3915.997249] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:17:09 alex-laptop kernel: [ 3915.999770] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:17:09 alex-laptop kernel: [ 3915.999779] eth1: associated
Sep 15 21:17:09 alex-laptop kernel: [ 3915.999871] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:17:09 alex-laptop kernel: [ 3915.999904] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:17:09 alex-laptop kernel: [ 3915.999913] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:17:09 alex-laptop kernel: [ 3915.999921] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:17:09 alex-laptop kernel: [ 3915.999929] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:17:22 alex-laptop kernel: [ 3928.814321] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:17:22 alex-laptop kernel: [ 3928.814333] eth1: deauthenticated
Sep 15 21:17:22 alex-laptop kernel: [ 3928.814352] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:17:22 alex-laptop kernel: [ 3928.814361] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:17:22 alex-laptop kernel: [ 3928.814369] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:17:22 alex-laptop kernel: [ 3928.814377] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:17:22 alex-laptop kernel: [ 3928.816074] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:17:22 alex-laptop kernel: [ 3928.816086] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:17:22 alex-laptop kernel: [ 3928.817000] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:17:22 alex-laptop kernel: [ 3928.817009] eth1: authenticated
Sep 15 21:17:22 alex-laptop kernel: [ 3928.817014] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:17:22 alex-laptop kernel: [ 3928.819474] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:17:22 alex-laptop kernel: [ 3928.819483] eth1: associated
Sep 15 21:17:22 alex-laptop kernel: [ 3928.819574] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:17:30 alex-laptop kernel: [ 3937.000346] eth1: Initial auth_alg=0
Sep 15 21:17:30 alex-laptop kernel: [ 3937.000363] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:17:30 alex-laptop kernel: [ 3937.001496] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:17:30 alex-laptop kernel: [ 3937.001505] eth1: authenticated
Sep 15 21:17:30 alex-laptop kernel: [ 3937.001510] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:17:30 alex-laptop kernel: [ 3937.003995] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:17:30 alex-laptop kernel: [ 3937.004007] eth1: associated
Sep 15 21:17:30 alex-laptop kernel: [ 3937.004102] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:17:30 alex-laptop kernel: [ 3937.004146] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:17:30 alex-laptop kernel: [ 3937.004154] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:17:30 alex-laptop kernel: [ 3937.004163] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:17:30 alex-laptop kernel: [ 3937.004170] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:17:43 alex-laptop kernel: [ 3949.794752] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=0)
Sep 15 21:17:43 alex-laptop kernel: [ 3949.794766] eth1: deauthenticated
Sep 15 21:17:43 alex-laptop kernel: [ 3949.794785] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:17:43 alex-laptop kernel: [ 3949.794793] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:17:43 alex-laptop kernel: [ 3949.794801] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:17:43 alex-laptop kernel: [ 3949.794809] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:17:43 alex-laptop kernel: [ 3949.795375] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:17:43 alex-laptop kernel: [ 3949.796325] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:17:43 alex-laptop kernel: [ 3949.797323] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:17:43 alex-laptop kernel: [ 3949.797331] eth1: authenticated
Sep 15 21:17:43 alex-laptop kernel: [ 3949.797337] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:17:43 alex-laptop kernel: [ 3949.799772] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:17:43 alex-laptop kernel: [ 3949.799780] eth1: associated
Sep 15 21:17:43 alex-laptop kernel: [ 3949.799873] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:18:15 alex-laptop kernel: [ 3981.996741] eth1: Initial auth_alg=0
Sep 15 21:18:15 alex-laptop kernel: [ 3981.996758] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:18:15 alex-laptop kernel: [ 3981.997878] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:18:15 alex-laptop kernel: [ 3981.997887] eth1: authenticated
Sep 15 21:18:15 alex-laptop kernel: [ 3981.997892] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:18:15 alex-laptop kernel: [ 3982.000372] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:18:15 alex-laptop kernel: [ 3982.000383] eth1: associated
Sep 15 21:18:15 alex-laptop kernel: [ 3982.000476] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:18:15 alex-laptop kernel: [ 3982.000513] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:18:15 alex-laptop kernel: [ 3982.000521] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:18:15 alex-laptop kernel: [ 3982.000529] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:18:15 alex-laptop kernel: [ 3982.000537] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:18:28 alex-laptop kernel: [ 3994.826037] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:28 alex-laptop kernel: [ 3994.826049] eth1: deauthenticated
Sep 15 21:18:28 alex-laptop kernel: [ 3994.826067] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:28 alex-laptop kernel: [ 3994.826076] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:28 alex-laptop kernel: [ 3994.826084] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:28 alex-laptop kernel: [ 3994.826092] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:28 alex-laptop kernel: [ 3994.826100] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:18:28 alex-laptop kernel: [ 3994.826759] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:28 alex-laptop kernel: [ 3994.827701] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:28 alex-laptop kernel: [ 3994.828798] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:18:28 alex-laptop kernel: [ 3994.828805] eth1: authenticated
Sep 15 21:18:28 alex-laptop kernel: [ 3994.828810] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:18:28 alex-laptop kernel: [ 3994.831304] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:18:28 alex-laptop kernel: [ 3994.831312] eth1: associated
Sep 15 21:18:28 alex-laptop kernel: [ 3994.831404] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:18:44 alex-laptop kernel: [ 4010.995177] eth1: Initial auth_alg=0
Sep 15 21:18:44 alex-laptop kernel: [ 4010.995194] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:18:44 alex-laptop kernel: [ 4010.996330] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:18:44 alex-laptop kernel: [ 4010.996340] eth1: authenticated
Sep 15 21:18:44 alex-laptop kernel: [ 4010.996346] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:18:44 alex-laptop kernel: [ 4010.998813] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:18:44 alex-laptop kernel: [ 4010.998822] eth1: associated
Sep 15 21:18:44 alex-laptop kernel: [ 4010.998912] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:18:44 alex-laptop kernel: [ 4010.998946] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:18:44 alex-laptop kernel: [ 4010.998955] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:18:44 alex-laptop kernel: [ 4010.998963] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:18:44 alex-laptop kernel: [ 4010.998971] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:18:54 alex-laptop kernel: [ 4021.026881] eth1: disassociate(reason=3)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789274] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=1)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789287] eth1: deauthenticated
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789297] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789305] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789313] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789321] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789330] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789338] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789346] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789354] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789362] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789370] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789378] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789394] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789402] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.789410] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:18:57 alex-laptop kernel: [ 4023.790150] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.791094] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.791101] eth1: authenticated
Sep 15 21:18:57 alex-laptop kernel: [ 4023.791108] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:18:57 alex-laptop kernel: [ 4023.793612] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:18:57 alex-laptop kernel: [ 4023.793620] eth1: associated
Sep 15 21:18:57 alex-laptop kernel: [ 4023.793715] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:19:13 alex-laptop kernel: [ 4039.997399] eth1: Initial auth_alg=0
Sep 15 21:19:13 alex-laptop kernel: [ 4039.997409] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:19:13 alex-laptop kernel: [ 4039.998960] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:19:13 alex-laptop kernel: [ 4039.998964] eth1: authenticated
Sep 15 21:19:13 alex-laptop kernel: [ 4039.998967] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:19:13 alex-laptop kernel: [ 4040.001385] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:19:13 alex-laptop kernel: [ 4040.001389] eth1: associated
Sep 15 21:19:13 alex-laptop kernel: [ 4040.001427] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:19:13 alex-laptop kernel: [ 4040.001445] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:19:13 alex-laptop kernel: [ 4040.001449] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:19:13 alex-laptop kernel: [ 4040.001453] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:19:13 alex-laptop kernel: [ 4040.001456] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:19:26 alex-laptop kernel: [ 4052.650222] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:26 alex-laptop kernel: [ 4052.650232] eth1: deauthenticated
Sep 15 21:19:26 alex-laptop kernel: [ 4052.650248] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:26 alex-laptop kernel: [ 4052.650256] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:26 alex-laptop kernel: [ 4052.650264] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:19:26 alex-laptop kernel: [ 4052.651016] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:26 alex-laptop kernel: [ 4052.652196] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:26 alex-laptop kernel: [ 4052.653112] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:19:26 alex-laptop kernel: [ 4052.653120] eth1: authenticated
Sep 15 21:19:26 alex-laptop kernel: [ 4052.653125] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:19:26 alex-laptop kernel: [ 4052.655575] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:19:26 alex-laptop kernel: [ 4052.655624] eth1: associated
Sep 15 21:19:26 alex-laptop kernel: [ 4052.655715] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:19:34 alex-laptop kernel: [ 4061.000413] eth1: Initial auth_alg=0
Sep 15 21:19:34 alex-laptop kernel: [ 4061.000425] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:19:34 alex-laptop kernel: [ 4061.001761] eth1: Initial auth_alg=0
Sep 15 21:19:34 alex-laptop kernel: [ 4061.001766] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:19:34 alex-laptop kernel: [ 4061.001779] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:19:34 alex-laptop kernel: [ 4061.001783] eth1: authenticated
Sep 15 21:19:34 alex-laptop kernel: [ 4061.001786] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:19:34 alex-laptop kernel: [ 4061.005355] eth1: authentication frame received from 00:1c:f0:6a:e2:a6, but not in authenticate state - ignored
Sep 15 21:19:34 alex-laptop kernel: [ 4061.007769] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:19:34 alex-laptop kernel: [ 4061.007774] eth1: associated
Sep 15 21:19:34 alex-laptop kernel: [ 4061.007814] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:19:34 alex-laptop kernel: [ 4061.007836] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:19:34 alex-laptop kernel: [ 4061.007841] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:19:34 alex-laptop kernel: [ 4061.007845] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:19:34 alex-laptop kernel: [ 4061.007848] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Sep 15 21:19:47 alex-laptop kernel: [ 4073.835714] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:47 alex-laptop kernel: [ 4073.835723] eth1: deauthenticated
Sep 15 21:19:47 alex-laptop kernel: [ 4073.835736] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:47 alex-laptop kernel: [ 4073.835740] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:47 alex-laptop kernel: [ 4073.835743] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:47 alex-laptop kernel: [ 4073.835747] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:47 alex-laptop kernel: [ 4073.835751] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:19:47 alex-laptop kernel: [ 4073.836167] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:47 alex-laptop kernel: [ 4073.837297] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)
Sep 15 21:19:47 alex-laptop kernel: [ 4073.838149] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:19:47 alex-laptop kernel: [ 4073.838154] eth1: authenticated
Sep 15 21:19:47 alex-laptop kernel: [ 4073.838156] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:19:47 alex-laptop kernel: [ 4073.840610] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:19:47 alex-laptop kernel: [ 4073.840617] eth1: associated
Sep 15 21:19:47 alex-laptop kernel: [ 4073.840659] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:20:12 alex-laptop kernel: [ 4098.002159] eth1: Initial auth_alg=0
Sep 15 21:20:12 alex-laptop kernel: [ 4098.002175] eth1: authenticate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:20:12 alex-laptop kernel: [ 4098.003305] eth1: RX authentication from 00:1c:f0:6a:e2:a6 (alg=0 transaction=2 status=0)
Sep 15 21:20:12 alex-laptop kernel: [ 4098.003316] eth1: authenticated
Sep 15 21:20:12 alex-laptop kernel: [ 4098.003321] eth1: associate with AP 00:1c:f0:6a:e2:a6
Sep 15 21:20:12 alex-laptop kernel: [ 4098.005794] eth1: RX ReassocResp from 00:1c:f0:6a:e2:a6 (capab=0x431 status=0 aid=2)
Sep 15 21:20:12 alex-laptop kernel: [ 4098.005798] eth1: associated
Sep 15 21:20:12 alex-laptop kernel: [ 4098.005837] eth1 (WE) : Wireless Event too big (320)
Sep 15 21:20:12 alex-laptop kernel: [ 4098.005854] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Sep 15 21:20:12 alex-laptop kernel: [ 4098.005858] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Sep 15 21:20:12 alex-laptop kernel: [ 4098.005862] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Sep 15 21:20:12 alex-laptop kernel: [ 4098.005866] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15

```

I don't know why it does this. As I said it was working PERFECTLY until a couple days ago, and I did not do anything regarding networking.

Edit: I am now testing with the Ubuntu 8.04.1 live CD. Even though the 1st attempt failed:
```

old device 'wlan0' activating, won't change

```
It worked on the second attempt.

So it is some software problem. Also, why the wireless card is 'wlan0' on the live CD while on the installed OS is 'eth1'

I am at a loss figuring out the sys log to see what's the problem... I feel I might need to re-install Ubuntu (after a year of use)

---

### Post by alecz20 on 2008-09-21
it started working back again.

I still have no clue as why it failed, but now its back to normal.

---

### Post by alecz20 on 2008-10-16
Problem started appearing again.

The wireless works for about 24 hours, then it disconnects and prompts for password. I fails to connect anymore, deauthenticating everytime.

The only way to fix the problem is to reboot the laptop.

Any ideas? :(

---

### Post by alecz20 on 2008-11-08
I also noticed that when this happens, I get hundreds of messages saying:
```

Nov  8 15:21:33 alex-laptop kernel: [176585.228766] eth1: RX deauthentication from 00:1c:f0:6a:e2:a6 (reason=6)

```

If I am running amule, there is a memory leak that completely hangs the system. Do this is a double problem.

I might give a try to Intrepid, since it's supposed to have a fixed wireless driver. Or maybe there is a proprietary driver that does not have this problem, I am getting pretty upset about this issue. Not only I can't access the network anymore, but the memory leak hangs the system and i need to do a hard reboot. Setting a memory limit for my user in /etc/security/limits.conf does not help either.

---

### Post by Geneset on 2010-07-08
I don't know if this applies, but I had a similar reason=6 problem on connection that was solved by [using the compat-wireless drivers]("http://goo.gl/fb/93hJP") instead of the stock ones.

---

### Post by TZer0 on 2010-07-13
I'm having the same problem. The network card stalls (the OS doesn't report anything), nothing gets through and things disconnect.

The 2nd time it happened I noticed it and did a manual restart of the card - something which resolves the problem... for a while.
dmesg | grep wlan0
```
[ 4666.121416] wlan0: deauthenticated from 00:1c:f0:71:c7:ec (Reason: 6)
[ 4667.287146] wlan0: direct probe to AP 00:1c:f0:71:c7:ec (try 1)
[ 4667.292148] wlan0: direct probe responded
[ 4667.292166] wlan0: authenticate with AP 00:1c:f0:71:c7:ec (try 1)
[ 4667.294143] wlan0: authenticated
[ 4667.294224] wlan0: associate with AP 00:1c:f0:71:c7:ec (try 1)
[ 4667.298489] wlan0: RX AssocResp from 00:1c:f0:71:c7:ec (capab=0x431 status=0 aid=3)
[ 4667.298505] wlan0: associated
[14447.613222] wlan0: deauthenticating from 00:1c:f0:71:c7:ec by local choice (reason=3)
[14449.586300] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14455.782583] wlan0: deauthenticating from 00:1c:f0:71:c7:ec by local choice (reason=3)
[14455.982676] wlan0: direct probe to AP 00:1c:f0:71:c7:ec (try 1)
[14455.987668] wlan0: direct probe responded
[14455.987687] wlan0: authenticate with AP 00:1c:f0:71:c7:ec (try 1)
[14456.184105] wlan0: authenticate with AP 00:1c:f0:71:c7:ec (try 2)
[14456.186102] wlan0: authenticated
[14456.186180] wlan0: associate with AP 00:1c:f0:71:c7:ec (try 1)
[14456.196329] wlan0: RX AssocResp from 00:1c:f0:71:c7:ec (capab=0x431 status=0 aid=3)
[14456.196351] wlan0: associated
[14456.206575] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[14466.688068] wlan0: no IPv6 routers present

```sudo lshw -C network
```
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 90:4c:e5:95:c6:60
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=10.0.0.15 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:57100000-5710ffff

```

---


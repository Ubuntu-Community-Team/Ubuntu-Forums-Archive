---
title: "tor stopped working (noroute even with the bridges)"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by kamikakushi on 2010-10-06
tor used to be my life saver from office, but since my office moved, and although i still use the same network, I couldn't make it work. I have downloaded the latest version tor-im-browser-1.3.10_en-US which includes polipo, vidalia, pidgin etc. but didn't help.
 
if i use bridges the log says 
 
[COLOR=gray]Eki 06 11:06:31.152 [Notice] Tor v0.2.1.26. This is experimental software. Do not rely on it for strong anonymity. (Running on Windows XP Service Pack 3 [workstation] {terminal services, single user})[/COLOR]
[COLOR=gray]Eki 06 11:06:31.152 [Notice] Initialized libevent version 1.4.13-stable using method win32. Good.[/COLOR]
[COLOR=gray]Eki 06 11:06:31.152 [Notice] Opening Socks listener on 127.0.0.1:9050[/COLOR]
[COLOR=gray]Eki 06 11:06:31.152 [Notice] Opening Control listener on 127.0.0.1:9051[/COLOR]
[COLOR=gray]Eki 06 11:06:31.152 [Notice] Parsing GEOIP file.[/COLOR]
[COLOR=gray]Eki 06 11:06:55.295 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 1; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:06:55.311 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 2; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:06:55.311 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 3; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:06:55.311 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 4; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:06:55.389 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 5; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:06:55.389 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 6; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:06:55.389 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 7; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:06:55.389 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 8; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:06:55.389 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 9; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:06:55.389 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 10; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.235 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 11; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.235 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 12; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.235 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 13; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.235 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 14; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.376 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 15; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.376 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 16; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.376 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 17; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.376 [Notice] Bootstrapped 10%: Finishing handshake with directory server.[/COLOR]
[COLOR=gray]Eki 06 11:07:16.376 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (DONE; DONE; count 18; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.376 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 19; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.376 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 20; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.376 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 21; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:16.376 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (DONE; DONE; count 22; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.300 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 23; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.300 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 24; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.300 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 25; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.300 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 26; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.300 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (DONE; DONE; count 27; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.441 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 28; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.441 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 29; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.441 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 30; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.456 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 31; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.456 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 32; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.456 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (DONE; DONE; count 33; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:07:37.550 [Warning] Problem bootstrapping. Stuck at 10%: Finishing handshake with directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 34; recommendation warn)[/COLOR]
 
and if i do not use bridges 
 
[COLOR=gray]Eki 06 11:08:07.568 [Notice] Tor v0.2.1.26. This is experimental software. Do not rely on it for strong anonymity. (Running on Windows XP Service Pack 3 [workstation] {terminal services, single user})[/COLOR]
[COLOR=gray]Eki 06 11:08:09.334 [Notice] Initialized libevent version 1.4.13-stable using method win32. Good.[/COLOR]
[COLOR=gray]Eki 06 11:08:09.334 [Notice] Opening Socks listener on 127.0.0.1:9050[/COLOR]
[COLOR=gray]Eki 06 11:08:09.334 [Notice] Opening Control listener on 127.0.0.1:9051[/COLOR]
[COLOR=gray]Eki 06 11:08:09.334 [Notice] Parsing GEOIP file.[/COLOR]
[COLOR=gray]Eki 06 11:08:33.491 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 1; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:08:33.491 [Notice] No current certificate known for authority moria1; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:08:33.491 [Notice] No current certificate known for authority tor26; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:08:33.491 [Notice] No current certificate known for authority dizum; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:08:33.491 [Notice] No current certificate known for authority ides; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:08:33.491 [Notice] No current certificate known for authority gabelmoo; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:08:33.491 [Notice] No current certificate known for authority dannenberg; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:08:33.491 [Notice] No current certificate known for authority urras; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:08:38.632 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 2; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:08:54.820 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 3; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:09:00.070 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 4; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:10:14.416 [Notice] No current certificate known for authority moria1; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:10:14.416 [Notice] No current certificate known for authority tor26; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:10:14.416 [Notice] No current certificate known for authority dizum; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:10:14.416 [Notice] No current certificate known for authority ides; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:10:14.416 [Notice] No current certificate known for authority gabelmoo; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:10:14.416 [Notice] No current certificate known for authority dannenberg; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:10:14.416 [Notice] No current certificate known for authority urras; launching request.[/COLOR]
[COLOR=gray]Eki 06 11:10:35.339 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 5; recommendation warn)[/COLOR]
[COLOR=gray]Eki 06 11:10:35.339 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 6; recommendation warn)[/COLOR]
 
[COLOR=black]if i can make a connection somewhere else and the try again at the ofifice i get uptto %85 but never connect succesfully. [/COLOR]
 
I know i better check tor forums but they're all forbidden from my office i can not even search :( 
 
anybody who can help me or has an advice?
 
k.

---


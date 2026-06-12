---
title: "PPPoE problem"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by Lamrin on 2005-10-26
Hi,

 

im running RP-PPPoE, Free radius on linux 7.3 with 2.4 kernel. everything is working fine but when i connect netgear/linksys kind of router in my network as a PPPoE user........ it connects properly but i get following messages contnuously in my system logs.


=====================================================
Oct 20 15:55:11 thane002 pppoe-server[1110]: PADT for session 267 received from 00:0F:B5:14AD; should be from 00:E0:50:01:76:7D
Oct 20 15:55:11 thane002 pppoe-server[1110]: PADT for session 267 received from 00:0F:B5:14AD; should be from 00:E0:50:01:76:7D
Oct 20 15:55:11 thane002 pppoe-server[1110]: PADT for session 12 received from 00:0F:B5:14AD; should be from 00:E0:4C:80:1A:2E
Oct 20 15:55:13 thane002 pppoe-server[1110]: PADT for session 267 received from 00:09:5B:6C3:A3; should be from 00:E0:50:01:76:7D
Oct 20 15:55:13 thane002 pppoe-server[1110]: PADT for session 267 received from 00:0F:B5:14AD; should be from 00:E0:50:01:76:7D
Oct 20 15:55:13 thane002 pppoe-server[1110]: PADT for session 267 received from 00:0E:35:6D:E4:1F; should be from 00:E0:50:01:76:7D
Oct 20 15:55:13 thane002 pppoe-server[1110]: PADT for session 267 received from 00:0F:B5:14AD; should be from 00:E0:50:01:76:7D
Oct 20 15:55:14 thane002 last message repeated 2 times
Oct 20 15:55:14 thane002 pppoe-server[1110]: PADT for session 267 received from 00:0E:35:6D:E4:1F; should be from 00:E0:50:01:76:7D
Oct 20 15:55:14 thane002 pppoe-server[1110]: PADT for session 267 received from 00:0F:B5:14AD; should be from 00:E0:50:01:76:7D
Oct 20 15:55:14 thane002 pppoe-server[1110]: PADT for session 267 received from 00:0F:B5:14AD; should be from 00:E0:50:01:76:7D
Oct 20 15:55:30 thane002 pppoe-server[1110]: PADT for session 18 received from 00:09:5B:6A:E3:89; should be from 00:A1:B0:A0:9F:06
Oct 20 15:55:30 thane002 pppoe-server[1110]: PADT for session 18 received from 00:09:5B:6C3:A3; should be from 00:A1:B0:A0:9F:06
Oct 20 15:55:30 thane002 pppoe-server[1110]: PADT for session 3 received from 00:0F:B5:14AD; should be from 00:E0:4C:E1:AF:CA
Oct 20 15:55:30 thane002 pppoe-server[1110]: PADT for session 3 received from 00:0F:B5:14AD; should be from 00:E0:4C:E1:AF:CA
Oct 20 15:55:33 thane002 pppoe-server[1110]: PADT for session 12 received from 00:09:5B:6C3:A3; should be from 00:E0:4C:80:1A:2E
Oct 20 15:55:33 thane002 pppoe-server[1110]: PADT for session 12 received from 00:09:5B:6A:E3:89; should be from 00:E0:4C:80:1A:2E
Oct 20 15:55:33 thane002 pppoe-server[1110]: PADT for session 12 received from 00:0F:B5:14AD; should be from 00:E0:4C:80:1A:2E
Oct 20 15:55:33 thane002 pppoe-server[1110]: PADT for session 12 received from 00:0F:B5:14AD; should be from 00:E0:4C:80:1A:2E
Oct 20 15:55:33 thane002 pppoe-server[1110]: PADT for session 3 received from 00:0F:B5:14AD; should be from 00:E0:4C:E1:AF:CA
Oct 20 15:55:34 thane002 pppoe-server[1110]: PADT for session 12 received from 00:0F:B5:14AD; should be from 00:E0:4C:80:1A:2E
Oct 20 15:55:34 thane002 pppoe-server[1110]: PADT for session 12 received from 00:0E:35:6D:E4:1F; should be from 00:E0:4C:80:1A:2E
Oct 20 15:55:34 thane002 pppoe-server[1110]: PADT for session 12 received from 00:0F:B5:14AD; should be from 00:E0:4C:80:1A:2E

=======================================================


i don't know why this messages are coming in logs even though user is connected. and most of the time the amount of these messages hangs the server........ which sometime crash down my MySQL also.

will there be any specific settings in netgear/linksys box ?

if somebody knows...... please help me out.

Thanks In Advance

Lamrin

---


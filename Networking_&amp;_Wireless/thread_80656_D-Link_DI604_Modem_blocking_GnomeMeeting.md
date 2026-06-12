---
title: "D-Link DI604 Modem blocking GnomeMeeting"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by geofff on 2005-10-22
I am attempting to test GnomeMeeting but without success. My router says "Unrecongnised attempt blocked from 66.135.35.44" (the voxgratia test address). GnomeMeeting then times out.

Within Applications>System Tools>Configuration Editor>apps>gnomemeeting>protocols>h323>ports I have the following:
listen_port           1720
rtp_port_range    5000:5016
tcp_port_range   30000:30010
udp_port_range  5020:5023

Within D-Link and not really knowing what I'm doing I've set "gnomemeeting" as a "special application" with trigger port 1720 and public port 1720 but this has not made any difference. 

During GnomeMeeting setup my NAT type was detected as Cone and I enabled STUN. My sound test worked OK. IP translation is enabled in the preferences and my IP address is being picked up correctly. H245 tunnelling is enabled. I haven't got any gatekeeper settings enabled.

From the total lack of other people's posts on this issue it would seem everyone elses gnomemeeting just works and yet I've just done a new install so I can't imagine its anything to do with my system. I haven't a clue why this is happening.

Help very welcome!

---


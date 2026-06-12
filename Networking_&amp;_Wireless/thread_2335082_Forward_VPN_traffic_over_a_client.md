---
title: "Forward VPN traffic over a client"
date: 2016-08-25
forum: Networking &amp; Wireless
---

### Post by jayjay89 on 2016-08-25
Hi All,

since there are media providers blocking data center IPs am no longer able to enjoy some services. I was a little bit upset, but then this idea hit me:

I am still an owner of a VPS which I used as a VPN-Server/Gateway using PPTP. The idea is to set up Raspberry Pi which will be placed in a friends house and act like a gateway. (my friend has unfortunately a dynamic IP and does not agree to use any DynDNS services) I was thinking about creating a virtual adapter which will connect to my VPN-Server with a static IP on this Interface. The VPN Server will route the traffic from other clients through the Raspberry Pi at my friends house.

Has anyone tried this yet? Would you recommend another solution?

And the really important question - I am not sure how to configure the the PPTP-Server and the Raspberry Pi the way I described. Please Help!

BR&Thx

---

### Post by TheFu on 2016-08-26
I wouldn't use PPTP. It isn't secure and hasn't been for over a decade.
Use IPSec or L2TP.

Besides that, if the remote system makes the connection and you don't suck all the bandwidth which will **** off your friend, then this should work.
Might want more of a computer than a R-pi. They aren't exactly known for handling netework throughput well.  There are $90 25W computers available with 3-10x more compute power. The old AMD E350/E450 or A4 lines should have plenty of CPU for VPN, compression and pushing data that a r-pi just doesn't have.

If money isn't an issue, perhaps an APU2 (x64 CPU) designed for imbedded routing would be a good choice too?  Got one here for $144 total. Runs BSD or Linux. Has 3 GigE Intel PRO/1000 NICs onboard. Fanless. 10W max.  No video, just serial console - if you don't know what that means, then probably should pick another device.

Another option is to buy a SlingTV box for your friend - assuming that service is available where he/she is located.  Or setup a Plex MS and share content both ways.

---


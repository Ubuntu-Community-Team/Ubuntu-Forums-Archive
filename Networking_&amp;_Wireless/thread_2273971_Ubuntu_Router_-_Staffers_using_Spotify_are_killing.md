---
title: "Ubuntu Router - Staffers using Spotify are killing our connection"
date: 2015-04-16
forum: Networking &amp; Wireless
---

### Post by Brendan_Farr-Gayno on 2015-04-16
I run a small programming business and opted to take a machine and make it our router/gateway/dhcp/dns server. We've got it running Ubuntu Server 14 LTS and it's been great. 

We have a 20mbps/20mbps connection and it handles our regular web traffic quite well and some light voip. Having access to the full bandwidth for 'work related' stuff is important and it's been pretty good to have this much upload bandwidth available to us.

I've noticed however that the voip suffers pretty badly some days and I think a few users running spotify might be the culprit. This always seems to happen when I'm on with an important client and it's becoming frustrating. However, I believe music while you are working is a real perk and I hate having to say things like 'a call is coming in, kill your spotify'. 

**Is there something I can do? I don't want to 'block' Spotify, maybe just slow it down for the staff.**

My question is, how can I limit spotify and other 'non critical' services on this gateway box? Is it possible for an Ubuntu router to also do this kind of application-level quality of service/traffic shaping etc?

Right now all users must pass through this box to access the internet, we have one NIC connected to our modem and another other connected to a switch, so I feel like there must be something that can do this without having to buy an expensive network QoS appliance?

Any ideas? Thanks!

---

### Post by michi1983 on 2015-04-17
Hm, I just have read [this]("https://community.spotify.com/t5/Newcomers-and-Contribution/Troubleshooting-connection-issues/td-p/104003").
You could try squidguard to QoS special ports.
Just an idea.

Greetz

---


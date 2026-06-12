---
title: "Resolve domain name differently depending on network"
date: 2015-12-18
forum: Networking &amp; Wireless
---

### Post by herkules on 2015-12-18
Hi there!

I'd like to ask for some advice on a networking challenge:
- I have a server running at home (owncloud, ssh, media server, ....). 
- have a dyndns running to be able to reach it from outside.

Now, from my laptop, I have to use the dyndns-adress when outside my home network, but when at home I have to use the servers local IP-adress (to save bandwidth, faster transfers, ...).

Now I'd like my laptop-ubuntu to recognize that I'm in my home network ( e.g. identified by the wifi-SSID) and "catch" any requests to the dyndns-adress and automatically directly use the loacl IP-adress instead. (thus making this transparent to any user)

A similar question was asked as a feature for the owncloud sync-client here: [https://github.com/owncloud/client/issues/203](https://github.com/owncloud/client/issues/203)  but it was not implemented + I'd like to have this feature for all use-cases, not only oc.

I'm about confident on the terminal etc, but I'm no network-expert...

Any hints are appreciated!

---


---
title: "Advice on blocking TCP RST flag packets (a la Comcast/Sandvine)..?"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by BobRetelle on 2008-06-04
I've been involved playing a small (mostly unknown) online game which recently has begun receiving MANY apparently spurious TCP RST packets which interrupt players' connections by causing the server to close the virtual circuit and force a relogin sequence over and over.

While not an administrator of the game, I've been trying to research the problem and it appears we're an untended side-effect of the use by Comcast (and other ISPs) of the Sandvine traffic shaping system which spoofs TCP Reset packets as a way of controlling bandwidth for either customers using BitTorrent peer-to-peer file transers, or in our case, anyone generating higher than "normal" bandwidth spikes.

This is causing severe interruption of the normal flow of Internet traffic by exploiting one of the built-in functons of the TCP protocol.

Apparently the game server is running an ubuntu distribution (although I'm afraid I don't have information as to which version is currently being used), and I've found an article which suggests using netfilter to block the TCP RST flag packets as a means of preventing the interruptions.

The administrators of the game implemented this method in the past few days, and in conjunction with a firewall running on players' local machines blocking the RST packets being sent in the opposite direction it appears to be helping the problem.

However, the game server has begun running extremely slowly, causing severe lag for all players, not just those affected by the Resets (I myself haven't experienced the problem since I use an AT&T DSL link to the Internet and running the Ethereal packet sniffer on my end shows no unusual RSTs coming in).

Another player with ubuntu experience has theorized that unclosed connections are building up in memory and eventually taking over all the available system resources, causing the lag.


My question is:  Can anyone think of a better way to prevent the interference from these exploited RST flag packets..?

Or, a way to resolve the issue of unclosed connections caused by blocked RSTs..?

(We've considered adding a blocking rule in the router protecting the game server, but are concerned this will result in the same problem on the server since normal RSTs won't be able to get through either.)

Thanks for any advice anyone might have..!
BobR

---


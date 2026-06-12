---
title: "OpenVPN, can ping , but not see another on it.."
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by pzhukke on 2008-05-18
Hi!

Yeah as the topic says:

On my VPN, I'm able to ping every client that is on it, but when I start like Counter Strike or any other game, I can't see any games on LAN...
But if I like (in Counter Strike) type the IP of the server, and connect, it will work!
So I can connect to the servers on the LAN, if I know the ip and connect that way, but not every game supports that..

So my question is:
How do I solve this problem; How do I configure my VPN to allow clients to actually see eachother?
I mean, we can ping eachother, but not "see" eachother, d'you get my point?

Regards.
Eric.

---

### Post by SpaceTeddy on 2008-05-18
this is not acctually a problem with counterstrike, but with your basic setup of the vpn. I guess that you set your vpn up to use tun devices and used the "server" switch in your config of the server. 

This will create a **routed** vpn. Why is that imporant ? Because in a routed enviroment the broadcasts (which counterstrike send out to find servers in a LAN) will not pass through a routed environment, thus makeing it impossible for counterstruke to find any servers in the LAN. The easy solution to that is to use hamachi instead of OpenVPN.

What you need to do to get this working with OpenVPN is to create a bridged vpn via TAP devices (ultimatively using layer 2 routing instead of layer 3) so that the broadcasts will pass over your vpn. However, i must point out that this will cause A LOT of traffic for your VPN server, as any broadcast will be going over it.
I have only done this together with bridging and point-to-point connection before, but the basic steps to set this up should be found [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127") in part two of the turorial. However, this is **NOT** the exact setup you want as this describes how to bridge networks together - not having a layer 2 vpn with multiple clients. 

If you cannot make sense of that tutorial, please post your server and client config file, and i will see if i can modify them to work with layer 2.

hope it helps :)

PS: 
layer 2 = MAC layer = any non-routed enviroment
layer 3 = IP layer = any routed enviroment

---


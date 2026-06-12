---
title: "Unstable networking"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by ZGStyle on 2006-11-11
Hi
I was happy Kubuntu 6.06 (Dapper) user for a couple of month.
Recently I did fresh install of Kubuntu 6.10 (Edgy) and now I have a problem with my network connection. I have spent whole day trying to resolve this problem by myself,but unsuccessfully :(.
I can't listen to my music which is on server, can't listen to Internet radio stations without interruptions - I get disconnected after every 1-3 min.
As I mentioned before - hardware is the same, ISP the same, only difference -  new version of Kubuntu.
An here is what I'm getting after dmesg:

[17180195.480000] eth0: Media Link On 100mbps full-duplex
[17180261.488000] eth0: Media Link Off
[17180271.496000] eth0: Media Link On 100mbps full-duplex
[17180412.520000] eth0: Media Link Off
[17180427.532000] eth0: Media Link On 100mbps full-duplex
[17180528.540000] eth0: Media Link Off
[17180543.552000] eth0: Media Link On 100mbps full-duplex
[17180574.552000] eth0: Media Link Off
[17180584.556000] eth0: Media Link On 100mbps full-duplex
[17180620.568000] eth0: Media Link Off
[17180635.580000] eth0: Media Link On 100mbps full-duplex
[17180671.580000] eth0: Media Link Off
[17180686.588000] eth0: Media Link On 100mbps full-duplex
[17180867.608000] eth0: Media Link Off
[17180877.616000] eth0: Media Link On 100mbps full-duplex
[17180913.616000] eth0: Media Link Off
[17180928.628000] eth0: Media Link On 100mbps full-duplex
[17180959.636000] eth0: Media Link Off
[17180974.648000] eth0: Media Link On 100mbps full-duplex
[17181015.648000] eth0: Media Link Off
[17181030.656000] eth0: Media Link On 100mbps full-duplex
[17181056.668000] eth0: Media Link Off
[17181071.680000] eth0: Media Link On 100mbps full-duplex
[17181202.692000] eth0: Media Link Off
[17181212.696000] eth0: Media Link On 100mbps full-duplex

Please help!

---

### Post by skyler91 on 2006-11-11
I'm having the same problem with mine right now.  My networking seemed to work just fine for several weeks after installing 6.06 but now my connection just cuts out every few minutes.  I've found out that if I go into network settings and disable, then re-enable my eth0 card, it will start working fine again for a few minutes, but this is getting really annoying because I can't really download or stream anything.  I'm connecting from my eth0 card through a Linksys router, then to my cable modem.  I have a second computer on the same network running Windows XP and it never seems to have these problems at all.  Any help would be greatly appreciated!

---

### Post by ZGStyle on 2006-11-12
OK. Seems I have found problem ;)
It's not Kubuntu fault, but my router.
I have EUSSO wireless router (UGL2454-RTA). This is second router which I have - first just got broken and I got this by warranty.
I discovered when I TURN ON wireless, LAN connection gets dropped every 1-3 min, so there is problem with router hardware of firmware.
I have Windows on my PC as well (using VMWare) and it seems Windows can handle these short networking interruptions.
Conclusion - don't by EUSSO router ;)

---

### Post by BlueNoteMKVI on 2006-12-06
For anyone else who comes across this thread - 

I have a similar problem.  I don't think it's the router, but I do think it's hardware.  

My desktop was having this problem yesterday.  I upgraded to 6.10 hoping it would be solved, but no luck.  Today I came here to find a solution and found this thread.  I thought the problem was not hardware, because my laptop (running 6.06) did not have the problem, neither did my Windows box, so the router is good.  Just for fun I switched the cables around, plugging my laptop in where my desktop was, and now the laptop has the problem and my desktop does not.  Looks like I need to open up the wall and check the socket.

---


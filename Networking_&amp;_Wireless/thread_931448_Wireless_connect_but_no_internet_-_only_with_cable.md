---
title: "Wireless connect but no internet - only with cable"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by mamendes on 2008-09-27
Hi,

I have a wireless connection here that I'm able to connect and gain ip (192.168.1.200) address from the router (which is 192.168.1.1). But after that, I cannot access Internet, I cannot solve [www.google.com](www.google.com), I don't even can ping the router (192.168.1.1).

The connection info (at NetworkManager) seems all ok: ip, broadcast, mask, default route, dns's...

Then I simply plug the cable into the router, wlan0 gets down, eth0 gets up, I gain another address (192.168.1.201) and I can use Internet and life is good again.

Keep in mind that I used to use it only with the wireless connection, It started to act weird since yesterday night.

Does anyone has any suggestions? Thanks!

---

### Post by sdowney717 on 2008-09-27
are you really connected to the router?

if so, then can you ping a web address? using both name and octet number address. 

Perhaps the DNS settings for the connection are messed up. If DNS is not working, you cant browse but you can ping the octet address number.

---

### Post by mamendes on 2008-09-27
I cannot ping anything, not even the router (gateway)!

When I do an ifconfig before connecting to the wireless network, the interface has no ip nor gateway. After connecting, it gains ip and gw. I don't think this information can be cached or something, can it?

If it's not really connecting just saying so things are even more weird :/

---

### Post by mamendes on 2008-09-27
More info:

When ubuntu starts, the wireless network connects and I can ping [www.google.com](www.google.com), install stuff with apt-get, etc.

But when I run firefox3... The connection gets `void`.

Here is dmesg before running ff3:

   73.407620] NET: Registered protocol family 17
[   76.859704] wlan0: Initial auth_alg=0
[   76.859713] wlan0: authenticate with AP 00:16:b6:99:99:99
[   76.862207] wlan0: RX authentication from 00:16:b6:99:99:99 (alg=0 transaction=2 status=0)
[   76.862212] wlan0: authenticated
[   76.862218] wlan0: associate with AP 00:16:b6:99:99:99
[   76.864580] wlan0: RX AssocResp from 00:16:b6:99:99:99 (capab=0x411 status=0 aid=1)
[   76.864585] wlan0: associated
[   76.866554] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   76.957921] padlock: VIA PadLock not detected.


Here is the ping [www.google.com](www.google.com), you can see when I ran ff3:

64 bytes from br-in-f104.google.com (209.85.193.104): icmp_seq=410 ttl=246 time=24.5 ms
64 bytes from br-in-f104.google.com (209.85.193.104): icmp_seq=411 ttl=246 time=23.9 ms
64 bytes from br-in-f104.google.com (209.85.193.104): icmp_seq=412 ttl=246 time=23.9 ms
64 bytes from br-in-f104.google.com (209.85.193.104): icmp_seq=413 ttl=246 time=23.9 ms
64 bytes from 209.85.193.104: icmp_seq=414 ttl=246 time=24.1 ms
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available

Does it make any sense at all?

BTW I installed Opera and it does not close the connection, only firefox.

---

### Post by sdowney717 on 2008-09-27
how about doing a complete firefox reinstall. synaptic complete removal and then reinstall.
How does firefox 2 work?

---

### Post by superprash2003 on 2008-09-28
please post an output of ifconfig

---

### Post by mamendes on 2008-09-28
> **sdowney717 said:**
> how about doing a complete firefox reinstall. synaptic complete removal and then reinstall.

Same thing, except that for the first time I called firefox3 (after reinstall, before restarting) it did not happen. But after the first restart, the first page I call in firefox and I get the "no buffer space available".

> **sdowney717 said:**
> 
How does firefox 2 work?

Same thing as firefox 3.

So far I'm limited to Opera. I'll try a torrent client to see what happens.

---

### Post by donec on 2008-09-28
I just switched from cable to DSL and had a similar problem. The fix was to access the router and setup a PPPoe user name and password. This was required to access the internet service. Maybe there is something in this that may help you.

---

### Post by mamendes on 2008-09-29
No, that is not the problem, I can browse throw the others computers on the router.

The connection become mute (it does not drop) almost always when I open the first url with Firefox. Opera is fine, torrent is fine.

When this happens, I have to bounce the rtl8187 so as I can bounce the wlan0.

I read somewhere that would be a known bug, and to limit the speed of the link would avoid it. So, I'm keeping the wireless network speed to 2 mb/s and avoiding firefox.

I would not call this a reasonable solution :) but so far it's the only one I have.

---


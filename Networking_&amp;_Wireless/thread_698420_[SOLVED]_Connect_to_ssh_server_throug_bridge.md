---
title: "[SOLVED] Connect to ssh server throug bridge"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by clauguia on 2008-02-16
I have an Ubuntu laptop that I can connect to Internet either by plugin it directly to an ADSL router or by wireless connection to a Windos XP machine wich is conected to the ADSL router. I also have an Ubuntu SSH server connected directly to the ADSL router.

When my laptop is wired, I can connect to the ssh server and thats fine. What I want to do is to connect to the ssh server via the Windows bridge, like this:
[HTML]
                             +-----------------+       +---------------+
                             |   Machine A     |       |   Machine C   |
                             |   Windows XP    | <~~~~>|   Ubuntu      |
                             | Netw. B  Wlan   |       |    Wireless   |
                             | 162.198.0.1/100 |       | acc. Intern.  |
                             | Bridges to Int. |       | through Mac.A |
                             +-------+---------+       +-------+-------+
                                     |                         )
                                     |                         ( How to?
                                     |                         )
    +-------+-------+        +-----------------+       +-------+-------+ 
    |               |        |  Modem ADSL     |       |   Machine B   |
    |  The Internet |        |  Router         |       |    Ubuntu     |
    |               |<------>|  Network A      |<----->|   SSH Server  |
    |               |        |  10.1.1.1/24    |       |               |
    +---------------+        +-----------------+       +---------------+
[/HTML]

I think it must be very simple, since I've seen a lot of more difficult issues over the internet. I just counld't find a tutorial for this.

---

### Post by nixscripter on 2008-02-21
If what you have is this:

1. Machine A is a bridge. It will just forward the stuff back and forth. It gets its IP from the ADSL router.
2. Machine B is a server. It gets its IP from the ADSL router.
3. ADSL router will forward packets to the SSH server from machine A.
4. Machine C gets its IP address from Machine A.

I don't see why you couldn't just: ```
 ssh you@ssh_server
``` from Machine C. Did I miss something?

If you are unable to get from Machine C to B, e.g. ping it, what is the error you get?

---

### Post by clauguia on 2008-02-24
You got it right, nixscripter. Sorry if it was not clear.

Machine C can ping Machine A but cant ping the router nor the ssh server. The ip of Machine C is 168.192.1.30 and it sees Machine A as 168.192.1.1 . It says host unreachable.

Machine A has an wireless ip of 168.192.1.1 and an wired ip of 10.1.1.5 and can ping all.

I should mention that Machine A has an USB wireless dongle connected to Machine C through an ad-hoc connection. Also, it was not configured as bridge, but it merely forward internet to the wireless connection. Maybe that is the problem.

This is now a theoretical question to me, though. A lightning brought an end to my modem and I bought an wireless router that places all my computers in one net range.

---

### Post by nixscripter on 2008-02-25
I suspect it was a routing problem. "Network unreachable" usually means that the sending computer doesn't know where to send the packet to get it to its destination. You know the correct answer would be for Machine C to send it to Machine A, but if that wasn't in the routing table, it wouldn't know that. It could also have been machine A was misconfigured.

In any case, I'm glad the problem is solved. Er, not that your modem got hit by lightning, but you know what I mean ;-)

---

### Post by clauguia on 2008-03-10
Yes, I understand. I was afraid that would be the answer. As Machine A 's plataform is Windows, I don't know how to configure it correctly. Reading some tutorials I found out that there's also some way to make a bridge in Windows, maybe that would be an answer. Too late to test it now. Thanks.

---


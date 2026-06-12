---
title: "Odd transient network issue"
date: 2015-12-02
forum: Networking &amp; Wireless
---

### Post by xiano8494 on 2015-12-02
I have posted this issue to AskUbuntu, but I feel it might not be appropriate there.

I have a strange problem that has been affecting one of my internal web servers. Reports were coming in occasionally that users were unable to authenticate with a web app on the server, the app was reporting the Windows DC it was using for authentication wasn't responding. The same DC was used for DNS resolution so I couldn't ping by host-name, I tried pinging the domain controller and got no response. Before I could do any further investigation everything came back up.

The problem then reoccurred, this time I had Wireshark ready and watched the traffic on the Domain Controller. I could see the ping requests from the web server and the replies from the domain controller going back in the Wireshark view, but the web server was showing 100% packet loss.

Whilst Wireshark was running I could also see numerous name resolution requests coming in and being replied to, but the web server was not receiving them.

I did wonder about some kind of rate limiting, but there is no active firewall on either boxes at the moment. Other boxes on the network can communicate with the web server fine, and it can communicate with them.

Rebooting the web server solves the problem temporarily, there doesn't seem to be a pattern to when it stops working.

I'm at a bit of a loss what to try next. Any ideas?

---

### Post by The Cog on 2015-12-02
My next step would be to run tcpdump on the webserver, and see if the replies really do reach the webserver, or whether they are being lost in the network somehow.

Do you have separate public and back-end NICs? I wonder if the back-end connection is just losing all receive traffic for a while for some reason.

---

### Post by xiano8494 on 2015-12-02
Hi,
Thanks for your reply.
I did as you said and couldn't see the packets reaching the server.
Turns out they were getting lost in the network.  I checked the WireShark capture in more detail on the DC and noticed the MAC addresses didn't match.  Turns out the firewall was doing proxy arp as discussed here: [http://www.cisco.com/c/en/us/support/docs/security/adaptive-security-appliance-asa-software/116154-qanda-ASA-00.html](http://www.cisco.com/c/en/us/support/docs/security/adaptive-security-appliance-asa-software/116154-qanda-ASA-00.html) and the DC was therefore sending the packets to the firewall not the web server!  The fix suggested on that article fixed my problem.

---

### Post by The Cog on 2015-12-02
Oh, well played!
That would have taken me quite a while to find.
You can mark the thread solved using the Thread Tools pull-down menu at the top of the page.

---


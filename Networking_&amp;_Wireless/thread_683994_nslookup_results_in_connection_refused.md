---
title: "nslookup results in connection refused"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by dbrower256 on 2008-01-31
I have a Ubuntu 7.10 Server running a dns service and a Ubuntu 6.10 Desktop running as a dns client.  When I run nslookup for [www.microsoft.com](www.microsoft.com) (or any public domain name) I get a message saying that connection was refused?  What does this mean?  It seems to me that the dns server forwards the query to a dns sever provided by my ISP but the query was refused service?  What do I need to resolve this?

Daniel

---

### Post by ssuehr on 2008-02-01
In general, if you have a client querying a DNS server for a record for which that server is not authoritative, the DNS server will look at its root hints, query a root server for the authoritative DNS server for that zone, and then the local server will forward the request on to the authoritative server for that particular zone, eventually returning the result to the client.  If the local DNS server is accepting recursive queries then it wouldn't be talking to the ISP DNS server at all.

If you're receiving connection refused on the client, then whatever server is being queried doesn't seem to be listening.  Try manually changing the server to your ISPs server - also try using the 'dig' command.

---

### Post by dbrower256 on 2008-02-04
> **ssuehr said:**
> In general, if you have a client querying a DNS server for a record for which that server is not authoritative, the DNS server will look at its root hints, query a root server for the authoritative DNS server for that zone, and then the local server will forward the request on to the authoritative server for that particular zone, eventually returning the result to the client.  If the local DNS server is accepting recursive queries then it wouldn't be talking to the ISP DNS server at all.

If you're receiving connection refused on the client, then whatever server is being queried doesn't seem to be listening.  Try manually changing the server to your ISPs server - also try using the 'dig' command.

I feel I should clarify my problem and my purpose.  I'm trying to get a local dns server running on Ubuntu just for the sake of learning how.  I have set the forwarders to the dns servers of my isp.  I set a client to use my dns server.  When I do nslookup for an address in my local network, I get a result.  However, when I do nslookup for [www.microsoft.com](www.microsoft.com) or a domain that is on the internet, I get a message saying something like I was denied a connection or that my query was denied.  

When I use a Windows Server 2003, everything works just fine.  I've set up the zones and used the A and PTR commands for the dns server and the clients like I should.  Nevertheless, thanks for replying.  Perhaps you could suggest something else to me.

---


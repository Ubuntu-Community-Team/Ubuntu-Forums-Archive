---
title: "Encrypt traffic from Server(s) to 100k nodes"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by Luis_Ramos on 2014-03-26
Hi guys,
Can someone point me to the right direction?
I'm working in an application that requires to encrypt (or at least protect) the traffic to it's nodes. For scalability I always like to aim high.
The traffic being transmited will be plain text constantly and a few images a day.
My first thought was Tunnels, but I don't think they can escalate that high.
Any response will be very appreciated.

---

### Post by Kirboosy on 2014-03-27
Welcome to the forums!

You are being very vague and its quite difficult to help you here. Please read the following post with tips on how to get your post answered as quickly as possible.

[Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475&p=8920811&viewfull=1#post8920811")

Hope that helps!
~Caboose

---

### Post by SeijiSensei on 2014-03-27
> **Luis_Ramos said:**
> My first thought was Tunnels, but I don't think they can escalate that high.
Any response will be very appreciated.

I'm pretty sure you could set up that many tunnels with OpenVPN, but you might need multiple servers to handle all the connections.  With proper routing I think it's feasible.

If the traffic is largely one-way from server to node, I suspect HTTPS is the best choice.  Web servers easily handle 100K connections per day or more.  The nodes need only an HTTPS-enabled client like wget or curl.  If there is upstream data, using [POST]("http://en.wikipedia.org/wiki/POST_%28HTTP%29") over an HTTPS connection might still be a better choice than 100K tunnels.

---

### Post by Kirboosy on 2014-03-27
He could also use SSH and bind it for specific ports that way it doesn't interfere with the rest of his network traffic

~Caboose

---


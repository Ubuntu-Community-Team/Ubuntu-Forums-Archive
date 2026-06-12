---
title: "How to redirect traffic?"
date: 2018-05-03
forum: Networking &amp; Wireless
---

### Post by fourirakbar on 2018-05-03
Sorry if this is strange question, but this is make me crazy right now.

I use ubuntu 16.04.
I have a topology like this: [IMG]https://ibb.co/iW18in[/IMG][https://ibb.co/iW18in](https://ibb.co/iW18in)
By the way, sorry if I post a link to open the image. I can't upload an image here...

In the past, I have an system that let client to access internet. The traffic like this: CLIENT - SERVER - ROUTER - INTERNET

First what I do:
in server I make a rule : IPTABLES -t nat -A POSTROUTING -o wlp3s0 -j MASQUERADE -s 192.168.99.100
So the client who have IP 192.168.99.100 can access internet

Now, I want to make traffic like this : CLIENT - SERVER - CONTAINER - SERVER - ROUTER - INTERNET. Like the image topology above. The container is inside the server.
In container have 2 interface, eth0 (172.17.0.2) and eth1 (172.19.0.2)
Gateway from eth0 and eth1 is on the server.

I don't understand how can I redirect traffic to the container?
[IMG]https://ibb.co/iW18in[/IMG]

---


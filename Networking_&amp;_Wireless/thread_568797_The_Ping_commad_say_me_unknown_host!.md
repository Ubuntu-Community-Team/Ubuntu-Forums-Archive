---
title: "The Ping commad say me unknown host!"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by tofighi on 2007-10-06
when I use **nslookup** I can find the ip of** client.domain.local**  but when I ping it I see unknown host, how can I resolve this problem?

---

### Post by tofighi on 2007-10-08
I find out a solution,I don't know is it really best solution or not but I use bind to solve the problem.
adding the server in resolve.conf didn't lead to forwarding dns server.
but you can add this to your bind forwarders:

> vi /etc/bind/named.conf.options 

then add this section (or uncomment it) (this is an example for dns servers on 10.0.0.2 and 10.0.0.3)

> forwarders {
10.0.0.2;
10.0.0.3;
};

---


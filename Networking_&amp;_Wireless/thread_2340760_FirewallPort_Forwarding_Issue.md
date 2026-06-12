---
title: "Firewall/Port Forwarding Issue"
date: 2016-10-21
forum: Networking &amp; Wireless
---

### Post by jpark830 on 2016-10-21
Hello. I am in very weird situation.

So I am using ubuntu webserver(192.168.0.1 listening on port 80), and another small server for my side rails app project server.(192.168.0.4 also listening port 80)

I was messing around with iptables, but set everything back to how it was before.

now when i enter the ip address on the web browser, the traffic gets forwarded from the webserver to teh rails app project server,
so the contents from the project server pops up on the browser not the contents of the original webserver.

even when i enter the domain name of webserver 192.168.0.1, "example.com" to the address bar and try to access, still same thing, it gets forwarded to project server. =(

I am not familiar with ubuntu firewall nor iptables. does anyone have idea what is gonig on with my server?

---

### Post by nathan-linux-sa on 2016-10-22
Hi

On the webserver (192.168.0.1), run the command below to check the nat table in iptables and send the output

```

sudo iptables -t nat -L -vn

```

Note: I am assuming you are trying to achieve the above from the local lan.

---


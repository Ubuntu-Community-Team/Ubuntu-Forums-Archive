---
title: "Not accepting incoming TCP connections"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by Ariod on 2007-08-04
Hello!

I'm using Ubuntu 7.04 with Open Diameter installed. Now, I'm trying to run some Open Diameter test applications, a client and a server. They can make connection to each other through localhost just fine, but when I tried to run them on separate computers (both running Ubuntu 7.04), TCP connection cannot be made. I've tried sniffing with Wireshark and I see two packets. The first one is a SYN packet going from 192.168.1.103 (client) to 192.168.1.104 (server). The other one is a RST/ACK packet going from server to client.

What could cause the server returning a RST packet? I don't have a firewall installed, unless Ubuntu has a preinstalled firewall (though, iptables show no rules).

Thanks for any suggestions.

---

### Post by noob12 on 2007-08-04
I suspect your server is only listening on loopback.

Can we see

```

netstat -tnl

```

---

### Post by Ariod on 2007-08-06
Here is the output of netstat:

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.1.1:1812          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN  
```

Does this mean that OpenDiameter (second line) really is listening on localhost? And why is it "127.0.1.1" instead of "127.0.0.1"?

I'd also like to note that I'm not using superuser privileges here. Does this matter for servers?

---

### Post by noob12 on 2007-08-06
Yes.  The local address should be 0.0.0.0 if you want it accessible on all interfaces.

The 127.0.1.1 address suggests that the service is looking up your hostname and using that to choose the interface to listen on.  See the entry for your hostname in /etc/hosts.  But I wouldn't change that.

Instead, many services will have a config that lets you set up which interface(s) they listen on.  Check the docs for the OpenDIameter service (I'm not familiar with that specific service) and see if you can specify the listen interfaces.  Then specify 0.0.0.0 to specify listening on all interfaces or the ip address of a specific interface, which is presumably statically assigned, if you only want to listen on a specific one.

---


---
title: "[SOLVED] Web Server"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by theozzlives on 2008-10-24
I have a static IP, and was wanting to put my web server in front of my router, and the rest of my network behind the router. The problem is no matter what I do, I lose connectivity behind the router. My cable modem is plugged into ETH1 and ETH0 goes to the router. ETH1 has my IP info and ETH0 is set to DHCP, my router is set to dynamic IP. Does someone have a solution?

---

### Post by lswb on 2008-10-24
The conventional approach would be to connect the router to the cable modem and use Network Address Translation to send web traffic to the server. i.e. incoming traffic addressed to your static ip would first go to the router, and the router would relay those packets that use port 80 ( or whatever other ports you specify) to your server on the local net. This will also keep nuisance and malicious incoming traffic from hitting your server. The router can be configured to ignore unwanted traffic, for instance if your server is running only a web server, the router won't bother it with ssh, telnet, mail, etc. requests that might come in. Some of this unwanted traffic will be from malicious sites looking for a way in to your server.

What you propose is possible with network connection sharing, but consider that all internet traffic will have to pass through your server _before_ it even gets to the router. If your local net has a significant number of other systems on it it will put a load on the server that would more easily be handled by a router in a conventional configuration.

Is there some reason why you want to have all traffic going through the server before the router?

---

### Post by theozzlives on 2008-10-25
My web server is being assigned 192.168.1.4, that's a private IP.

---

### Post by lswb on 2008-10-25
> **theozzlives said:**
> My web server is being assigned 192.168.1.4, that's a private IP.

Isn't that address being assigned by the router? Check your router documentation. 

Your local net should be set up something like this:
```

  |M|     |R|
  |O|     |O|------[WorkStation]
  |D|-----|U|------[WorkStation]
  |E|     |T|------[Server]
  |M|     |E|------[WorkStation]
          |R|

```

Your router will be configured so that incoming http requests will be sent to the server. The router will handle any necessary address translation between the internet and your local net. Maybe I'm misunderstanding what your goal is?

I take your original post to mean that you propose to set up your net like this:

```

  |M|              |R|
  |O|              |O|-----[WorkStation]     
  |D|---[SERVER]---|U|-----[WorkStation] 
  |E|              |T|-----[WorkStation]  
  |M|              |E|
                   |R|

```

While it is possible to do it this way there are lots of good reasons for NOT doing so. Unless you have some unusual needs, I would avoid this. Do some googling on "network address translation" and "ip masquerading" then find out how to configure your router and server to work together.

---

### Post by j.bunce on 2008-10-25
From a security perspective, the best thing to do would be to create a separate vlan, and place that into a DMZ. If your router supports it. Otherwise you'll have to use port the port forwarding option.

---

### Post by theozzlives on 2008-10-25
I got port forwarding, today I setup http to go to 192.168.1.4

---

### Post by Iowan on 2008-10-25
Port forwarding will work better if the router is between the internet and the server - otherwise the signal probably won't get to the router to be sent back to the server... not to mention the aforementioned benefits of having the router as a (partial) firewall.

---


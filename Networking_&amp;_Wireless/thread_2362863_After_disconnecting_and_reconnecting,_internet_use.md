---
title: "After disconnecting and reconnecting, internet uses only ipv6"
date: 2017-06-02
forum: Networking &amp; Wireless
---

### Post by leozinho29_eu on 2017-06-02
Hello

I have an Asus M2400Ne with a Intel Corporation PRO/Wireless 2200BG [Calexico2]. However, sometimes the internet disconnects due to low signal and then, when it reconnects, it tries to use only ipv6, ignoring completely the ipv4. The big problem of this is that the internet where I live uses only ipv4. So, while it can connect to the router again, it will never receive data from outside the local network, as it tries to use exclusively ipv6, which is not available. 

When this happens, it is simply impossible to connect in any way: both Wireless and Ethernet refuses to use ipv4. The only way I have found to make it use again ipv4 is rebooting the computer.

This is not a new problem, but only recently I understood this details. What should I do to make the computer understand that it can, and should, use ipv4?

Thank you.

Edit: the system version is Lubuntu 16.04.2 i386.

---

### Post by chili555 on 2017-06-02
Did you try editing connections in Network Manager to tell it to ignore IPv6? This is for ethernet, but you want wireless.

[https://digitizor.com/wp-content/uploads/2009/11/disable-ipv6-network.png](https://digitizor.com/wp-content/uploads/2009/11/disable-ipv6-network.png)

---

### Post by leozinho29_eu on 2017-06-03
This solution could solve the problem with one particular network, but the problem seems to be bigger.

However, I believe I have found the true cause of the issue.

Somehow, instead of reconnecting to the network it was connected, the computer sometimes create a new connection to the same network, so there would be something like:

Network
Network2
Network3
... 
Network9
Network10

The router has only one network, but there would appear many different connections on the computer. The router's logs are filled with disconnections and connections from the computer's MAC address. Even when it is working perfectly (to the user), the router logs many disconnections and reconnections.

Any of those different options connect to the router. Most of the times, when it disconnects from Network2 (for example), it would reconnect to Network2. But it could fail and would create a Network3.

Another complicating factor is LogMeIn Hamachi. It has a connection (ham0), and it could be assigned as the default one when the reconnection failed. When this happens, the internet would stop working.

So there is a configuration problem, which creates many connections for the same network (same router, same configuration) and then the Hamachi connection may become the default. 

While removing Hamachi would (probably) solve, I need Hamachi, so I would need to find a way to make it don't create many different connections to the same network.

---

### Post by leozinho29_eu on 2017-07-28
I have found the problem and I became surprised with it. The problem was ntpd. I am not sure about how it caused this, but my hypothesis is that it conflicted with systemd-timesyncd in such way the result would be connectivity loss due to DNS problems. The solution I chose was purging the ntpd package and use systemd-timesyncd instead. With Lubuntu 16.04, using dnsmasq and systemd-timesyncd the internet was working.

I have upgraded it to Xubuntu 17.04 and now it is using systemd-resolved and systemd-timesyncd and it is working too.

---


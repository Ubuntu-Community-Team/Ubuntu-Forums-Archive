---
title: "How to FreeNX from remote location?"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2007-04-26
I have successfully set up the NoMachine Server(Ubuntu PC) & Client (WinXP) & can connect perfectly with SSH on a home wireless network.


My question...in order to connect to the Server, from the Client, while on a network outside of my home network (say...another city/state/internet connection), what would I need to add in the "server host" filed of the NoMachine Client?

In the home network, I just need to add the internal IP of the Server, & I'm connected.

Do I need to add anything else to that, from the outside network connection?


Thanks alot!

---

### Post by DapperMe17 on 2007-04-28
bump

---

### Post by hugmenot on 2007-04-30
You need to know the IP address that that your home server is on the itnernet with.
Either it is static, then you can always just enter your internet facing IP, or it&#8217;s dynamic, then it will be helpful to setup a dynamic DNS resolver for your home server. There are plenty of free solutions for that like dyndns.org. Usually your NAT router device (if you have one) has an inbuilt function to update your address (like e.g. my-home-nx.dyndns.org) with the currently assigned IP.
Then you&#8217;ll need to map the SSH port properly to your server at home so that the connections from outside are forwarded to the SSH-server. Since NX transparently utilizes your SSH port it is the only port that has to be open.

---

### Post by DapperMe17 on 2007-04-30
Ok,

Hypothetically,

Let's say its a static IP address....for example 12.345.67.890....with the Ubuntu machine IP (NX server) as 192.169.0.001, with a wireless router with IP 192.169.0.0.


What would I type into the NXClient server host box?

Would I also have to port forward port 22 in the router, or are you saying it isn't required, due to the NX transparency?

---

### Post by hugmenot on 2007-05-01
> **DapperMe17 said:**
> Would I also have to port forward port 22 in the router, or are you saying it isn't required, due to the NX transparency?

You definitely need to forward port 22. The transparency just consists of NX piggybacking onto your SSH port (i.e. 22).

The port forward short circuits your outside IP to the IP of the PC running SSH cum NX on your internal LAN.
So, to connect to it you use the outside IP from abroad and the real internal IP if your sitting next to it.

---

### Post by DapperMe17 on 2007-05-01
Thanks!


I'll try that, by typing the outside IP address of "123.456.7.890" into the NXClient Host box. 


From there, as long as I've port forwarded the router to the internal Ubuntu IP, I should be in business...

---

### Post by DapperMe17 on 2007-05-02
Works like a charm!



Thanks much for all the help.

---


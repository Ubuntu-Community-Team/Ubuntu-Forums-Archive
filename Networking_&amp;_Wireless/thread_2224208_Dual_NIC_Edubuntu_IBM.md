---
title: "Dual NIC Edubuntu IBM"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by mehraks9 on 2014-05-15
I have installed edubuntu on IBM Server X series with two nic.In my setup the eth0 is connected to switch and eth1 is connected to my Belkin router with other windows pc. Client booting is fine with above setup but internet access to other windows pc and wifi devices get disconnected.I have been working on this for last two weeks to sort out the issue but can't.many resources on internet seems to be similar but without amy solution.
What I want is to have net access to all my windows pc as well as edubuntu clients with same router and switch.I have tried modifying network interfaces, ltsp configuration and so on but endup with fresh installation.what if eth1 can be configured to my router ip?
I am setting up computer lab in my school where each pc can pxe boot edubuntu from Ibm server and and normal boot from from local hard disk.
kindly suggest any link or help resources....

regards

---

### Post by mehraks9 on 2014-05-18
I m little disappointed that no member is replying.Is there any information missing in my post?

---

### Post by spynappels on 2014-05-18
Can you please detail your network topology a little more?

The network segment connected directly to the router, that's the normal network, right?

The other switch is for the nodes booting from servers? These nodes connect to the network through the Edubuntu server?

---

### Post by spynappels on 2014-05-18
Thinking about this a little more, the following are some general things to bear in mind. I am not very familiar with Edubuntu, these are more general considerations from a network perspective.

On the server, you need to make sure that IP forwarding is enabled in the kernel. Your server is essentially a router for the nodes behind it. To check if it is enabled, run the following:
```
cat /proc/sys/net/ipv4/ip_forward
```
If a 1 is returned, packet forwarding is enabled.
If a 0 is returned, you can enable it by doing the following:
```
sudo echo "1" > /proc/sys/net/ipv4/ip_forward
```

You may also need to adapt/adjust the iptables rules to permit the traffic to pass.

---


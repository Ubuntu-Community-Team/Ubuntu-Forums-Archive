---
title: "Cannot be pinged"
date: 2014-05-14
forum: Networking &amp; Wireless
---

### Post by iExchange128 on 2014-05-14
Hello,

I just got the latest version of ubuntu on my desktop computer which is connected to my home network via a wired connection.  My mac laptop is connected to the same network wirelessly. The problem is that my mac laptop is not able to ping my ubuntu desktop computer? Yet, the ubuntu desktop is able to ping my mac laptop.

Additional Info: 
1. The built in firewall on mac is disabled. The UFW firewall on ubuntu is disabled too.
2. The desktop uses a static IP while the laptop is getting an IP from DHCP on the router.

I wonder what commands should I use to find the source of problem and resolve it?
Thanks!

---

### Post by HiImTye on 2014-05-14
what's the output of```
sudo iptables -L | grep 'echo-request'
```and is your mac in the same block as your Ubuntu computer?

---

### Post by iExchange128 on 2014-05-16
This is what I get:
```
ACCEPT icmp --  anywhere  anywhere  icmp echo-request
```
It sounds like there's no problem with that part?

And what do you mean by 'block'? Sorry for the questions...

---

### Post by HiImTye on 2014-05-16
I mean the same /24
yeah, iptables looks ok

---

### Post by spynappels on 2014-05-16
Are you pinging by hostname or IP address?

---

### Post by iExchange128 on 2014-05-16
> **HiImTye said:**
> I mean the same /24
yeah, iptables looks ok
Yes they are in the same subnet

> **spynappels said:**
> Are you pinging by hostname or IP address?
IP address

---

### Post by HiImTye on 2014-05-16
can your ubuntu machine ping it's own ip?

---

### Post by iExchange128 on 2014-05-16
> **HiImTye said:**
> can your ubuntu machine ping it's own ip?
Yes it can

---

### Post by HiImTye on 2014-05-16
then this suggests that the issue is with the Mac or the router

---

### Post by iExchange128 on 2014-05-16
> **HiImTye said:**
> then this suggests that the issue is with the Mac or the router
I see, could you tell me what kind of settings on the router might cause this?

---

### Post by spynappels on 2014-05-16
I'm not sure about what to check on the Mac (not having used one) or the router (not knowing what it is) but I can help you to confirm or deny whether it is an issue with the Ubuntu box.

You should take a network capture on the Ubuntu box, looking for ICMP packets to check if they are getting to the Ubuntu box. I'm assuming that you have tcpdump on your Ubuntu box, if not you can get it using
```
sudo apt-get install tcpdump
```
You can check whether you are receiving and/or respong to pings by doing the following:
```
sudo tcpdump -i eth0 "icmp and net 192.168.1.0/24"
```
adjust the interface and network range as required.

For each ping you get, a line should be written to the screen, with another line for each response you send. No packets written to the screen means you're not getting the pings, only having inbound packets written to the screen means you're not processing them and printing both to the screen means your replies are not getting to the host doing the pinging.

---


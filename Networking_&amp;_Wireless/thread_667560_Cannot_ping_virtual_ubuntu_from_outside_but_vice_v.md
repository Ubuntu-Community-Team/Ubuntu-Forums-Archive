---
title: "Cannot ping virtual ubuntu from outside but vice versa can ping"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by yanny on 2008-01-14
I have installed Ubuntu desktop edition in VMware on a Windows XP computer. 

I got a macbook (laptop) and another Windows computer (Vista), these three are using the router to connect to the internet.

Using Vista & Mac I cannot ping to Ubuntu ip-address which is 192.168.91.137 (this address I got when I type ifconfig: inet addr 192.168.91.137).

I can ping with Windows XP (computer with VMware)  to Ubuntu ip-address. Also from Ubuntu itself I can ping to Windows XP, vista & mac ip-address.... They all have connection to internet.

I had installed SSH server at the Ubuntu, I forwarded only SSH port with portnumber 22 and ip-address 192.168.91.137 at my router's settings page.

Because PING doesnot work, so did SSH.

Do you know what is wrong here? Thanks!

---

### Post by HermanAB on 2008-01-14
Well, check the Ubuntu firewall settings:

$ sudo iptables -L

Also, you should use VMware Bridged ethernet, not NAT ethernet.
(This is most likely the problem, since Ubuntu ships with iptables disabled)

Cheers,

Herman

---

### Post by yanny on 2008-01-14
After I checked my Firewall using sudo iptables -L, I got these results: 

```

target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     
``` 


What does it mean?

Ok, I will try to use Bridge instead of NAT, though I did it before but couldn't connect internet....

---

### Post by yanny on 2008-01-14
Ok, now I have changed into Bridge, and I can ping to the Ubuntu!! :) Thank you soooooooooooo much!!

But what I want to know is, what are my results of the Firewall check means?

---

### Post by yanny on 2008-01-15
This problem is SOLVED!

---


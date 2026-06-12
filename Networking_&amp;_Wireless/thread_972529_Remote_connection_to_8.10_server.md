---
title: "Remote connection to 8.10 server?"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by rhcm123 on 2008-11-05
Hi! I will be going on vacation soon, and I will be bringing along my trusty laptop. However, I would also like to be able to access my home file server. (I will have broadband internet access there.)

I just need to be able to use ssh (I connect at home to my server with sshfs) to get at my server system. I don't need a gui or anything. Can anybody reccomend a good, SIMPLE!!! way to connect from anywhere in the world to my home server?
(I know my home IP, just so you know, and am not signed up with anything like DynDNS)

---

### Post by cariboo on 2008-11-05
Set a static ip address on your home server, just in case it gets rebooted, then port forward that ip address to port 21 on your router. Then if you are sure your router ip address won't change then you can sign in to your server using:

```
ssh user@external_ip_address
```

It would progbably be a good idea to install denyhosts to deny anyone from accessing  your server. 

Remember the best protection in a strong password. There was a person here on the forums that was using the user name guest with the same password, his server was broken into in no time at all.

Jim

---

### Post by rhcm123 on 2008-11-05
> **cariboo907 said:**
> 
Remember the best protection in a strong password. There was a person here on the forums that was using the user name guest with the same password, his server was broken into in no time at all.

Jim

I should probably then change my root password from root? :)
Thanks, this is really helpful. You get a thankz!

---

### Post by rhcm123 on 2008-11-05
Wait a tic!
My IP as assigned by my ISP is 173.70.42.163.
I was given the option of assigning a new public IP for my server.
I, of course, took it. No fun in connecting to a modem. I took 173.70.42.150.

I think the server encounters a problem in my massive network system.

My modem has a WAN adress of 173.70.42.163, as you saw. It has a lan address of 192.168.1.1.
It has multiple ethernet ports, but only one is used, and it connects to the router, with an IP of 192.168.2.1
This then connects to the server room router, with an IP of 192.168.2.2.
The server has an ip of 192.168.2.193.

Now, I have port forwarding enabled (as you saw) on the modem, forwarding ssh reccived on 173.70.42.150 to 192.168.2.193. The router also has port forwarding enabled, forwarding ssh (port 22 on tcp) to 192.168.2.193.

(Soory if that got confuzzling.)
But i cannot connect! I hit enter on a computer temporarily connected to our neghibors wi-fi and the cursor just moves to the next line. No error, no notification, nothing.:confused:

---

### Post by rhcm123 on 2008-11-06
Nevermind, I need to get another public IP from my ISP to run this well... I doubt my parents will pay for that.. humph.

---


---
title: "Remote SSH connection to home LAN."
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by extruct on 2008-09-19
Hi all.
I got a home lan of 2 pc's. My sis pc running winxp and my pc running Ubuntu. They both connected with a wire to a router that is connected to a modem. I want to have access to my PC from college via SSH. What software should I install on my pc and on college's pc and how to connect?
Thanks.

---

### Post by Friek on 2008-09-19
You need to have the openssh server installed, which is default afaik. You can check easily by running 'telnet localhost 22' in a terminal. If it doesn't say 'Connection refused', the ssh server is running properly ;)
Otherwise, run 'sudo aptitude install ssh' to install it.

Additionally, if you want to access it remotely and you're behind NAT, you need to create a port forward to the LAN IP of your box on port 22. How to create port forwards depends on your router..

---

### Post by chris_nava on 2008-09-19
If you are going to set up port forwarding (required if you want to SSH in) you should also consider setting up static IPs.

This will prevent any other PC on the LAN from getting the port forward if the are rebooted and another one happens to get the IP you previously had.

Many routers allow you to associate a permanent DHCP IP with the MAC address of your NIC card (so the PC configs don't need to change.)

Also... You may want to set up Dynamic DNS so you don't have to know the IP that your ISP gave your router.

---

### Post by extruct on 2008-09-20
Friek
It said "Connection refused" so I installed SSH now it says some other things :p
About port forwarding Ill be able to handle it I did it before.

chris_nava
My IP is already static. Can you tell more about Dynamic DNS? Or refer me to some tutorial about it?

One more question, as I understand now I'm running ssh server, How do I protect it so my PC wont be hacked or something like this? Sorry if its dumb question, never did it before.

Thanks again!

---

### Post by Friek on 2008-09-20
If the IP you log in from is static too, you can add it to /etc/hosts.allow:
sshd: ALL EXCEPT <ip> : deny

That way, no other IPs are allowed access..

---

### Post by issih on 2008-09-20
You should consider doing a few other things for security:

1) Change the port ssh works on
2) Make absolutely sure that all users have STRONG passwords
3) install deny hosts to stop people continually trying to connect..
     [http://www.ubuntugeek.com/securing-ssh.html](http://www.ubuntugeek.com/securing-ssh.html)

Otherwise you run the risk of being hacked quite quickly.

Dynamic dns services are literally websites that provide you with a domain name that they dynamically map onto your isp assigned dynamic ip address. They achieve this by having a small program installed on either your pc (or in some cases integrated into your router's firmware) that logs into the website and informs them of the new isp assigned address.

noip and dyndns both do this for free for home users, I suspect there are other, those are just the ones I'm aware of

---


---
title: "Networking through VPN"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by timo2 on 2014-03-08
Hey all,

I'd like to reach my computers at home from work but my ISP does not
provide static IP addresses so I bought yesterday a server in France where
I installed a PPTP server which provides every client with a static IP address.

This was not even a small problem but now I have a problem with port forwarding and 
I hope one of you guys can help me:

I can reach my mobile phone from home through the VPN netwerk but I can't reach my
computer by pinging from my mobile.

That means any firewall is blocking this connection.

My network looks like this:
EASYBOY -> TP-Link TL-WR1043ND -> Computers

Where do I have to forward the 1723 port? 
Actually I only forwarded it in the EasyBox. 

Is this correct or do you have any idea why it's not working correctly?

Thanks for your help

---

### Post by gordintoronto on 2014-03-08
The router is where you do port forwarding. In the manual for your router, it's described under "UPnP". As it says in the manual, you need the computer to have a static IP address, so, for example, you might forward port 1723 to IP address 192.168.168.58. At my office there are numerous computers, each with a specific IP address and terminal server port number, so I can access each of them using Remote Desktop. (KRDC)

If you use a firewall, you will also need to open the port.

---


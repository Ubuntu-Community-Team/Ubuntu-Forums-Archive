---
title: "How to setup up a pptp bridge"
date: 2016-06-19
forum: Networking &amp; Wireless
---

### Post by daniel294 on 2016-06-19
Hi all,

I used to connect my home server via pptp to access it from outside the home LAN. But, now my ISP blocked that option and I cannot access my home LAN from outside, any more.
To overcome that, I set up an pptp server on Ubuntu server on Amazon.
The idea was, to connect my home server to the Amazon (via pptp) then, connect my client to Amazon (also via pptp) then create a bridge between ppp0 and ppp1 on the Amazon server.

My home LAN has the IP of 192.168.0.x the Amazon server has a IP of 172.131.1.x
Currently, I can connect my home server to Amazon. After that, I have a ppp0 interface on my home server with the ip of 172.31.1.2
I can also connect my client (from outside my LAN) to the Amazon server and I have a ppp0 with the ip of 172.31.1.3
On the Amazon server I have two interfaces ppp0 and ppp1. 
The problem is that I can't access from my client (outside of the LAN) to my server (in my home LAN)

I need help connecting from outside of my LAN to the home server

Thanks a lot,
Daniel.

---

### Post by SeijiSensei on 2016-06-19
First, you'd be better off using OpenVPN as [PPTP]("http://openvpn.net/") has many insecurities.

I'd build a [static OpenVPN tunnel]("http://openvpn.net/static.html") between your home machine and the Amazon host.  Then you can build an equivalent tunnel between your mobile device and the Amazon host.  If you enable packet forwarding on the Amazon host (see /etc/sysctl.conf for details) that machine will route traffic between your mobile device and the home machine.  You don't need any sort of bridging.

If you already have successfully built PPTP tunnels among all three machines, the missing ingredient may be enabling packet forwarding in /etc/sysctl.conf.

---


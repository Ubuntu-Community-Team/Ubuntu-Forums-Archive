---
title: "some VPN questions"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by night_fox on 2008-11-13
Dear all,

I have some questions about VPN. Here is my situation:

Here I am, in my house, posting away from my amazing network, of which I am incredibly proud. I configured all of the wireless routers myself, I have 3 of them. Router 1 acts as my DHCP server, and connects to the modem. Routers 2 and 3 connect to router 1. All computers connect wirelessly to either router. My friends and I can all use our various VPN clients very easily to connect to our Uni's network.

1st question: I am using Network Manager's built-in vpn client to connect to the Uni VPN. It takes a few tries to connect, and then connects for a while, gives me enough access to SSH into a computer to use MATLAB for a bit, and then spontaneously hangs up. Is this a bug in network-manager-vpnc or should I email the VPN providers?

2nd question: I would like to be able to SSH into my own laptop from anywhere around the world. Router 1's web based configuration makes absolutely no mention of VPN, but router 2 has several configuration pages about it. Can I use router 2 as a vpn server even though its not directly connected? Does this mean I would need to forward some ports on router 1 to router 2?

3rd question: Supposing that I forwarded all the ports used for VPN on router 1 to router 2, does this mean that every computer inside the house network would be unable to connect to a remote network via VPN?

4th question: Supposing that I used my laptop to connect to a remote network using VPN, say my uni one, I noted down my IP address, and that I logged on to a computer at uni. Would I be able to use SSH to my laptop's IP address within the uni network, to communicate with my laptop?

Thanks in advance,

John

---


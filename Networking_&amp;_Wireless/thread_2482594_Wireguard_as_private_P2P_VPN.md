---
title: "Wireguard as private P2P VPN"
date: 2023-01-05
forum: Networking &amp; Wireless
---

### Post by vmalep on 2023-01-05
Dear all,

I wish you a very happy new year! Mine has not started quite well so far...

I have just spent more than a full day trying to configure a private P2P VPN using wireguard. I first tried with a RPI from home, then on a DigitalOcean cloud server, with pivpn, wireguard directly, using configuration scripts or not, and I am getting crazy.

The best I could achieve is the P2P VPN working, but with no more access to internet. The clients are supposed to go through the VPN if connecting to another peer and through the ISP for any other connection (internet), but it does not work. And I cannot find any HowTo explaining how to do exactly that.

I am not sharing any config file here (i.e. wg0.conf) because I have tried so many different config (plus the iptable masquerating stuff) that I could not summarize it to something making sense. I just feel soooo frustrated that we do not have yet an easy solution with Linux for that (what I concretely need is the ability to connect seamlessly to other Ubuntu devices among our family).

At this stage, I will revert back to Tinc VPN that I used to configure in the past, but I see it as a drawback since with Tinc, it is a bit more complicated to had new clients. If one of you knows about the magic solution or the perfect howto, please let me know.

Cheers,
Pierre

---

### Post by The Cog on 2023-01-05
Are you asking or help debugging, or announcing that you don't want help?

I have been using wireguard to connect P2P to a Digitral Ocean droplet for a couple of years. I did it because my ISP (Virgin Meda) doesn't appear to have any engineers that can even spell IPv6, let alone implement it. I can pass both IPv4 and IPv6 through the droplet. On the droplet, I use NAT for IPv4 but I pass IPv6 straight through to the PC. I'd be happy to help you debug if you want.

However, my first suggestion woudl be to install a newer version than 9.10, upgrading to version that has wireguard built into the kernel. On both your PC and your droplet.

---


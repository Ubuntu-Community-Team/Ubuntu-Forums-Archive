---
title: "Port Forwarding using iptables"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by lgbpinho on 2009-03-19
Hi there.

I'm trying to run amule and torrent clients, but i'm getting really slow speed and low-id. I checked my router and it is redirecting some ports (tcp 4662, udp 4762 for amule) to my machine. SO the problem is probably some firewall. I onlly have iptables running. then:
1) whats the command for openning the ports using iptables?
2) how can i redirect what comes from ports 4662(tcp) and 4672(udp) to 10.0.0.2?

---

### Post by paultag on 2009-03-19
> **lgbpinho said:**
> Hi there.

I'm trying to run amule and torrent clients, but i'm getting really slow speed and low-id. I checked my router and it is redirecting some ports (tcp 4662, udp 4762 for amule) to my machine. SO the problem is probably some firewall. I onlly have iptables running. then:
1) whats the command for openning the ports using iptables?
2) how can i redirect what comes from ports 4662(tcp) and 4672(udp) to 10.0.0.2?

You shant.

The local ports are opened by the application its self.

So, I must ask. Why forward ports? Unless you are running a server, and you _really_ want to expose an unprotected and unsecured non-production box to the dirty dirty internet you can continue with this.

I, howerver, would look insted to doing this without redirecting Internet traffic to the local box. P2P clients don't need to have traffic forwarded to the machine from the router.

And, to answer the question: IPTables is used to filter OUT the riff raff.

[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)

Cheers,
Tag

---

### Post by mkvnmtr on 2009-03-19
I would not recommend messing with Itables. I torrent a lot and they are not the problem. They open a port when they need to. 
I have a static IP that I got through my router. I use Deluge but noticed the same results on Transmission and Ktorrent. I use random ports option and choose to have 50 half open connections. I set my total torrent bandwidth a little lower than what is allowed by my ISP so I can still use the internet. I get the max download speed my ISP allows on a well seeded torrent almost always. It seems that some days it is a little slow but that is just the internet,
To check your if you are getting bad speeds try the 8.10 Ubuntu torrent. It is well seeded and you can leave it on and help the Ubuntu community.

---


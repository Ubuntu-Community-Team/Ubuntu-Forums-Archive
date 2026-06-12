---
title: "Stuck behind a firewall (Setting up VPN)"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by IQAndreas on 2008-08-28
Hello all.

I would like to set up a VPN server on one of my computers (linux or windows, does not matter), but I have a problem.

My ISP has all their clients (including me) behind their own firewall. Then, they lend out private IP addresses (in my case, 10.0.52.12) to all their clients. I also have a private firewall, but I can easily edit that or forward any ports as necessary. I would like to allow other people to access my server, but since I do not have a public IP address, would this still be possible?

Google searching just lead me to a bunch of really technical mumbo jumbo sites, and I'm not quite sure which of those sites applied to my situation.

I am familiar with basic networking (such as private and public IPs etc).

---

### Post by stoneybroke on 2008-08-29
I think what your ISP does is lease IP addresses with DHCP so once a client computer closes the connection the IP address becomes available to another computer these IP addresses are dynamic so they will change every time a computer connects/disconnects you will have to give your server a static IP address and use Port Forwarding to point to that address if you know what I mean.

If not ask again.

---

### Post by tangibleorange on 2008-08-29
hmm should be possible. find out your public IP at:

[http://www.whatismyip.com]("http://www.whatismyip.com")

and then make your VPN server listen on some obscure, high-number port (like 58841) that nothing else uses (hopefully no-one else behind your ISP firewall is using it, as I assume all clients are using the same IP). then forward the port on your router. check if it is open through the internet at this site:

[https://www.grc.com/x/ne.dll?rh1dkyd2]("https://www.grc.com/x/ne.dll?rh1dkyd2")

and probe the port you chose. if it lists as stealth but you've opened and forwarded the port, your ISP is blocking it...

---


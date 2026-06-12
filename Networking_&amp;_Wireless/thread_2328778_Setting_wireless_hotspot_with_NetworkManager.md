---
title: "Setting wireless hotspot with NetworkManager"
date: 2016-06-24
forum: Networking &amp; Wireless
---

### Post by KNRO on 2016-06-24
I want to use NetworkManager to set a hotspot using my wireless adapter on my main machine (myubuntu). So I used NM to create a new wireless connection and set it in Access Point (AP) mode, then in the IPv4 setting, it is set to "Shared to Other Computers". Now this works. I can connect from my phone and other computers wirelessly to the SSID and get an IP address..etc.

The problem is that I cannot resolve the hostname of the my machine on the client side. That is, if I try to **ping myubuntu**, it fails. Also **nslookup myubuntu** fails. I know NetworkManager uses dnsmasq, so I added a file hosts.conf with one line:

```

addn-hosts=/etc/hosts

```

to /etc/NetworkManager/dnsmasq.d and /etc/NetworkManager/dnsmasq-shared.d

I thought if you're connected to the hotspot, all DNS requests goes to it, and it should be able to recognize the hostname (myubuntu) and return its IP address to the client machine and ping would work, but it seems I am missing something here. Any clues?

---


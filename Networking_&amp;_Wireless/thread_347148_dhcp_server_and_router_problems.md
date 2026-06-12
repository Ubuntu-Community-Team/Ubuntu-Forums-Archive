---
title: "dhcp server and router problems"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by motherofberyl on 2007-01-26
hi
i'm attempting to set up a server that i can boot from on my home network. i've successfully got the dhcp server to run, however, when i run it on the same network as my router, i lose my internet connection. i've disabled the dhcp server in the router, but the router fails to get an IP address for the WAN port whenever my linux dhcp server is running.. i'm a little stumped. any thoughts?

i'm using dapper server and the router is a netgear rp614. i can still log in to the router when the internet connection fails, and all the machines receive the right ip address.

---

### Post by kidders on 2007-01-28
Hi there,

It sounds like your router might be being assigned an address by your DHCP server. It's conceivable that this might be confusing it. :confused: Assuming your router works properly with *all* the DHCP servers switched off (ie yours and it's own), the next thing to try kinda depends on the structure of your LAN. Could you take a look at my attachment and see which model is closest to yours? (Basically, I'm interested in where your DHCP server is.)

By the way, your DHCP server logs will tell you if I'm on the right track ... you should be able to watch IPs being assigned to the various things on your network.

---

### Post by motherofberyl on 2007-01-28
hey kidders
i'm using model b in your beautiful diagram, just playing with a box on the network. if i get a chance later (when no one else needs internet access) i'll try and run the shcp server and see what the logs tell me is connected. let me know what logs will be useful.

thanks for your help 

rob

---

### Post by kidders on 2007-01-30
Any joy?

Also, since your DHCP server and internet gateway aren't the same computer, you should check to make sure the default route being sent to your DHCP clients is sensible. A bad default route could prevent DHCP clients from accessing the internet ... but we can worry about that more, after we figure out what's causing your internet connection to go down.

---


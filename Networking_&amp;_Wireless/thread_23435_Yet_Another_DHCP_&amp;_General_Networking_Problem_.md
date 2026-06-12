---
title: "Yet Another DHCP &amp; General Networking Problem with 5.04"
date: 2005-04-01
forum: Networking &amp; Wireless
---

### Post by Papaskunk on 2005-04-01
First off, I'm not asking for any help here, as I'm not sticking with 5.04 for multiple reasons (already rolled back to 4.10). I just want the community/developers to be aware of this.

Booting to the Hoary install CD, my NIC is detected, a DHCP request seems to be made, but... nothing is ever received. Says it can't find a DHCP server. Even after the installation is complete, no amount of tinkering, editing .conf files, etc. can get it to accept the DHCP supplied by my server. I don't know if it's requesting DHCP in IPv6 or what, but it just doesn't work. As I said though, it does detect and load the correct module for the card!

Later, after I decided to go back to 4.10, I put in the install CD and, low and behold... it works. Meantime, I booted up into Gentoo, Knoppix a couple of times, networking worked fabulously. They both loaded the exact same module for my NIC (typical 10/100 PCI card, should work out of the box). My gateway even detected a connection and logged a ton of packets (25,000 or so in just a few minutes) coming from the machine while it had 5.04 on it. At the same time, *I was not even able to ping the gateway*, which is the same machine running the DHCP server, through a direct crossover connection, though I was able to under Knoppix, Gentoo, and Ubuntu 4.10 on the same machine using the same connection (pinging with manual IP settings of course, since no IP was ever supplied/accepted/whatever). This is the part that really bothers me, because with a working NIC and eth0 activated that is *sending thousands of packets to my gateway,* why can't I ping it?

My guess is, somehow IPv6 is getting in the way. I admit, I'm relatively new to Linux and Ubuntu, but after reading all the other threads in this forum and seeing nothing work, just thought I'd throw this out there. And, aside from understanding conceptually how IPv6 works, I have no real working knowledge of how to handle it in practicality.

As I mentioned, I'm not requesting help since I already rolled back to 4.10 for other reasons, but  it is kind of bothering me as to what was actually going on, so if anyone has any ideas...

---


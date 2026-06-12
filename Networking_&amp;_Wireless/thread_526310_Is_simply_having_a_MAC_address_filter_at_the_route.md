---
title: "Is simply having a MAC address filter at the router good enough security?"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by tak1150 on 2007-08-15
Sorry if this has been discussed before. I couldn't find a thread for this exact topic.

I have a D-Link DI-634M wireless router. When you go to the web based administration interface, there is an option to filter computers based on MAC addresses.

Would having this MAC filter as the only means of security be enough (conservatively assuming every neighbor of mine is a gifted hacker)? I am having hard time WPA working. Thanks!

---

### Post by Steveway on 2007-08-15
No, others could easily change their MAC-adress to yours.

---

### Post by tak1150 on 2007-08-15
Thanks for replying!

What about restriction by IP addresses?
-Local ones like 192.168.0.100?

---

### Post by Austin_KW on 2007-08-15
> **tak1150 said:**
> Thanks for replying!

What about restriction by IP addresses?
-Local ones like 192.168.0.100?

MAC address, IP addresses are just numbers used by different layers of networking to address packets by sender and destination. Anyone can setup their system to use any number and thus pretend to be you or more simply just sniff the air to see what you are doing.

You need to use WPA-PSK with a 20+ random character PSK to secure a wireless network.

---


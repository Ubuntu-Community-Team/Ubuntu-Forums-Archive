---
title: "Swapping servers"
date: 2015-05-22
forum: Networking &amp; Wireless
---

### Post by chriso0258 on 2015-05-22
Hello,

I'm running Ubuntu Linux 12.04.3 and Apache version 2.4.12. This is my test server which is mirrored after my production server. I've made some updates, changes, etc. on this server and have imported my data from the production server. My question is this. For ease of transition, I would like to down the production server and bring this test server up as the production server. The only difference between them is the DNS host name (IP is DHCP). If swapping these servers is feasible, what file(s) do I need to modify to make the switch? Is this a good idea or is there a better method? If all goes according to plan, the test server will become the production server and the production server will become my test server. 

What are you thoughts? I've not done this before.

Thanks for your assistance/advice.

Chess Dad.

---

### Post by corti-nico on 2015-05-22
> **chriso0258 said:**
> If swapping these servers is feasible, what file(s) do I need to modify to make the switch?

Unfortunately your question is not easy to answer, it depends on which services are available on your servers. Just apache or even others (mailservers, etc...)
It depends even on your local DNS configuration, have you got a local DNS server or your are using an online service for DNS?

Theoretically speaking, you should change your DNS record of your production server hostname, to point to your test server.
Please take in account that if you use vhost in apache, you should configure it to accept http request from your production server hostname.

---


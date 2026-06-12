---
title: "How do i get connected on ubuntu 6.10 with PPPoE"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by tahsin on 2007-02-15
Hi on windows i just set up a PPPoE dialer with a user name and password and i was given a MAC or network address i used to put this address on the ethernet card properties>network>address>value on windows and i use to log in with the pppoe dialer to get connected on windows? so how do i set up these things and get connected on ubuntu. I have tried lots of things but no use:confused: .Can any1 give me a clean solution please.I really need help please help me :(

---

### Post by justin whitaker on 2007-02-15
> **tahsin said:**
> Hi on windows i just set up a PPPoE dialer with a user name and password and i was given a MAC or network address i used to put this address on the ethernet card properties>network>address>value on windows and i use to log in with the pppoe dialer to get connected on windows? so how do i set up these things and get connected on ubuntu. I have tried lots of things but no use:confused: .Can any1 give me a clean solution please.I really need help please help me :(

Tahsin,

It's easy. 

First, open up a terminal. You need root access, so if you haven't sudo passwd, do it now. Log in as root, and type pppoeconf.

Follow the prompts. 

Thanks,
Justin

---

### Post by tahsin on 2007-02-15
Thanks justin but i did that and i still cannot connect when i type plog on the terminal i get invalid user name and athentication failed but dont i need to put in the network address that my isp has given me?where do i input that?any clues?

---


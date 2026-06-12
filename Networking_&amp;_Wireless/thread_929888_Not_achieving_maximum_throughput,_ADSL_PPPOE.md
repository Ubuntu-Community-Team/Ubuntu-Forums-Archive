---
title: "Not achieving maximum throughput, ADSL PPPOE"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Blackhand on 2008-09-25
I recently installed Ubuntu Hardy 8.04.

I used pppoeconf from the console to set up ADSL internet access on the machine. It seemed to work great right out of the box, however, I've realized that in Ubuntu I'm only getting a maximum download rate of 30.5kbs, while in Windows I get 50kbs (512k line).

Ive used tests on my ISPs home page to test this.

Does anyone have any suggestions?

---

### Post by caljohnsmith on 2008-09-25
I've seen other threads of people having speed issues when setting up PPPoE in Ubuntu. The easiest solution for most is to just go into your ADSL modem settings and change it to "PPPoE is on modem" instead of "PPPoE is on computer", or whatever is the equivalent for your particular modem. That way you set up the username/password in the modem, and then use Ubuntu to connect to your modem with standard DHCP. Could this be an option for you?

---

### Post by Blackhand on 2008-09-25
I am aware of this solution which effectively lets the ADSL router act as a gateway.

Unfortunately it is not an option for me in my current network setup.

Thank you though for your help and the quick response.

---


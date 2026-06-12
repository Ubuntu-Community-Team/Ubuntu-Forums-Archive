---
title: "How do I share a dial-up with firestarter"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by iwannauseubuntu on 2005-09-05
Help Please

I need help with the following:

I have a PI233 which I am busy trial setting up as a dhcp server/ internet sharing for my network, currently 4 clients.

I have installed ubuntu and run the apt-get update. I have downloaded firestarter and installed it along with dhcp3-server. 

The dhcp works fine and gives out ips to all the clients. Firestarter will not let any client get internet access, in fact it denies firefox on the ubuntu machine as well. Whenever I enable the firestarter control of dhcp, firestarter fails to start.

iptables as far as I know is setup. I used the masquarade instructions in the how-to manual in usr/shared/docs.

Where do I look for the problem?

Internet is dial-up, getting about 33.6k connection speed. The modem is a 56k. 
Another question, where do I set the modem not to wait for a dial tone?

---

### Post by kagashe on 2005-09-05
Hi,

Click on Preferences in Firestarter
Your Network settings in Firestarter should look like this:
Internet connected network device:
Detected device(s): Dialup device (ppp0)

Local Network connected device:
Detected device(s): Ethernet device (eth0)
Check Enable Internet connection sharing
Check Enable DHCP for local network

If not set up as above run the wizard and set it up.

kagashe

---

### Post by iwannauseubuntu on 2005-09-05
thanks kagashe

my shipit cd's arrived today so I am reinstalling

I will ask further once the installation has happened, with a PI that can be some time.

---


---
title: "PPTP and DHCP"
date: 2005-06-02
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2005-06-02
Hello all!
I've got a problem here:
I'm a linux newbie and I have decided to set up Ubuntu on my server. I've got a VPN connection to my provider with and the provider's server IP is assigned dynamically via DHCP. I'm not very familiar with the routes and all so far so I can't competely understand the line ```
route add host <IP address of VPN server> <gateway>
``` What is gateway here? Is it my 192.168.0.1 or the Internet server's address that is assigned dynamically by a DHCP server? And if it's assigned dynamically, how can I write a static address being not sure that it will not change next time?

Let's say I have two interfaces, eth0 which is for my local network and eth1 which connects to the provider's DHCP server. I have configured them both okay (i can ping my provider's server so DHCP server assigns an address) but I'd like to know what do I need to do to make a VPN connection.

And yet, where do I write details such as username and password? I have discovered that it seems that different realizations of pptp-linux use different files, for instance there's a file /etc/ppp/options in Ubuntu and many manuals refer on the /etc/ppp/options.pptp.

Yet the situation is not quite clear for me with the /etc/ppp/ppp.conf file. Should I put my login and password detals there or should I put them in the etc/ppp/chap-secrets ?

And what is about /etc/ppp/peers directory? Should I create a settings file in it as well?

Please clear the situation for me!
Thanks in advance!

---

### Post by xristos on 2005-06-03
You can start from here ---> [http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/)
Read the section about debian . It's the same for Ubuntu .

---

### Post by PryGuy on 2005-06-03
Thank you very much, Greece! :)

---

### Post by xristos on 2005-06-03
[QUOTE=PryGuy]Thank you very much, Greece! :)[/QUOTE]
 Anytime Russia !

---

### Post by codemills on 2005-06-03
[QUOTE=xristos]Anytime Russia ![/QUOTE]
 lol.

india thanx russia and greece 

:P

---

### Post by PryGuy on 2005-06-07
Russia thanks India, Greece, Britain, Spain, Italy, China!!! :grin: 
And well, all the rest... :wink:

*hope the moderators won't punish us for such a great sign of the planetary friendship* lol

---


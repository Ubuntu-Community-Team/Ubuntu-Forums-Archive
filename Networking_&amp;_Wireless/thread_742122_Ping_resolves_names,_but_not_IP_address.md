---
title: "Ping resolves names, but not IP address?"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by roninbk on 2008-04-01
Fairly n00bish here, be gentle...

I've had intermittent problems recently with my internet connection, periodically disconnecting and reacquiring an IP address from the ISP's DHCP. (or that's how it appears on the Network and System Monitors I added to my top Panel)

Thing is, when following the instructions at [https://help.ubuntu.com/7.10/internet/C/network-troubleshooting.html](https://help.ubuntu.com/7.10/internet/C/network-troubleshooting.html) where it suggests attempting to ping 82.211.81.158 and ubuntu.com, I get 0% returned on the IP address, but 100% on the domain name.

From what I understand of DNS, if the DNS lookup was going to fail, it would have resolved the IP address, and not the domain name. As it stands, I'm thoroughly confused.

It's completely reproducable too, I've retried it a number of times. Halp?

---

### Post by puneit on 2008-04-01
Ok.. The IP you have mentioned is not replying for me too.. This is the way I test my network by pining. Here is brief about my network. I am connected to a Netgear Wireless LAN which is supplied by ADSL modem. IP of Netgear is 10.0.0.1 and of ADSL is 192.168.1.1
Therefore my first test is by pinging 10.0.0.1
On getting a response I ping 192.168.1.1
Then I ping a global name server at 4.2.2.2 or 4.2.2.1 or  208.67.222.222 or  208.67.220.220 
You must get a response from one of these. 
Try this!

---

### Post by roninbk on 2008-04-01
> **puneit said:**
> Ok.. The IP you have mentioned is not replying for me too.. This is the way I test my network by pining. Here is brief about my network. I am connected to a Netgear Wireless LAN which is supplied by ADSL modem. IP of Netgear is 10.0.0.1 and of ADSL is 192.168.1.1
Therefore my first test is by pinging 10.0.0.1
On getting a response I ping 192.168.1.1
Then I ping a global name server at 4.2.2.2 or 4.2.2.1 or  208.67.222.222 or  208.67.220.220 
You must get a response from one of these. 
Try this!

Skipping 10.0.0.1 and 192.168.1.1, as I am not behind a router at the moment, (removed at an earlier troubleshooting attempt.)

Oh, this is interesting. I pinged as before, and it failed on all four global IP addresses you brought up. HOWEVER, when pinging from a *command prompt*, all but the original 82.211.81.158 resolve at 100%!

This leads me to the following suppositions:
1) The problem with resolving IP addresses is occuring with the Network Tools frontend, not ping in general, or my connection.
2) The 82.211.81.158 address may be a documentation bug,

---

### Post by roninbk on 2008-04-02
Bumping for solution on why Network Tools ping would not resolve, but command line will...

---


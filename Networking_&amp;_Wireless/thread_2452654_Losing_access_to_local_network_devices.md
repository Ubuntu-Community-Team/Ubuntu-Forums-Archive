---
title: "Losing access to local network devices"
date: 2020-10-26
forum: Networking &amp; Wireless
---

### Post by beanfest on 2020-10-26
I will prefice this with i am a novice linux user. I may incorrectly use technical terms. I am running 18.05LTS as I am still too afraid to upgrade

The issue is that a couple times a day my PC is unable to resovle ip addresses for devices on my local network. I always have access to the interenet though. I lose the ability to find by name, local devices. I am able to correct the issue by going to the network settings, turning off the ethernet connection and then turning it back on. The IPV4 address is set to DHCP and the DNS is set to automatic. I have tried manually setting the DNS but the issue remains the same. The domain name server runs on a windows 2008 server. I am the only linux user in the company so IT is unable to provide support.

Here is an example of the nslookup that I ran when I was unable to communicate with a local network device[INDENT]nmxuser@303MFG-AS:~$ nslookup hwlab-pc3
Server:        127.0.0.53
Address:    127.0.0.53#53


** server can't find hwlab-pc3.nanometrics.ca: NXDOMAIN[/INDENT]


Here is an example of after I reset the network connection.[INDENT]nmxuser@303MFG-AS:~$ nslookup hwlab-pc3
Server:        127.0.0.53
Address:    127.0.0.53#53


Non-authoritative answer:
Name:    hwlab-pc3.nanometrics.ca
Address: 10.11.2.9


[/INDENT]

---

### Post by beanfest on 2020-10-26
What is different between accessing a local PC and accessing the external internet?
Why would my PC stop being able to access the DNS? Is there a timeout function? Is there no caching of addresses?

---


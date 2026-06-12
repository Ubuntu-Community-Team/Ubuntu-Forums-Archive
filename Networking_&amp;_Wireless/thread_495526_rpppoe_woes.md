---
title: "rpppoe woes"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by slugg0 on 2007-07-08
hi all. i am an avid Linux user and have been for some years. i have used many distro's from slackware 7 through building a stage 1 gentoo box. i would say i am pretty savvy most of the time at figuring things out but I cannot get this one. After getting sent to iraq, i have subscribed to the only available internet provider where i am at. this is where the problem starts. i have an ethernet cord running from a router somewhere to my computer. the internet provider told me that i need to create a "internet connection pppoe" on my desktop. he gave me a set of instructions which are for windows. i told him i dont use windows and he said he cant help me with linux that i would have to figure it out on my own. so here is the problem. pppoe works on edgy eft, and i have done the whole setup thing a million times now providing the username and pass eth(x) etc and i have had absolutely no luck. i have been stumped by this and have googled and tried many different how-tos, read the docs, etc but nothing has worked. as soon as i get back to my computer, i will try to get some output for you all, maybe you can point me in the right direction. it seems the server disconnects me when sending the password. give me a bit and i will post the output for you. i appreciate any help at all at this point.

---

### Post by slugg0 on 2007-07-08
Ok, heres the output of the commands plog and pppoe-discovery.

$ sudo pppoe-discovery
  Access-Concentrator: TB-New
  Service-Name: service1
  AC-Ethernet-Address: 00:0c:42:03:19:ae

$ plog

pppd [6852]: LCP terminated by peer (Encryption negotiation rejected)
pppd [6852]: modem hangup

I also changed the username to one that is bad to check output and it gave me:
CHAP authentication failed
primary DNS address: 123.123.123.123
secondary DNS address: 321.321.321.321
Connect time 0.0 minutes
Sent 12 bytes received received 4 bytes
restoring old default route to eth0
connection terminated
bad username and or password
modem hangup

i am not sure why its rejecting the encryption negotiation. 
The settings under windows calls for:
Service name:  (blank)
Options: display progress while connecting
               prompt for name and password
               redial if line is dropped
security: typical
networking: Type of broadband connection PPPoE (enabled LCP extensions and software compression)
                    TCP/IP
                    QoS 
im really frustrated at this point as i am paying for internet i cant use and i have to use a friends laptop to check my email now. the only thing i can come up with is the LCP thing but i have no idea how to fix it. i have checked my /etc/ppp/peers/dsl-provider config and everything seems ok. suggestions welcome. thanks!


------ Update------
Ok after looking at the windows settings on my friends laptop I made a discovery. Windows LCP in typical mode has no encryption. So is this possible to do with Linux and pppoe? i really dont like the thought of using a service provider that has no encryption, but it is my only solution at this point. At least that is explaining the error message of why LCP is getting an encryption negotiation rejected...... Any thoughts?

---

### Post by nkn.crazy on 2008-07-24
i need some help abt configuring my net connection in ubuntu hardy
i have tata indicom BB connection....
i tried installing rp pppoe dailer in linux...and i could do that properly with out any errors
when i try to start the connection with the command "pppoe-start"
it says connected !
but even then i m not able to use the net
1. did any one face this problem?what could be the problem?
2.can u suggest any other pppoe dailers for linux


i tried googling this issue but i didnt find any answer...so i m posting this.
i m sorry if i am posting a repeated issue

---


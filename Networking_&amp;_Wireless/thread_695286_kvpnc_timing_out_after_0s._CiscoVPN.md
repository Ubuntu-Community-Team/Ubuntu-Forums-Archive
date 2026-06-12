---
title: "kvpnc timing out after 0s. Cisco/VPN"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by jord1242 on 2008-02-12
Hey all, not sure if anyone has run into this, but I am trying to setup a VPN connection using Cisco, and I get the following error:

```
Timeout while connecting to ***.***.***.*** (Work) after 0s. 
Please check if the VPN server is reachable and the settings 
(UDP/TCP, local port, UDP encapsulation port) are correct. 
Maybe the timeout must be increased too.

```I am able to ping the server at ***.***.***.***. I am fairly sure all information was entered correctly as my network admin gave me a sheet with all the relevant data on it.

I tried to up the peer timeout in the Cisco connection specific settings to more than 0, but it still gives me the same issue.

Anyone have any thoughts as to what to try? Thanks for anything you can come up with.

peace,
JJ

---

### Post by jord1242 on 2008-02-13
Anyone have any ideas? I have tried resetting the peer timeout and restarting but nothing.

JJ

---

### Post by carverj on 2008-02-13
so you are trying to connect to the server with Cisco VPN client?
Do you know if the server is up at the moment?

---

### Post by jord1242 on 2008-02-13
Yeah I can ping the server just fine from the same machine. Not sure why it is timing out so fast though. It seems like if it was giong to time out it would take some time to come back and tell me it timed out, right?

---

### Post by carverj on 2008-02-14
Have you established connection previously with that client? 
It's just that the configuration of the server may be the problem!?

---

### Post by jord1242 on 2008-02-14
Other people I work with use the client to get in just fine. I have not been able to determine what is different about how they have there setup, but they are working. I set it up what I thought was the same way and get that weird timeout.

---

### Post by carverj on 2008-02-14
Right, so there is no hang from password problems, other workstations can connect from same network, server is configured to allow VPN tunnel from this machine.....
Options/thoughts....
Can you debug kvpnc to find more info? (haven't used client personally and just going by some of the posts I found by googling:-  kvpnc timeout Cisco/VPN)
Actually, see:-
[http://home.gna.org/kvpnc/en/faq.html#003](http://home.gna.org/kvpnc/en/faq.html#003)
Possible solution as these guys have problems so use command line instead:-
 [http://www.nabble.com/VPN-Question-td14997473.html](http://www.nabble.com/VPN-Question-td14997473.html)

What was the timeout value? 0? What is it now? So you have tried doubling it!!?

See: - 
[http://home.gna.org/kvpnc/en/faq.html#013](http://home.gna.org/kvpnc/en/faq.html#013)
for what the kvpnc ppl are saying
Otherwise, did your company give you any way to contact the Cisco experts or the guys who setup the server?

---

### Post by jord1242 on 2008-02-16
Thanks for the help. I finally got it figured out. For anyone interested, 

Sometimes when you make changes in kvpnc, if you don't close it after clicking apply and restarting your machine, it doesn't take affect. This is what was happening in my case. I was changing the peer timeout value to 10 from 0, and because I wasn't restarting, it wasn't taking affect. Once I changed it to 10, then restarted, it worked.

Thanks so much for all your help! It is very much appreciated.

JJ

---


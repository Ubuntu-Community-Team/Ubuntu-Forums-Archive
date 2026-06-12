---
title: "Port Trunking for 2x bandwidth"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by Mickeysofine1972 on 2007-08-28
Hey guys

I was wanting to use a Ubuntu box to load balance the traffic from two adsl routers and pass the traffic back and forth to another box that is behind the Ubuntu box. heres a bit of ascii to explain:
```

                                      ASDL1                               ADSL2
                                           |                                 |
                                            -------------------------------
                                                                  |
                                           UBUNTU LOAD BALANCER
                                                                  |
                                                                  |
                                                 NETWORK(ED) PC(s)

```
I want the networked pc to be able to send and receive through either of the two ADSL routers and If I add more pc's later I would like them all to get a load balanced access to the internet.

I've looked at network bonding but I cant help thinking I should be running some kind of packet forwarding from the bonded interface.

What do you think is the best way to do this?

Kind Regards

Mike

---


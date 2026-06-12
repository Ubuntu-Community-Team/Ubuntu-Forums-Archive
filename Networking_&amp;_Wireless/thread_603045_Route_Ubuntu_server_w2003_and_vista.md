---
title: "Route Ubuntu server w2003 and vista"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by LMSSML on 2007-11-04
Hi people,

I would like to know if it's possible having this scenario.

             Router
                 |
    Ubuntu Server
        |                    |
   W2003             Vista

As the try schematics above I would like to have the following situation:

The internet traffic comes to therouter goes directly to firewall(iptables) filtering traffic and then goes to the other twoo machines.

In resume I want to know if it's possible having a router but all incoming and outgoing traffic be controlled by ubuntu server.

If it's possible I would like to know the possible ways to do that and documentation if it's possible.

Best Regards

---

### Post by puccaso on 2007-11-04
mmm
u need firestarter or something?
it sets this stuff up automatically or with a few clicks

---

### Post by papapep on 2007-11-04
You should install a proxy in the ubuntu server and define it as the default gateway to the other machines. Then you can setup the proxy to filter content, allow or deny ip's, protocoles, mac's, domains, etc....
Documentation is easily found googling for squid proxy and ubuntu or linux.

Oh, I forgot to tell you that between the server and the other machines you should put a switch and that, in an ideal setup, your server should have two network cards.

---

### Post by LMSSML on 2007-11-04
Thanks people for the fast awnsers

Papapep , I would like toknow if I use a usb modem and make from my router a switch I could solve the problem.

But Why using a proxy couldn't i use the iptables for that  > allow or deny ip's, protocoles, mac's, domains, , 

Thanks for the help.

Probably my question are out of theme but I'm curious about these things.

Thanks again.

---

### Post by LMSSML on 2007-11-05
Hi 

Is my idea correct about what papapep said.
Or is there another way to do that.

---

### Post by az on 2007-11-05
Most routers allow you to set up a DMZ, which is a box just as you describe.  All traffic is routed through that box.  You don't need to have many network cards on your Ubuntu box that way.

---

### Post by LMSSML on 2007-11-06
And how it goes ubuntu connect with DMZ just for the IP ?

---

### Post by az on 2007-11-06
> **LMSSML said:**
> And how it goes ubuntu connect with DMZ just for the IP ?

I think the way it works on most routers is that you designate one IP to be the DMZ and then you designate one MAC to always use that IP address (if using DHCP)

---

### Post by LMSSML on 2007-11-09
Now I've got two nics and how it can be done, I've tried to configure firestarter with second nic but it says that my internet it's not available.

Could anuyone help

---

### Post by LMSSML on 2007-11-09
Does anyone could give me basic idea on how to do it

---


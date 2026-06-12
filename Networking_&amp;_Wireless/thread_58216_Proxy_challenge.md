---
title: "Proxy challenge"
date: 2005-08-19
forum: Networking &amp; Wireless
---

### Post by jaqkar on 2005-08-19
Hi There

I am looking to configure my Ubuntu box as a proxy/gateway with a twist, I want  traffic then from the Ubuntu box to go to the ISP's proxy. So my windows box will have the ubuntu box as default gateway and pass all traffic to it, the ubuntu box will send all traffic to the proxy of ISP. The ubuntu box only has one nic.

My setup looks like this: Internet > Router > Switch > Ubuntu/Win

I currently use the router for NAT but I cannot specify a proxy for it to use, lately the isp is not working so well unless i specify a proxy. I can easily specify it for http in the browser but I want to do this so all traffic goes to the ISP proxy and also I dont want to run something like squid on windows if I have ubuntu to do this. If all goes well I also want to just use my adsl router as a modem and use my ubuntu box as the primary firewall.

Can anyone please point me in the right direction.

---

### Post by jaqkar on 2005-08-21
Bump  ](*,)

---

### Post by jaqkar on 2005-08-23
OK I take it nobody on the forum knows how to do this or it must be so damn simple that nobody bothers to reply.  :neutral:

---

### Post by cybergypsy on 2006-10-29
Why not setup Squid under Ubuntu and point all the other PC`s at that ?

You will need to setup a parent proxy for squid and use the 'never_direct' command to make sure it always goes via this parent proxy.

#ubuntuppc is quiet........

---


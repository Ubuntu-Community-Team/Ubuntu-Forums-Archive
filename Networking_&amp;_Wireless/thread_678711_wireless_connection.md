---
title: "wireless connection"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by pmaloney1 on 2008-01-26
Hi all,
If you get this message againg I do apolagise as I am new to this. But my Problem is when I boot my system "Ubuntu 7.10" my wireless link lights up but I cannot connect to internet. I am runing a DWL-G122 high speed usb wireless adapter. Can anyone help a brain dead guy. 
Paul.

---

### Post by chewearn on 2008-01-26
Can you ping any device on your network, e.g. your router? 
```
ping <ip>
```

where <ip> is the IP of the device you want to ping (press CTRL+C to exit ping).

Also, can you post the output of ifconfig
```
ifconfig
```

---

### Post by pmaloney1 on 2008-01-28
Hi again,
Sorry for the delay in getting what you require but grandkids take up a lot of my time.

Firstly when I ping my router i get five packets sent and received a 0.04ms each.

now when I ifconfig I get the following.

"Wlan0
Link encap: Ethernet HWaddr 00 :1B : 11 : C8 : FD : SF
UP BROADCAST MULTICAST MTU :1500 Metric : 1
Rx packets :0 errors :0 dropped :0 overruns :0 fram :0
Tx packets :0 errors :0 dropped :0 overruns :0 carrier :0
collisions :0 Txqueuclen :1000
Rx bytes :0 (0.0b)
Tx bytes :0 (0.0b)

Hope this can help me 
Paul.

---

### Post by chewearn on 2008-01-28
That's strange.  I'm totally stumped.

You can ping the router, yet the ifconfig output showed that no IP is assigned to your wireless interface.  Unless I'm mistaken, this is an impossible situation.  Sorry to have to ask, but are you sure you have done it correctly?  Can you recheck?

---

### Post by pmaloney1 on 2008-01-30
Hi Astalavista,

Sorry for the delay in answering your last responce but I have finally got everything going by starting at the router and working back to the laptop. and yes it was me forgeting to give it an IP address, I was trying to do it by using the wrong system anyhow its working now so thank you very much for your help it got me doing a bit of investigation on my own and learnt a lot.
Paul

---


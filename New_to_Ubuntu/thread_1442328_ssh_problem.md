---
title: "ssh problem"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by cjv8888 on 2010-03-29
Last night my ISP was down so there was no internet at all.  I found that I could not network my computers at all using ssh, either wireless or even between 2 computers side by side wired to the routers.
Could someone knowledgable explain to me why this is so?
And what protocol would you suggest to network the computers when the internet is down?
Thanks.

---

### Post by KdotJ on 2010-03-29
How are you trying to ssh into them? Using their IP addresses on the subnet?

---

### Post by byStanderone on 2010-03-29
...am not so sure about your setup, but the isp has nothing to do with the local network, cept of course connecting to the outside world, take a look at your local network configuration.

---

### Post by KdotJ on 2010-03-29
Assuming that the computers are connected to the network (albeit not the Internet), go onto one of the computers you wish to ssh into, open a terminal and type: 
```
ifconfig -a
```

with the information it shows back, look for the net address (something like 192.xxx.x.x maybe)
then go back to the client machine and try ssh into the host with that adddress you just got. 

E.g

```
ssh user@192.xxx.x.x
```

---

### Post by cjv8888 on 2010-03-29
The internet comes via cable modem which is wired into a wireless router which also has wired connections.  
I usually connect by 'connect to server'
then choose ssh and use the local ip address: 192.168.1.101 etc
and it always works.
Last night, no matter what I tried, I got a timed out/cannot connect message.
This morning the ISP has come back on and the ssh is working again!
I thought the router should work independently of the availability of the internet. Strange.

I set static ip addresses for the computers with a number between 100 and 110 eg 192.168.1.101 but at the router I set the automatic DHCP to start at 192.168.1.111.  Normally this works well.  Do you think this setup made the router not see the computers below number 111 when the internet is down?

---

### Post by asmoore82 on 2010-03-29
This should not have been a problem.

The only thing I can think of is that some network services can be configured
to verify remote hosts with a reverse DNS lookup before accepting connections.

"time out" is what brought this to mind.

---

### Post by HermanAB on 2010-03-30
Probably because your dinky little home router wasn't working.  Chances are that your ISP itself was OK.

---

### Post by cjv8888 on 2010-03-30
> **HermanAB said:**
> Probably because your dinky little home router wasn't working.  Chances are that your ISP itself was OK.

No, I rang them last night.  The whole area was down.  When it came back on this morning, everything is working again including the ssh connections and internet.

---

### Post by HermanAB on 2010-03-30
Hmm, that still means that your dinky little home router wasn't working, since it provides DHCP and connects your home machines together...

---

### Post by Aped on 2010-03-30
> **HermanAB said:**
> Hmm, that still means that your dinky little home router wasn't working, since it provides DHCP and connects your home machines together...

Condescending much? 

Anyway, router probably got hung up trying to connect to the ISP or something and just stopped making proper connections. If it happens again, try restarting the router or just unplugging the uplink cable (the one that connects to your modem).

---

### Post by HermanAB on 2010-03-30
"condescending..."

I'm having constant problems with the dinky little router in my hotel apartment.  I think I need to go to Carre Four and get another model, since the this one is wearing out the power switch...

---

### Post by cjv8888 on 2010-03-30
> **Aped said:**
> Condescending much? 

Anyway, router probably got hung up trying to connect to the ISP or something and just stopped making proper connections. If it happens again, try restarting the router or just unplugging the uplink cable (the one that connects to your modem).

So you think the router was just shell shocked and not connecting while the internet modem was down, otherwise ssh should have been working and it is not a settings issue?

Thanks, I will try some experiments later on.

---

### Post by HermanAB on 2010-03-30
Yup, you should read up on 'ifconfig' and 'route'.  If the router works from a packet switching point of view, then you should always be able to set an IP address manually and connect to the other machine.

---


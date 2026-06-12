---
title: "internet works only for 20mins"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by donny.davis on 2011-06-29
hey its a new problem with my machine
i use a local internet connection
till yesterday it was working fine
but now i can only use it for only 15-20mins
i need to restart my machine to again access the internet

i hv heard tht its a virus problem in windows but how its affecting linux machine

---

### Post by goldshirt9 on 2011-06-29
could it not be a problem with the server / local network.
can you try to use another connection

---

### Post by trizrK on 2011-06-29
Can you give us some more info?
Are you connected via ethernet or a wireless card?

---

### Post by donny.davis on 2011-06-29
> **trizrK said:**
> Can you give us some more info?
Are you connected via ethernet or a wireless card?

ethernet...

---

### Post by donny.davis on 2011-06-29
i also hv windows on my machine
there is no such problems while using internet in it

pls help

---

### Post by Grenage on 2011-06-29
When the 20 minutes are up, are you able to ping the router?
Are you able to ping an external address? (try 8.8.8.8)
Do you still have a valid ip?:
```
ifconfig | grep "inet addr"
```

Does taking the network interface down and bringing it back up help?:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

That assumes that eth0 is your network adapter.

---

### Post by donny.davis on 2011-06-29
> **Grenage said:**
> When the 20 minutes are up, are you able to ping the router?
Are you able to ping an external address? (try 8.8.8.8)
Do you still have a valid ip?:
```
ifconfig | grep "inet addr"
```


i still hv ip address
i can ping to my gateway

---

### Post by donny.davis on 2011-06-29
> **Grenage said:**
> 
Does taking the network interface down and bringing it back up help?:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

That assumes that eth0 is your network adapter.

no this didnt work
i just want to know whether its my system problem or i should talk to my service provider...... but it works fine in windows...

---

### Post by Grenage on 2011-06-29
Can you ping 8.8.8.8?  If that works, can you ping something by name, such as google.com?  The reason I'm asking these questions is to find out if DNS is failing, or the local network connection.  I foolishly assumed that you were using a router, but now realise that you never mentioned the means of connection.  Is the ethernet cable going into a modem, or a router?

It's unlikely to be your service provider if it works in Windows.

---

### Post by donny.davis on 2011-06-29
even when the net is working it doesnt respond any bytes ( ping 8.8.8.8 )

---

### Post by Grenage on 2011-06-29
> **donny.davis said:**
> even when the net is working it doesnt respond any bytes ( ping 8.8.8.8 )

Do you have a firewall, or does your ISP block ICMP?  Can you ping *anything* on the internet?

---

### Post by donny.davis on 2011-06-30
i can only ping my comp and the gateway(router)

---

### Post by SeijiSensei on 2011-06-30
> **donny.davis said:**
> i can only ping my comp and the gateway(router)

Running torrents?

What happens if you turn your router off and on?  (You'll probably need to pull the power cord out of the router to accomplish this.)

---

### Post by donny.davis on 2011-07-02
hey thank you ppl for ur help

[COLOR="Red"]my internet service provider had some problem with his hardware
it has been sorted out now[/COLOR]

also i cant manage the router..... it is tht local providers property

anyways thankz

---


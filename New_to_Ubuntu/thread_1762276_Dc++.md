---
title: "Dc++"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by scorpious on 2011-05-19
I've installed linuxDC++ and want to connect to hub.canthub.info I get
```
*** Connecting to hub.canthub.info...
*** Connected
*** Connect failed: No route to host
*** Connecting to hub.canthub.info...
*** Connect failed: Connection timeout
```any idea's?

cheers

edit: not sure if It's important but I can connect fine when using windows.

---

### Post by lifelike27 on 2011-05-19
Did you setup DC++ in windows yourself? There might be some settings that you might have overlooked.

---

### Post by clicku on 2012-02-26
Hi,

I don't mean to bump this thread, but it ranks pretty highly in Google. **I know where you are**, what you're doing and a lot of people have this problem; It seems to strike every single OSX user as well.

You're trying to connect to a local address, and it seems that the PPPoE internet connection overrides LAN routes. You can avoid the issue simply by disconnecting from the internet, or by running something like 

```

ip addr del LAN_IP dev eth0
ip addr add LAN_IP/32 dev eth0 

ip route add GATEWAY_IP/32 dev eth0
ip route add 10.8.0.0/16 via GATEWAY_IP dev eth0 src LAN_IP
ip route add default via INTERNET_IP

```

---


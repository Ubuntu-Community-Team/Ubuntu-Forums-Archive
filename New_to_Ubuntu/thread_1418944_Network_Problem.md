---
title: "Network Problem"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by sudeepk on 2010-03-01
I use dual boot for windows xp and ubuntu 9.10. Suddenly i am unable to access internet on ubuntu but i am able to access in windows. In ubuntu i am able to ping localhost. what should i do?

---

### Post by cjhabs on 2010-03-01
Start by running "ifconfig" and see if the ip address and subnet mask are correct - maybe the machine failed to get a dhcp address from the router.

---

### Post by sudeepk on 2010-03-01
yes i have tried ifconfig. i have given correct ip addres. i also made a new network connection using  network setting applet. but its not working out.

---

### Post by Pritamsng on 2010-03-01
run "dhclient" 2 three times...

---

### Post by cjhabs on 2010-03-01
If you run "route" does it show that you have the correct gateway?

---

### Post by sudeepk on 2010-03-01
I cant see any light in my network port. and also i cannot see any MAC id when i run ifconfig. But everything is working fine in windows..

---

### Post by velle frak on 2010-03-01
Since you can use the internet via Windows, I assume you have no hardware problem.

Do as the guys/girls above suggested, find out if you have an ip adress using ifconfig in a terminal window, if not run dhclient if you have a dhcp server in your network or configure a static ip if you have not.

---

### Post by sudeepk on 2010-03-01
yes i have assigned ip address 
ifconfig eth0 192.168.1.203 up

and i have pinged my server that 192.168.1.1

but no response.

---

### Post by teward on 2010-03-01
Interesting, sounds like a hardware-ish issue...

Could I ask you to do something?  sudo ifconfig eth0 down up

Do that, it SHOULD take down the network connection and then reopen it.  If it doesn't work, then check the compatibilities of Linux and the network card

---

### Post by velle frak on 2010-03-01
Weird. What's the output of ifconfig?

---

### Post by Kakers on 2010-03-01
What does your interfaces look like?

```
cat /etc/network/interfaces
```

---

### Post by sudeepk on 2010-03-01
i Have tried sudo ifconfig eth0 up down nothings happening. i have tried /etc/init.d/networking restart. This is some funny problem. Till yesterday i was accessing internet in ubuntu. now all of the sudden its gone.

---

### Post by sudeepk on 2010-03-01
output of cat /etc/network/interfaces

auto lo
iface lo inet loopback

output of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:19:d1:ef:1f:f4  
          inet addr:192.168.1.203  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:800 (800.0 B)  TX bytes:800 (800.0 B)

---

### Post by sudeepk on 2010-03-01
ITs working now. But i don't know its a permanent or temporary solution. All I have done is plugged and un-plugged the network two to three times till i can see the light blinking. Now its working. pretty lame method.

---

### Post by cjhabs on 2010-03-01
I have seen something similar in the past with Vista and it turned out to be my old Motorola router not being very multi-OS friendly. Replacing the router resolved my issue.

---


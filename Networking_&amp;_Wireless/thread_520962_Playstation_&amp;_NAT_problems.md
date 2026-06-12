---
title: "Playstation &amp; NAT problems"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by c.dric on 2007-08-08
i'm using the following setup to connect my PS2 to the net :

(net)Speedtouch(10.0.0.138 )---eth--(10.0.0.50)Airport Express(10.0.1.1)---wifi---(10.0.1.201)UbuntuLaptop(192.168.0.1)---eth---(192.168.0.2)PS2

the PS2 can connect to the net fine ... i can play some games fine but i do have a lot of disconnect with some people and i suspect i may have problems with the firewalls on the adsl router and the airport AP.

i've setup the adsl router to use 10.0.0.50 (router facing ip of the AP) as default server.
i've setup the airport AP to use 10.0.1.201 (wifi facing ip of my laptop) as default server.
i've setup the connection sharing of Firestarter on the Ubuntu laptop.

is this setup correct ? 
i suppose i can't use the PS2 IP as default server on the adsl router, right ?

any tips welcome :confused:
thx

---

### Post by c.dric on 2007-08-09
one more thing i forgot to add:

i've setup firestarter on the laptop to forward all the needed ports to the PS2.
i would rather define a default server like on the router and ap but i couldn't find this option in firestarter.

---


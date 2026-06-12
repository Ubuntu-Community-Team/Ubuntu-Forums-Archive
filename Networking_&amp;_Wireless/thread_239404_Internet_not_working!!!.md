---
title: "Internet not working!!!"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by A_Babbar on 2006-08-19
im on another computer that i installed Ubuntu 6.06.1(da latest one) and i cannot connect to the internet on it.  I am connected to the internet via ethernet and a router which connects to a modem for broardband.
I tried to allow the ethernet networkin stuff using the Networking Administration Tool but there is no connection for the ethernet and i cannot add a connection either.
Could someone plz help!!!.....ive neva used Linux before.  Ive had similar problems on XP, but thn i could fix it because i knew what to do!!!

HELP!!!!!!!  ](*,) ](*,)

---

### Post by ESPOiG on 2006-08-19
hmm... ive had a similar prob, it ended up being my dns servers :P...
try that enter your ip, gateway, subnet and then enter your dns servers

etc/resolv.conf - dns
etc/network/interfaces - ip

or use the gnome network manager :D, if you dont know your dns servers contact ur ISP

---

### Post by A_Babbar on 2006-08-19
but ubuntu is just not recognising that i have a ethernet network card under connections...and there should b something there shouldnt there be??

also sorry for being a bit of an idiot, but i do not know what gnome network manager is and i can not find it under applications.
Also i do not fully understand what dns servers are.
and where do u fill in the ip, gateway etc...???

---

### Post by A_Babbar on 2006-08-19
also, ive tried to find the two files containing the dns and ip infomation and the ip one exists but just has a list of connections eg eth0 but no ip addresses and the dns one does not exist

i dont understand what to do!!!

HELP!!!

---

### Post by drtvasudevan on 2006-08-19
from a newbie:
your nic is not recogniseed?! what nic is it?
anyway do this inb terminal and see

> sudo pppoeconf

---


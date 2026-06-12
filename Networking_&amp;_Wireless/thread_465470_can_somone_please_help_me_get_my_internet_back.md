---
title: "can somone please help me get my internet back"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by marshall.robert on 2007-06-05
hey, i knocked my wifi dongle and now i dont get internet, but i can still connect to my network. it was working perfectly before. 

someone suggested to boot into recovery mode, but that didnt work.

can someone please help?

cheers

-rob

---

### Post by etola on 2007-06-05
what is your problem specifically ??

can you get an ip ?

run ifconfig and look at eth1 ( not specifically eth1, it may be eth*x* - the one with the wireless extension ). is there an inet address defined ?

---

### Post by etola on 2007-06-12
it seems that you can get an ip.

can you try to connect using knetworkmanager ? it sometimes miraculously corrects the network problems.

---

### Post by t4thfavor on 2007-06-12
how do you know your actually connected to the wireless network?

Are you getting an ip? If not than the problem probably isn't your wireless card.
I am not sure but you can try to config it from the commandline
with 

sudo iwconfig "ethX/athX/wifiX" essid "yourSSID" key "your wep key or whatever you use"

---


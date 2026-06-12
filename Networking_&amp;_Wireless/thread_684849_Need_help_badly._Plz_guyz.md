---
title: "Need help badly. Plz guyz"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by dying4004 on 2008-02-01
guyz i need ur helop badly. i need to setup my lan card in kubuntu 7  for internet. let me tell u my xp setup at 1st.

i have 2 lan cards.   my isp's utp cable goes in 1 lan card. then i setup that lan card with given configuration

ip: 192.168.22.195
subnet mask: 255.255.255.0
gateway: 182.168.22.1

dns: 202.168.254.4
        202.168.254.8


now i have done setup my kubuntu 7 with these settings but do not have any internet in kubuntu.


so i would be really grateful if u cud kindly tell me how to setup my internet in KUBUNTU 7 with these settings.   best regards

---

### Post by patryk77 on 2008-02-01
make sure that your gateway is **192**.168.22.1 and not 182

Also make sure that you are configuring the right card

---

### Post by dying4004 on 2008-02-01
sorry guyz it was typing mistake.  gateway is be 192.1.68.22.1

i can browse nternet now by typing this command.....    ifconfig eth0 up 192.168.22.195

but i need to input my dns server address everytime i reboot my pc. after rebooting dns server addresses get wiped out. so is there anyway that i can write these dns addresses permanently??  thnx guyz

---

### Post by patryk77 on 2008-02-02
add the DNS servers to /etc/resolv.conf (just add these two lines):

nameserver 202.168.254.4
nameserver 202.168.254.8

---


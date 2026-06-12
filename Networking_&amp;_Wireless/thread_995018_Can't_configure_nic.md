---
title: "Can't configure nic"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by mikee55 on 2008-11-27
Hi, I have 2 NIC's. eth1 connects to my cable dsl and works fine, I can surf the web. eth0 connects to my LAN. I've installed Firestarter, but it says device eth0 is not ready. It says I need to check device settings and make sure my internet connection is active.
Network Configuration doesn't help either?

Thank you,
 Mike

---

### Post by eder.apt-get on 2008-11-27
Do you really need Firestarter? I mean, it´s a gui, but you can do IP masquerading without installing anything:
[http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/)

Anyway, maybe you might check this forum: [http://www.linuxquestions.org/questions/linux-networking-3/ubuntu-box-as-router-319188/](http://www.linuxquestions.org/questions/linux-networking-3/ubuntu-box-as-router-319188/)
It may give you a way to go..
(I´ve found tons of answers while googling "firestarter eth device not ready")

---

### Post by mikee55 on 2008-11-27
Hi, I can't believe everything is so complicated? Why do you need to type in all that just to do a Masquerade, in M$XP all I did was tick the shar e this connection with other computers on the internet connected card, aand job done. Why should it be so hard in Linux?

Mike

---

### Post by mikee55 on 2008-11-27
Tried Masquerade, nothing happens???

Mike

---

### Post by mikee55 on 2008-11-27
Anyone, please?

---

### Post by mikee55 on 2008-11-28
Where's everyone gone??????????????????????????????

---

### Post by Ayuthia on 2008-11-28
I was thinking that you had to assign an ip address for eth0.  Did you do that already?  I could be wrong about this though (It might apply to dhcp3-server--I can't remember).

---


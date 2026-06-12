---
title: "[Ubuntu &lt;=ethernet cable (samba)=&gt; Ubuntu] file transfer is a slow 6XX kbs"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by theweasel2345 on 2011-07-10
I am trying to move way from transfering files from one computer (Dell Inspiron B120 with a dead ethernet card/Ubuntu 11.04) to another (Asus 1005PE/Ubuntu 11.04) by means of 8Gb flash drive. Both computers currently have Samba file share that allows me to transfer files between each computer( The Dell uses a wifi usb adapter). Now, being that the wireless samba share was very slow, I connected an ethernet cable from my asus to a ethernet cable to usb adapter which is connected to my Dell, which I assigned the auto eth0 on the asus to ip adress 10.0.1.2/ netmask 255.255.255.252 and auto eth1 on my Dell to ip adress 10.0.1.1/netmask 255.255.255.252. Though I did see a speed boost to 600kbs, the speed is not even near 1mbs. Is there any way I can speed up the samba file transfer? I love both samba and ubuntu, and I am terrified of Filezilla. Thanks in advance!

---

### Post by theweasel2345 on 2011-07-10
I have also tried removing the pound sign from socket option = TCP_NODELAY. It didnt help at all

---

### Post by theweasel2345 on 2011-07-10
Bump

---


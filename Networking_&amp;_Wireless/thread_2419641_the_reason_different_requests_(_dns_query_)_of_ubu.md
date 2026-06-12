---
title: "the reason different requests ( dns query ) of ubuntu clients to internet"
date: 2019-05-24
forum: Networking &amp; Wireless
---

### Post by l0pht2 on 2019-05-24
Hello 

When the software  wireshark run in ubuntu desktop, see packets  cannectivity-check.ubuntu.com and ntp Without running out browsers and  softwares for request to internet or servers .

Why  ubuntu used  of the type  communication for Submit a requests?
of course, Submit a request ntp  is for update data  & time, but  some Submit a requests are imperfect (TCP 3 way handshake process).
Does it can problems for users in ubuntu?

---

### Post by TheFu on 2019-05-24
You can change the time servers used in /etc/ntp.conf.  Any NTP server(s) will work.  Having accurate time is very important for almost all internet cryptographic connections.


> Does it can problems for users in ubuntu? 
Perhaps you can rephrase that question?

---

### Post by l0pht2 on 2019-05-25
order of the problem for users,hackers use of this methods for connection and Exchange data with target?
 when the servers monitor datas  input and output,how they detect are Secure connections from unsafe ?
  even Can be seen incomplete communication and Cryptography.

Does The  tcp 3-way handshake connections can use for attakcs?
 becuase more submit requests servers is through domains,

---


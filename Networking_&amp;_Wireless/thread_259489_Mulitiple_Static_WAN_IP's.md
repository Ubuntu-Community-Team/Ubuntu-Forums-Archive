---
title: "Mulitiple Static WAN IP's"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by MrBrownstone3g on 2006-09-17
Hi All,

I am currently setting a weberver that can accept SSL and standard http.  I would like to know if it is possible to do this using one NIC with on alias i.e eth0 and eth0:0 and route then incoming connection to a second NIC eth1 using the standard internet connection sharing method.  eth1 one would than be connected to a router which would act as the dhcp server and internet connection for the LAN.

Would the method described above work?

Any feed back would be much appreciated.  

Cheers 
Graham

---

### Post by kidders on 2006-09-17
Hi there,

I'm not quite clear on where your web server fits into this arrangement, but, in terms of forwarding packets around the place, you should be able to do almost anything you can imagine.

Out of interest, why did you set up an alias for one of your network interfaces?

---

### Post by MrBrownstone3g on 2006-09-17
Hi

Apache can't serve SSL encrypted sites while using name based virtual hosting.  What I would like to do is use one static ip for the SSL site and the  alias to serve none encrypted sited using name based vitual hosting. 

Cheers
MrBrownstone3g

---

### Post by kidders on 2006-09-17
Well, so long as you only intend to host a single SSL-based service on any given port, there is no need to alias your network interface. You can use the same interface to host as many additional (unencrypted) name-based virtual hosts as you like.

---


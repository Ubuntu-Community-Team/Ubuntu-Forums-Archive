---
title: "NFS network and firestarter"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by jrev on 2007-06-19
Hi all,;)

I have an NFS local network with three PC's on ubuntu dapper 6.06
One is the Internet sharing machine and the other two are the clients.
My Internet connexion is with an external modem 56k.

The internet sharing is OK at this time 

Should I use firestarter ? on which PC's and why ?

Hope you can give me a practical advice

---

### Post by p_quarles on 2007-06-19
You don't need to run firestart unless you want to specifically open up certain services to outside computers, and if you're running on a dial-up connection, you don't have enough bandwidth to do that. 

Ubuntu is preconfigured with a very strong firewall. The only thing that Firestarter adds is the ability to configure it from the GUI.

---

### Post by jrev on 2007-06-19
Thanks for this clear answer :p

---


---
title: ":: PROXY PROBLEM &gt;&gt; ::"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by mohsin on 2005-08-09
hello .. 

 well i m using .. LAN net via proxy 

 i did these 

 give proxy to eth0 .. 192.168.0.1 port 8080 

 give mozila that same 

 other network proxies as same but when i browse :( .. mozila gives error .. 

 "unable to connect chek proxy settings "


        while ping works .. when i ping to that server add it reply .. 

 what is the problem could any one plz tell me

---

### Post by blind0wl on 2005-08-10
Ok...What is the IP of your machine?  Can you ping 192.168.0.1?  Is the proxy actually setup correctly?...As in tested elsewhere?...Do you have any exceptions in mozilla?  If your running the actual proxy server on your box...you'll need to make sure the localhost and 127.0.0.1 are taken out of the exceptions in proxy settings of mozilla.

---

### Post by mohsin on 2005-08-10
well .. my machine's static ip that is alloted to me 

 192.168.0.101

 default mask is .. 255.255.255.0

 default gateway or prxy is .. .192.168.0.1 i use this .. to browse net in windows .. 

 what i should do to use net over ubuntu now  :roll:

---

### Post by blind0wl on 2005-08-10
So you can ping 192.168.0.1?

---


---
title: "Selective use of a proxy in function of ip addres"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by Hebus95 on 2006-10-08
Hello,

I frequently need to setup a ssh connection through the proxy of my university in order to browse internal webpages when I am at home.
And when I have to browse extern pages I switch off from the proxy in the firefox preferences.
(I prefer not to browse extern webpages through the proxy even if it's possible)

In result i constantly have to manualy switch between proxy connection and direct connection, which is a little boring...

My question is :
Is there a possibility to automatically switch the proxy on and only if I try to access pages from the domain of my university ?
I'm looking for a very light solution, not the big firewall :mrgreen: 


Regards

---

### Post by Hebus95 on 2006-10-08
Any idea?

---

### Post by spd106 on 2006-10-09
Perhaps look into creating a VPN tunnel connection (tun0). This will allow you to route connections to the network through it. Try OpenSSH website, there's a brief description in wikipedia [http://en.wikipedia.org/wiki/OpenSSH](http://en.wikipedia.org/wiki/OpenSSH).

---

### Post by Hebus95 on 2006-10-09
Thank you for you answer, 
However I'm not sure I was clear enough (or perhaps i don't understand your answer since i don't kwon vpn very much)
I insist I already know how to create ssh connections and use the proxy.

The current situation is the following :

- For common internet pages (ubuntuforum.org, google etc) -> The browser has to use direct connection to the internet

- For the domain of my university -> The browser has to use the proxy.

For this purpose, i have to manually switch the proxy on or off in the preferences of Firefox.

I would like to make this automatic and at the system level.

My first ist idee is to use ip filtering. (but how ?)

For now I'm looking at the vpn tunnel connection, but whithout solution yet. 

Regards

---


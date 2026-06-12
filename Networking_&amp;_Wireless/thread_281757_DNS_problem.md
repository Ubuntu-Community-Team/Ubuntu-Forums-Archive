---
title: "DNS problem"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by bacsa81 on 2006-10-21
Dear Friends!
I have a issue with the name resolving on my Edgy.
I just installed on my new HP nx7400 laptop the rc and I entered the same data for my network which one works perfectly with my desktop pc, a breezy.
Unfortunetly on the Edgy the names are not resolved, DNS not working for me.
The DNS is the localhost 127.0.0.1, it is set in the hosts as localhost.localdomain localhost csaba, I have entered my routers ip as well into the hosts list it is 10.0.0.2
What is causeing this?
Thank you for any help..
Cheers Csaba

---

### Post by gustolove on 2006-10-21
wait so you said that the DNS u entered was 127.0.0.1? or did you enter your router ip?

---

### Post by bacsa81 on 2006-10-21
I entered 127.0.0.1 into the DNS field, the router I added to the hosts list

---

### Post by gustolove on 2006-10-21
well since your computer is not a DNS server 127.0.0.1 is not going to work for the DNS.. you should try putting the router address in the DNS field

---

### Post by emersony on 2006-10-21
I wasn't aware that either Breezy or Edgy installed a DNS server, and even so you would certainly have to add/configure your forwarding. 

E.

---

### Post by bacsa81 on 2006-10-21
I changed it to the routers ip, went to the about:config inside Firefox now I have net in browser!
But Gaim or Add Remove programs nor command line apt can resolve names...

---

### Post by bacsa81 on 2006-10-25
Sorry for the long silence, but I have been away.
So I could figure out that I need to disable ipv6 because my router doesn't supports it, but even so it couldn't resolve all the addresses, so I have entered my ISPs DNS addresses so my internet wortks fine for me. :) 
Is there any way to install a DNS server into my edgy so I can resolve the names by my own pc? :-k  It is a laptop so it would be good to have the NetworkManager running. :mrgreen: 
Any ideas?
Thanks 
Csaba

---


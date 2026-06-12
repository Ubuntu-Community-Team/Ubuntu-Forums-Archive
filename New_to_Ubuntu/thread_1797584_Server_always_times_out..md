---
title: "Server always times out."
date: 2011-07-05
forum: New to Ubuntu
---

### Post by Veltan on 2011-07-05
So I've set up my LAMP server, I installed my mediawiki, I forwarded my ports to 8080(port.conf is listening to 8080 aswell), and I had everything working fine. Then because I was not using it at the time and I didnt want it to be accessed I disabled the port forwarding for 8080. I may of also stopped apache2 I think which was totally unnecessary if I disabled the port forwarding.

Anyway, my problem is that the server no longer works. Every time I try to connect to a port it simply says timed out. I cant connect to [http://localhost](http://localhost) or the servers internal IP address. I can only access it via PuTTy and VNC. Can anyone help me figure this out or give me some insight?

---

### Post by androssofer on 2011-07-05
> **Veltan said:**
> So I've set up my LAMP server, I installed my mediawiki, I forwarded my ports to 8080(port.conf is listening to 8080 aswell), and I had everything working fine. Then because I was not using it at the time and I didnt want it to be accessed I disabled the port forwarding for 8080. I may of also stopped apache2 I think which was totally unnecessary if I disabled the port forwarding.

Anyway, my problem is that the server no longer works. Every time I try to connect to a port it simply says timed out. I cant connect to [http://localhost](http://localhost) or the servers internal IP address. I can only access it via PuTTy and VNC. Can anyone help me figure this out or give me some insight?

i'm a little confused by what your wanting to do/ whats wrong... so u got ur lamp on 8080, thats fine. but if you turned off apache, when you try to connect [http://localhost/](http://localhost/) to its gonna try to access apache on port 80, which will timeout cus apache aint ther. if u can putty in try firing up apache again and c wot happens.. 

is it on ubuntu server? or on ubuntu desktop?

---

### Post by Veltan on 2011-07-05
It's on ubuntu server, and I started apache again now that I want to use it, but the server refuses to be accessed. I'm not really sure what would cause this kinda of problem. It refuses to be accessed by IP address.

Ok, marking as solved, just figured it out. Somehow my internal IP address changed... Anyone know how something like that happens?

---


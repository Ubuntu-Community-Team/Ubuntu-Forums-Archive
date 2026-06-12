---
title: "My Internet suddenly stopped working."
date: 2011-05-03
forum: New to Ubuntu
---

### Post by amityadav9314 on 2011-05-03
Hi there!
Something weird has just happened to me, my internet (Ethernet) has suddenly stopped working.
Last time when i shutdown my ubuntu 10.10, everything was fine, but when I opened my computer again, my google chrome browser is showing 105 internal error, server not resolved. 
Any help will be appreciated.
Thanks!

---

### Post by Steve H on 2011-05-03
Are any of your other browsers working or is it just Chrome?

It might be worth clearing any cache that you have and checking your DNS settings. I think the cache settings are in the "spanner" on Chrome.

---

### Post by amityadav9314 on 2011-05-03
no, it is happening with all the browser including firefox and opera
One weird thing is that i can log in to my skype account, can chat on that, i have installed eset nod32 antivirus in my ubuntu 10.10 which i can update but i can  not load any pages on any of my browsers.

---

### Post by Steve H on 2011-05-03
So at least you know the connection is working. It looks like port 80 may be blocked (just a guess).

Have you got a firewall running? Usually UFW (the Ubuntu firewall) allows port 80 by default. Might be worth checking your error logs for any blocked traffic.

---

### Post by amityadav9314 on 2011-05-03
> **Steve H said:**
> 

Have you got a firewall running? Usually UFW (the Ubuntu firewall) allows port 80 by default. Might be worth checking your error logs for any blocked traffic.

How to check that whether my port 80 is blocked by firewall UFW?, please tell me

---

### Post by BertN45 on 2011-05-03
I would suspect the dns service. You get this effect if for some reasons your dns service does not work anymore. 

You can check it by typing "ping www.google.com" in the terminal and "ping 74.125.229.83". If the first one does _not_ reply and the second one does reply, you have a dns problem.

Sometimes it is caused by the router or modem and it helps if you turn it off for 10 seconds.

---


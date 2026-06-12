---
title: "Checking Internet Connection with ShieldsUp"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by unf4b1x on 2008-12-28
Everytime I connect to the Internet I always try to begin/start it with checking my connection through the ShieldsUp.  I think everyone knows about it and what does it mean.. To me, if the text below the "proceed" button is green then your ip cannot be check using "[[COLOR="Blue"]reverse dns[/COLOR]]("http://en.wikipedia.org/wiki/Reverse_DNS_lookup")?" But the problem comes up when it becomes red meaning: **The text below might uniquely identify you on the Internet**.  It can be **uniquely associated with the following "machine name":** meaning your box. I usually got it in green.

What is the difference having your ip address checked and be known using reverse dns? What trigger the change from being green to red? What has gone wrong with my connection? Can somebody please correct me if I'm wrong?

---

### Post by cariboo on 2008-12-28
The results from Shieldsup really don't mean a lot, If you are connecting through a router, it will check the router. As far as your ip address being invisible, there is no such thing. Every web site you go to has a record of your ip address.

As far as the change goes, if you are connecting through a router, did you change any settings lately? If you are connected directly without a router, have you installed any services that are listening for connections for example apache2, ssh or something similar.

Jim

---

### Post by unf4b1x on 2008-12-30
> **cariboo907 said:**
> ... As far as the change goes, if you are connecting through a router, did you change any settings lately? If you are connected directly without a router, have you installed any services that are listening for connections for example apache2, ssh or something similar.

Jim

I don't think I have downloaded or installed any server services but definitely installed other applications.. like games and other updates from time to time or whenever a notification for updates pop up. But I don't know if along with those updates something must have installed along with it. Can you see a log of the commands you have used in a terminal console with the results in it? I dunno, maybe I have used a command without understanding fully the complications of using it.

---


---
title: "406 Not Acceptable"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by pizzathahut on 2008-11-12
Howdy yall'!
I'm fairly new to Ubuntu and have been having this issue from day one.
My website works fine on any other OS but nothing on linux. When I try to pull up my site in ubuntu I get the error 406 Not Acceptable.

I have tried other untunto browsers to ensure it isn't a firefox issue. 
I have updated everything on my side.
I have edited the .htaccess file to disable  mod_sec which may have been the source, still no resolution.
I have contacted my hosting company and they say everything should be a-ok with them and isn't anything on their side (which I'm not fully satisfied with their answer or competence)

I cannot access anything within my domain. Has anyone ever had this problem in the past? 
This problem has kept me from using ubuntu for some time now.

---

### Post by jonobr on 2008-11-12
Hey,

Try some commands on the terminal side of things to see how it shakes out.
Go to apps->accessories->terminal
I would try a w3m from there (w3m is a text based browsers.
eg
enter w3m google.com

It should give you back text style google page.
(Hit q to quit this screen)
You can try IP address,
w3m 209.85.171.99
(again q to exit)

Of course you would use your ip address or name to connect.

---


---
title: "can you answer this question?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by linux000019 on 2009-05-26
so, i set up my home computer to act as a host; tested it from another home computer lan and it worked. now im at the library and i cannot connect using my networking software... the software tested as working. question i have is, what part is he error coming from, the library network, the home network, or the settings? if you asked me i would say the library network is not allowing anything out, how would i test this theory though? i can't figure it out.

---

### Post by Celauran on 2009-05-26
How did you test it at home? How are you trying to connect to it now? Does it have a static IP? Are the appropriate ports open on the firewall?

---

### Post by halitech on 2009-05-26
when you say you tested it from another home computer lan, do you mean a computer on your lan or a different location? Also, what type of connection are you trying to make to your computer from the library? Chances are the network at the library is probably set up to only allow traffic going out for browsers and maybe email (ports 80, 25 and 110)

---

### Post by Mornedhel on 2009-05-26
[B]"can you answer this question?" "No."

[/B]Seriously, please use more descriptive topics.

Can you connect from the library to known working servers using the same software ?

You could also try a port scan (System > Administration > Network Tools) to check if the port you're using is open in the library.

---

### Post by stefangr1 on 2009-05-26
Have you forwarded the appropriate ports in your router? If you didn't, you can't access you server from outside the home network. If you did, what ports, and for what software?

---

### Post by sandyd on 2009-05-26
heres a nice way to answer the questions
go to ipchicken.com

write down the ip

then do
```

sudo apt-get install nmap
nmap <put ip address here>

```

if that particular port isn't open, its your router

if the ports open, its your library. isn't it simple?

---

### Post by stefangr1 on 2009-05-26
> **carlee said:**
> 

if the ports open, its your library. isn't it simple?


Sorry to hijack this threat, but I just tried this piece of software and I get more ports than that I actually opened, like 21, 23, 80, whereas some of the ports that I have in fact open (especially in the higher ranges) do not show up. So I guess the program isn't magic...

---

### Post by dmizer on 2009-05-26
Thread closed. We do not support bypassing security restrictions put in place on a network which you do not administer.

---


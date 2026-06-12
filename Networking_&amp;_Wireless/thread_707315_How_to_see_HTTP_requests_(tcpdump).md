---
title: "How to see HTTP requests? (tcpdump?)"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by kikazaru on 2008-02-25
How can I see the HTTP requests going out from my computer? 

I managed to get some information using 

tcpdump -i ath0

I want to see the outgoing HTTP messages in text though, and all I get is nasty binary. I think the HTTP GET request should be formatted in ascii?

The reason I'm asking is because I have some C++ code for sending HTTP requests but it does't work on some pages because the website discriminates between my request and a firefox (for example) request. 

I tried using wget but that was refused too, and not just based on the browser identifier. At least, I don't think so...

Anyway, please help :)

---

### Post by The Cog on 2008-02-25
It would probably be easiest to install wireshark. It then appears in Applications->Internet. Choose Wireshark (as root) for capturing packets. It has a nice graphical display.

---

### Post by jonallport on 2008-02-25
As a workaround you can set the user agent as a parameter in wget.  

Try adding 

--user-agent='Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1)' 

to the wget request, that should pretend to be IE 7 running on WinXP

---

### Post by kikazaru on 2008-02-25
Dear The Cog Sir,

Thanks for you excellent advice. Wireshark seems to be exactly what I was looking for. I'll try it this evening. 

Also thanks to jonalllport. Unfortunately changing the user agent alone wasn't enough.

---


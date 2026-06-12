---
title: "Can't load www pages."
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by sparkzi on 2008-01-13
Hello,
I have installed Ubuntu 7.10. I Have ZX DSL 852 Modem. I installed ubudsl application with drivers and everytnig shuld work but:
i can download files 
i can use torrent 
i can upgrade update my ubuntu and internet connection is working very good, but i can't open www sites. I checked dns with "dig" and everything is good. When i want to open any page i have to wait very long. Often there are timouts.
I don't know what to do because, everything works except www sites... Please help

---

### Post by OlleyK on 2008-01-13
Can you ping any www site in Terminal? What Browser do you use?

---

### Post by sparkzi on 2008-01-13
Yes. I can ping and response is very quick! The same happens when I enter site adress to browser. Title of page change very quickly but later i have to wait very long. I use firefox and opera so i think that that is not browser problem.

---

### Post by twright on 2008-01-13
try "w3m www.google.com" and "firefox 208.69.34.230"

if the first works firefox is broken, if the second works then DNS is broken

also try "sudo -i && echo ipv6 >> /etc/modprobe.d/blacklist"

---

### Post by sparkzi on 2008-01-13
In w3m every  site is working very quick.
My dns are good.
I installed galeon and other browsers and in every I have the same problem... some pages work good but others aren't or work one time good and then second time bad...

---

### Post by twright on 2008-01-13
hi,
try this:
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)


it should speed it up considerably

---

### Post by sparkzi on 2008-01-13
I have said: my dns are good :) 
I found something interesting: when i make a speed test for example on numion.com there is always tex like: Upload can't be masure. To less data.   So there is problem with upload ;(

---


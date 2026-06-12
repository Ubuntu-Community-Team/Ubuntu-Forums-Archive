---
title: "Feisty, but not Gusty."
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by sekinto on 2007-10-19
Okay, so when I first installed Feisty Fawn it detected my wireless card, detected my network, asked for my WPA pass, connected to the router, then connected to the internet. Now I installed Gusty Gibbon and it detected my wireless card, detected my network, asked for my WPA pass, connected to the router, BUT DIDN'T CONNECT TO THE INTERNET. I have no MAC list enabled or any other router settings that should cause conflict. I just find it weird that it worked in Feisty but not Gusty.


Here are my specs:

Card-
GigaFast USB B/G WF748-UI

Driver Ubuntu Uses-
zd1211rw

Router-
ActionTec GT701 (I think)

---

### Post by sekinto on 2007-10-19
Anyone?

---

### Post by sekinto on 2007-10-19
Could someone please help me?

---

### Post by jlombs on 2007-10-19
There are a few threads about this...
I would suggest waiting it out a few hours
You might have a DNS issue - there are a few threads discussing changing your DNS settings but nobody has come back and said it was a def fix yet.

---

### Post by sekinto on 2007-10-19
So there's really nothing I can do at the moment. :(
That sucks because I hate using the Feisty Live CD to go on the internet.

---

### Post by Phil Airtime on 2007-10-19
If you change your DNS servers (in System - Administration - Network) to the following, it may work. It does it for me if I ever have trouble connecting to websites. The servers are provided by [Open DNS](http://www.opendns.com/), an independent DNS provider. 

- 208.67.222.222
- 208.67.220.220

---

### Post by sekinto on 2007-10-19
> **Phil Airtime said:**
> If you change your DNS servers (in System - Administration - Network) to the following, it may work. It does it for me if I ever have trouble connecting to websites. The servers are provided by [Open DNS](http://www.opendns.com/), an independent DNS provider. 

- 208.67.222.222
- 208.67.220.220

THANK YOU SO MUCH!

Changing the DNS servers worked PERFECTLY!

---


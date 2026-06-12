---
title: "How to know if this 'puter is &quot;behind a proxy&quot;?"
date: 2013-12-24
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2013-12-24
How do I determine is this computer is "behind a proxy"? How would I remove the proxy? This is my home computer. I connects to the internet via wifi. Short of making the computer vulnerable to the outside world, I don't want a proxy and AFAIK, I have no knowingly installed a proxy on this computer or it's wifi access.

What this is about is setting up a Raspberry PI with RaspBMC. I format the sd card, run sudo python install.py and answer the questions. The sd card gets a partition with 76 meg in use. I set up the system as "USB" and have tried both wired and wireless to get to the Raspbmc update server, but it fails. The sd card is less than a month old. It has been re-formatted a dozen times due to the update server not connecting.

---

### Post by ian-weisser on 2013-12-24
Whose wifi is it?
How does the wifi reach the internet?

---

### Post by Mark_in_Hollywood on 2013-12-24
I know that is English, but I'm scratching my head and thinking: "? ? ?" is he asking? 

"Whose wifi is it?"

It's AT&T's U-verse? 
It's mine I pay for it?

"How does the wifi reach the internet?"
from my wifi adapter in the computer's usb port to the ISP provided dsl modem and from there to who-know-where.

I'm pretty sure none of my answers help you, so please ask the question, again, knowing that I'm computer illiterate. PLEASE.

---

### Post by ian-weisser on 2013-12-24
Those answers do help.
You're (effectively) not behind a proxy. If your ISP is running some kind of proxy, you shouldn't be able to detect it's presence.
Time to look at your update and network settings.

It's considered your wifi, since it's from your router. It would be different if you were mooching wifi from a neighbor or coffee shop or your employer. Those might use a proxy or filter that could affect updates.

---

### Post by lisati on 2013-12-24
I'm with ian-weisser on this one.

None of the routers and/or modems I've used on my home broadband connection (mostly acquired via my ISP) have had any kind of proxy installed as part of their out of the box defaults. The only time there has been any kind of proxy enabled is when I set one up myself.

I'm guessing that the OP is using their own connection. As a rule, it's uncool to use a neighbour's WiFi without their knowledge or permission; doing so could easily strain relationships.

---

### Post by Mark_in_Hollywood on 2013-12-27
I'm saying this only once. I pay for 1/2 the bandwidth, every month. Try to stay on-point, please.

---


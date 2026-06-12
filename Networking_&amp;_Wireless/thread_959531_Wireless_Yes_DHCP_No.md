---
title: "Wireless Yes DHCP No"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by digitalzen on 2008-10-26
{Please forget/forgive the title, I have since resolved some issues.}

Hey guys, I hope this has not been address before. 

I have a Dell Mini N Series with Ubuntu 8.04.

I can not seem to connect to Secure networks, is there a know problem with ubuntu and WEP/WPA/WPA2 that Im missing?

I should mention the default wireless connection (although i forget the name) did work on unsecure wireless connections before I switched to using Wicd.

It will work on wired connection.

I have tried this on known good networks, both at work and at home.

Any ideas, or suggestions? What can i provide to help speed up any "try this" ideas.

Thanks very much in advance, again I hope this is not a common question.

Digitalzen

---

### Post by nixscripter on 2008-10-26
What is the wireless card, and what driver is it using? Post the output of the command from the terminal: ```
lshw -C network
```

---


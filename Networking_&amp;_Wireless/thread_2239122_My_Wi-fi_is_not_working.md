---
title: "My Wi-fi is not working"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by Wilman_Darnasutisn on 2014-08-12
hi
this is my first time install Ubuntu. I previously Linux Mint users.
the problem is when/after i'm install Ubuntu 14.04.1, i'm cannot find my network wireless in driver manager. if in Linux Mint, I can immediately turn on the wi-fi in the driver manager. and immediately be able to use wi-fi. and does not require a wired connection. may i wrong when installing ? or i must be prepared some file for wifi in Ubuntu?

many thanks to u
note: i dont have wired connection in my home :(

---

### Post by chili555 on 2014-08-12
> or i must be prepared some file for wifi in Ubuntu?Probably! 

Before we can identify what additional file you may need, please let us see some details about your wireless device. Open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---


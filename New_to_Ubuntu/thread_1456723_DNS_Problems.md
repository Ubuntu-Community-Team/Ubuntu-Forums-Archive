---
title: "DNS Problems"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by coldfusion1313 on 2010-04-17
When I use the wireless on my laptop in 9.10. It will work, but I have to turn off networking then turn it back on, for the internet to work again. This just happen I have been running 9.10 for 6 months and this has been happening for 1 month-ish. 

This only happens on my home wireless; at school and my neighbours wifi work fine. Our iMac and Windows computer get the same problem but not as bad as my laptop. Is it our router. Is it time for a new one? :(

Thanks for the help 
Mark

---

### Post by undecim on 2010-04-17
What router is it?

Maybe you need to configure it better.

And how do you know it's a DNS problem? Can you ping your rotuer when the wireless isn't working?

If you're sure it's a DNS problem, compare your /etc/resolv.conf files when your internet is and isn't working to see if that gives you any clues as to what the problem is.

---

### Post by coldfusion1313 on 2010-04-17
when the wifi stops working, web pages hang the address doesn't change and it will keep loading but nothing will happen.

---

### Post by undecim on 2010-04-18
> **coldfusion1313 said:**
> when the wifi stops working, web pages hang the address doesn't change and it will keep loading but nothing will happen.

While the wireless isn't working, open a terminal and paste this command:
```
ping 8.8.8.8 -c 5 -i 0.5; ping google.com -c 5 -i 0.5
```

See what you get.

---


---
title: "Failing to browse the internet but able to access ubuntu serves"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by Mishal on 2006-11-09
After tinkering around with rppppoe etc etc, I finally managed to connect to the internet. But the only way I found I was indeed online was when I downloaded software through Synaptic.

I can't browse using Firefox or Epiphany. I can't log in to GAIM. I can't do anything else. What seems to be the problem?

Edgy 64-bit running on Acer Aspire 5102 with a Bell Sympatico DSL connection.

---

### Post by stream303 on 2006-11-10
Does your **/etc/resolv.conf** file have one of your isp's dns nameservers listed first?  Just a thought - if not, this quickie howto might help:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

Let's see if this is the situation...

---

### Post by Mishal on 2006-11-11
Thanks. It is definitely a problem with the DNS. But I can't seem to find the place where I need to change the DNS in the router settings.

I am going to post my problem in that thread you linked to. :)

---

### Post by stream303 on 2006-11-11
Should be able to add them in the System > Administration > Networking tabs, but placing them in the router setup is a fine idea.

---


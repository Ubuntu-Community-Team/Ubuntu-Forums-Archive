---
title: "[SOLVED] How can I recreate my hosts file?"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by vgrisham on 2008-03-29
Last week, I was having problems with my internet connection. It wound up being my router. In the process of troubleshooting, I deleted all the hosts from the hosts list in the network manager, which was not smart. Anyway, I need to recreate the list. 

Would you please list for me what is in a typical hosts file. In case it matters, I'm running Hardy 64 bit. 

Thanks,
Vaughn

---

### Post by Eiríkr on 2008-03-29
Here's an empty hosts file template.  Replace the caps with your own hostname.  
```
127.0.0.1 localhost
127.0.1.1 HOSTNAME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Cheers,

Eiríkr

---

### Post by vgrisham on 2008-03-29
Thank you very much. That did the trick.

---

### Post by Eiríkr on 2008-03-29
Glad to help.  :D  Just be sure to pass along the help some day when you run across a thread where you can pitch in.  ;)

Cheers,

Eiríkr

---

### Post by vgrisham on 2008-03-30
> **Eiríkr said:**
> Glad to help.  :D  Just be sure to pass along the help some day when you run across a thread where you can pitch in.  ;)

Cheers,

Eiríkr
Dude (or Dudette), I wish the thank you button had been around after I first got going on Dapper. I was the noob geek wanna be help Meister Ubuntu evangelist. Sadly, I have but one thanks to my credit. Sigh.

---


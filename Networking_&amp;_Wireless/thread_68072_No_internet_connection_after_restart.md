---
title: "No internet connection after restart"
date: 2005-09-22
forum: Networking &amp; Wireless
---

### Post by dpogs on 2005-09-22
I flawlessly setup ubuntu OS, after installation it all goes well especially the internet. after restart, i cannot connect to the internet. Every time I click the fire fox browser it just simply say "It could not be found. Pleare check the name and try again.

how to fix this kind of problem. i applied what i read in the forum but it no help.

---

### Post by Lem on 2005-09-22
Sounds like the router and DNS issue.

Try the following;

```
sudo gedit /etc/resolv.conf
```

Change the nameserver IP to the DNS lookup IP supplied by your ISP

then use 
```

sudo chattr +i /etc/resolv.conf
``` 

to lock the file so it can'tbe changed by Ubuntu

---


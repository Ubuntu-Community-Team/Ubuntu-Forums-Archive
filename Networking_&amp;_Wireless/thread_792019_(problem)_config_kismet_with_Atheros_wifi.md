---
title: "(problem) config kismet with Atheros wifi"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by weapon-x on 2008-05-12
hi i just buy a new compaq laptop its F700 frm best buy ,, and i install the ubuntu on it ... the problem is i install the atheros wifi driver on it and can use wifi ,now i trying to install the kismet  on it can anybudy help in that ,,,,

thanks in advance..:(

---

### Post by Monicker on 2008-05-12
sudo apt-get install kismet.  Then set your sources options in kismet.conf accordingly.

---

### Post by weapon-x on 2008-05-12
> **Monicker said:**
> sudo apt-get install kismet.  Then set your sources options in kismet.conf accordingly.

acc... i have tried this the problem is after that can u tell me hot to config the file of kismet..

---

### Post by Monicker on 2008-05-12
> **weapon-x said:**
> acc... i have tried this the problem is after that can u tell me hot to config the file of kismet..

Show me the results of the following commands, while the wireless is running:
```

ifconfig
iwconfig
```


You should also have a default kismet.conf which is commented and covers the sources and enablesources options.

---

### Post by withnail420 on 2011-02-24
I know this is a three year old thread, but it's the first one I came across whilst googling for this. 
I found the answer anyway. 

In the kismet.conf file, in the sources bit where is says "none,none,addme" change it to "ath5k,wlan0,addme". 

That's only for using atheros chips though. For using RaLink ones it's rt2500 instead of ath5k.

Hope this helps someone.

---


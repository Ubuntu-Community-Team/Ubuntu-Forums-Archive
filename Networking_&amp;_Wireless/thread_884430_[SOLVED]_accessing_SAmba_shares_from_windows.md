---
title: "[SOLVED] accessing SAmba shares from windows?"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2008-08-09
I have already installed samba and I can see my Windows shares on my linux box. However i cant see the linux shares on my windows pc. I havent done any configuring yet. what can i do so that the windows machaine can see the ubuntu machine? Right now, it (the windows machine) doesnt even see that there is another computer on the network

---

### Post by munkyeetr on 2008-08-09
This tutorial got me up and running awhile ago:

[http://www.samba.netfirms.com/](http://www.samba.netfirms.com/)

---

### Post by Iowan on 2008-08-09
I was having the same issue on a testbed server I'd set up at work.  Though probably not your issue, I had misconfigured the **/etc/hosts** file with the *wrong IP address.* Although my server has actual IP address (192.168.X.X), this workstation has:```
127.0.0.1 localhost
127.0.1.1 HOSTNAME.DOMAIN HOSTNAME

```

---


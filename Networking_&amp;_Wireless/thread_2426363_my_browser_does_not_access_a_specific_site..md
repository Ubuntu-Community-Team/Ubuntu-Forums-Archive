---
title: "my browser does not access a specific site."
date: 2019-09-07
forum: Networking &amp; Wireless
---

### Post by espectro2 on 2019-09-07
My browser does not access a specific site.[www.olhardigital.com.br](www.olhardigital.com.br)
i added google dns 8.8.8.8 but the site is not loaded it is not down the site is technology site in my country digital look but my machine does not access what i can do on ubuntu to solve i am having several problems with this version of Ubuntu 18.04.3.

---

### Post by Rubi1200 on 2019-09-08
I am able to access it.

What error messages do you get? Are you using a proxy or VPN service?

What does the ping command show if you use the IP address 187.18.61.152?

---

### Post by espectro2 on 2019-09-09
I'm not using VPN
  ping result is this ping [www.olhardigital.com](www.olhardigital.com)
PING standby-instancia-varnish3.olhardigital.com.br (187.18.61.152) 56 (84) bytes of data.
  In the browser keep trying to connect forever.
do i think i should use VPN? was I invaded? Someone controlling my machine something like that?
thanks for listening

---

### Post by Skaperen on 2019-09-09
I am able to access it, also. both with .br and without.

before you go extreme, like a VPN, let's try to diagnose this, first.

---

### Post by Skaperen on 2019-09-09
in a shell command line terminal do "ping -c 9 www.olhardigital.com.br" and lets see what you get.  if you get ping results, are they for address   200.98.0.72 or 187.18.61.152?

---

### Post by espectro2 on 2019-09-09
ping -c 9 [www.olhardigital.com.br](www.olhardigital.com.br)
PING standby-instancia-varnish3.olhardigital.com.br (187.18.61.152) 56(84) bytes of data.

--- standby-instancia-varnish3.olhardigital.com.br ping statistics ---
9 packets transmitted, 0 received, 100% packet loss, time 8190ms

---


---
title: "PPTPD server loses internet connection when VPN clients are connected"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by awarberg on 2008-04-25
Hi

I installed PPTPD using

$ sudo apt-get install pptpd

Then inserted a line in /etc/ppp/chap-secrets
myuser pptpd mypass *

On my XP box I've created a VPN connection to this server. The connection establishes fine using myuser and mypass, but whenever I'm connected the server has no internet connection ie. I cannot do name lookups *on the server* eg. 
$ ping google.com
will fail.

Obviously this is no good. 

The ubuntu box (7.10) is behind a nat router and receives ip information dynamically from same device (the ip address is reserved per mac-address, however).

Can you guide me in the right direction?

Regards, Andreas

---

### Post by eolatunde4 on 2008-05-05
I had the same problem, however after performing the following steps, the problem was resolved:

> 
After setting VPN connection in XP. I right click on it-->Went to properties--> Networking-->TCP/IP-->Properties-->Advance-->General-->Unchecked use default gateway on remote network 

Hope that helps!

---

### Post by awarberg on 2008-05-06
I tried this setting but the real problem is that the **server** loses its internet access whenever a client connects.

---

### Post by awarberg on 2008-05-09
I've solved this issue, full setup description is here:
[http://www.lockergnome.com/awarberg/2008/05/09/pptpd-setup-for-home-networks/]("http://www.lockergnome.com/awarberg/2008/05/09/pptpd-setup-for-home-networks/")

Andreas

---


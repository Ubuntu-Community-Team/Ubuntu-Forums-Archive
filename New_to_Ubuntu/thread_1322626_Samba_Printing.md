---
title: "Samba Printing"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by TironN on 2009-11-11
So I have a  9.10 server running samba through webmin and I want to set up printing from my Fuji Xerox Phaser 2124 from the windows computer to the server. How would I go about doing this. (I can use SSH if it helps)

Thanks, Fergus

---

### Post by spikyjt on 2009-11-18
The command you need is ```
cupsaddsmb
``` If you view the manual ```
man cupsaddsmb
``` all the info you need is in there. The server guide docs - [https://help.ubuntu.com/9.10/serverguide/C/samba-printserver.html](https://help.ubuntu.com/9.10/serverguide/C/samba-printserver.html) suggest it might be even easier in newer versions (my production servers are still on 8.04LTS) but the stuff in the cupsaddsmb man page worked for me. Hope that helps.

---


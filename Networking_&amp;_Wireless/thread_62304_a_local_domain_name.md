---
title: "a local domain name"
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by dJnEvS on 2005-09-04
not sure if i need to post this here.

I'd like to have a local domain name
so the that the other computers in my network can go to
[www.mysite.com(example](www.mysite.com(example)) and link it to my computer(apache server)
is this possable? if so, how?

---

### Post by dJnEvS on 2005-09-04
bump

---

### Post by s_p_a_r_k_y on 2005-09-04
question, are the other computers WIndows or Linux? You could edit everyone's host files
/etc/hosts (linux)
and 
c:\WINDOWSDIR\system32\drivers\etc\hosts
 (replace windowsdir with c:\windows or c:\winnt)

and add an entry on each PC. Or if you have a DNS server you could add an entry. If all the machines are Windows and just your linux box you could do networking over netbios and then they could type in [http://yourLinuxBoxensSambaName](http://yourLinuxBoxensSambaName)

---

### Post by dJnEvS on 2005-09-04
that is possable indeed,
but then i have to to that on all computers..
is there a way to insert it on one comp. and it works with others as well?

---

### Post by dJnEvS on 2005-09-05
[QUOTE=dJnEvS]bump[/QUOTE]
 ...

---

### Post by s_p_a_r_k_y on 2005-09-05
if you have a DNS server for your companies domain you could do this. You would enter in your local IP address under something like local.yourcompany.com

---


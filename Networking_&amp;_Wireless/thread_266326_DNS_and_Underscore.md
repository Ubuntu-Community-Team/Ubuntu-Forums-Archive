---
title: "DNS and Underscore"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by miobio on 2006-09-27
Hello everybody


I'm trying to access a website of this form _foo.bar.com (note the underscore).

I know that's out of standards and I've already written to the administrator of that website to tell him to change the address.

Anyway, if I try to access it form Mac OSx it works :-S

I did a man resolv.conf and TADAAA

no-check-names
                     sets  RES_NOCHECKNAME in _res.options, which disables the
                     modern BIND checking of  incoming  host  names  and  mail
                     names for invalid characters such as underscore (_), non-
                     ASCII, or control characters.


So i added "options no-check-names" into my /etc/resolv.conf but it still doesn't work :-( ](*,) 


Any suggestions??? HEEEELP!!!

Thanks

---

### Post by mips on 2006-09-27
Dunno, all I know is that using _ is a big no-no.

---

### Post by miobio on 2006-09-28
The real website is _iskra.ilcannocchiale.it  if this can help :-S

---


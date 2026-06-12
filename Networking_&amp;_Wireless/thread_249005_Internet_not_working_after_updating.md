---
title: "Internet not working after updating"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by ofer_w on 2006-09-01
After updating the system the internet connection is not working

using adsl connection and modem

also trying sudo pppoeconf and running the wizard but still not working

any ideas?

thanks

---

### Post by Jad on 2006-09-02
Ofer, 
I use the modem console to connect to the Internet so it's always on and it's much better than using a PPPOE applications.

---

### Post by ofer_w on 2006-09-02
where is the modem comsole?

---

### Post by drtvasudevan on 2006-09-02
it is a bug
you need to repair it by resetting going here.
system>admin>networking

---

### Post by ofer_w on 2006-09-03
what solved my problem is adding the dsn of the internet provider
and doing the pppoeconf wizard again

now the internet is working but after restarting all the information is erased

so how do it is possible to save this for good and that the internet will start during boot?

thanks

---

### Post by drtvasudevan on 2006-09-03
> **ofer_w said:**
> what solved my problem is adding the dsn of the internet provider
and doing the pppoeconf wizard again

now the internet is working but after restarting all the information is erased

so how do it is possible to save this for good and that the internet will start during boot?

thanks

that is the bug.
the changes are not retained.
try to manually edit the interfaces file.

i manupulated so much i dont remember what really fixed the problem.
:confused: 
sorry.
open terminal 
 ```
gksu gedit /etc/network/interfaces
```
dont worry about error messages.
add to the file if not present:
dns-nameservers xx.xx.xx.xx
xx etc being the dns you mentioned.

---

### Post by ofer_w on 2006-09-04
> **drtvasudevan said:**
> that is the bug.
the changes are not retained.
try to manually edit the interfaces file.

i manupulated so much i dont remember what really fixed the problem.
:confused: 
sorry.
open terminal 
 ```
gksu gedit /etc/network/interfaces
```
dont worry about error messages.
add to the file if not present:
dns-nameservers xx.xx.xx.xx
xx etc being the dns you mentioned.

Thanks 

You wrote
dns-nameservers xx.xx.xx.xx
but there are 2 dns numbers 
so to write dns-nameservers xx.xx.xx.xx xx.xx.xx.xx 

?

---

### Post by drtvasudevan on 2006-09-04
one below the other i guess. or leave it with just one to try.
dns-nameservers xx.xx.xx.xx

---


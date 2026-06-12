---
title: "using X-server in virtualbox, with ssh with ubuntu"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by M_agj on 2010-03-03
Hi,
 
I´m using Ubuntu 9.10 32b in Sun Virtual Box installed over windows 7 32b. Everything is just fine. 
 
i´ve a remote computer (workstation) with ubuntu 64b which i remotely access just fine with ssh, including running programs such as matlab64 bits, on my laptop with ubuntu 9.10 as main OS.
 
How can i use the virtual box Ubuntu to run programs remotely? 
The error is "cannot connect x-server".
 
Thanks in advance.

---

### Post by spiderbatdad on 2010-03-03
not sure I can be of any help, but the error suggests you did not use the ssh -X option. If you had I would have expected something like cannot export display.

---

### Post by M_agj on 2010-03-03
thanks for answering. You´re completely right. 
Now i see this is the right forum for me :)

---


---
title: "updating problem"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by bindu arya on 2009-09-24
After updating i got this message
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.10-0ubuntu1~hardy1.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.10-0ubuntu1~hardy1.2_all.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.10-0ubuntu1~hardy1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.10-0ubuntu1~hardy1.2_i386.deb)
  404 Not Found

What is this?can anybody tell me?

---

### Post by mustafa-linux on 2009-09-24
in the terminal run:
apt-get update
then try to upgrade again.

---

### Post by rreese6 on 2009-09-24
IF that doesn't work check your Internet connection.

---

### Post by superprash2003 on 2009-09-24
or try selecting a different server under software sources

---


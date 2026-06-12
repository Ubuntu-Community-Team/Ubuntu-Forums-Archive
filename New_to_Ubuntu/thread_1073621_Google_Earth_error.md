---
title: "Google Earth error"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by aagavin on 2009-02-18
I installed google earth and when i run it it gives me this error:

> Warning: Unable to create prefs directory '/home/aaron/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

how do i fix it

---

### Post by binbash on 2009-02-18
go to the directory where google earth is installed then move libcrypto.so.0.9.8  to anyname you want.Example : 

cd google-earth
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.backup

---

### Post by aagavin on 2009-02-18
K I tried that and now it loads but its closes as soon as it loads???

---

### Post by aagavin on 2009-02-18
never minde it works

---


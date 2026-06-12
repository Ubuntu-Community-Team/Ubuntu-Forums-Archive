---
title: "Google Earth 5.0 in Ubuntu 8.04"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by yolsl on 2009-02-07
owner@owner:~$ googleearth

./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

I've been through pages of installation "guides" I don't really need another explanation on how to download/setup Google Earth I'd just appreciate it if someone could tell me what the above error message means...

---

### Post by Prometheus28 on 2009-02-07
i found the souttion yesterday

There's a workaround that seems to work for me. Just rename/delete the libcrypto that ships with Google Earth and create a symlink to the one installed in the system.

~/google-earth$ ln -s /usr/lib/libcrypto.so libcrypto.so.0.9.8






[http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en)

---


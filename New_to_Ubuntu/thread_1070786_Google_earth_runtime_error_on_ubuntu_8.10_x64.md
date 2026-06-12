---
title: "Google earth runtime error on ubuntu 8.10 x64"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by rogasgr on 2009-02-15
after i installed it like i read on forums like using
chmod -x GoogleEarthLinux.bin
sh ./GoogleEarthLinux.bin

i run it through gnome or terminal but it starts and after 1sec it shuts down. no message on gnome, nothing, only via terminal i get this error msg.





```
rogas@rogas-desktop:~/google-earth$ ./googleearth
Warning: Unable to create prefs directory '/home/rogas/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
```



help pls! :guitar:

---

### Post by indeterminate on 2009-02-15
Check this out: [https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/257464](https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/257464)

Sounds like if you delete the libcrypto.so.0.9.8 in your Google Earth folder, it'll probably work again.

---

### Post by rogasgr on 2009-02-25
thx mate it works fine  :guitar:

---


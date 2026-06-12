---
title: "Google earth problem"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by jmtjet on 2009-02-21
After downloading and installing Google Earth it will not start or crashes after a few seconds. I'm getting this error:

Warning: Unable to create prefs directory '/home/jeff/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

I haven't a clue as to how to fix this. Any help will be greatly appreciated.

Ubuntu 8.04. Thanks.

---

### Post by x33a on 2009-02-21
take a look here:

[http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/](http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/)

---

### Post by jmtjet on 2009-02-22
Thanks for your reply. Google earth seemed to be screwing up other things(cube)so I uninstalled it. Maybe it will be better in the future.

---

### Post by x33a on 2009-02-22
yes, it has problems with compiz. but, the future you are waiting for may not come too soon :D.

---

### Post by binbash on 2009-02-22
rename this file libcrypto.so.0.9.8  to anything you want.

---

### Post by mhbell on 2009-02-22
> **binbash said:**
> rename this file libcrypto.so.0.9.8  to anything you want.
Thank you very much for the info. I have been searching for a solution and even installed 3 different versions of Google Earth. I am using Super Ubuntu 8.11 and everytime I clicked on or typed googleearth, it would start up and then disappear. Your solution worked.
Thanks again.
Mel
:D

---


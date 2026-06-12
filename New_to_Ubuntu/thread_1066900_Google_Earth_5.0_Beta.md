---
title: "Google Earth 5.0 Beta"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-02-11
I installed Google Earth 5.0 beta from a .bin file, which I learned how to do from: [http://justbored.wordpress.com/2008/01/05/how-to-install-a-bin-file-linuxubuntu/](http://justbored.wordpress.com/2008/01/05/how-to-install-a-bin-file-linuxubuntu/)

It installed, but when I click the Google Earth icon it briefly shows the start up tip window and the app window, but immediately closes.

Is this a problem with the beta? How do I fix this otherwise? 

I did ctrl + alt + backspace (restart X?), but that did not resolve the problem.

---

### Post by Lazy-buntu on 2009-02-11
Terminal is giving me this:

Warning: Unable to create prefs directory '/root/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

---

### Post by rburkartjo on 2009-02-11
lazy, good luck hope someone can advise you how to fix. i usually avoid betas i have pouched my system more than once trying them/cheesemaker

---

### Post by binbash on 2009-02-11
you have to rename a file to get it working (i don't remember the name but there were a lot of threads about this)

---

### Post by AllRadioisDead on 2009-02-11
Rename the libcrypto.so.0.9.8 in the google-earth install dir to something else, so the libcrypto installed on the system is used.
[http://ubuntuforums.org/showpost.php?p=6663902&postcount=2](http://ubuntuforums.org/showpost.php?p=6663902&postcount=2)

---

### Post by Lazy-buntu on 2009-02-11
"Rename the libcrypto.so.0.9.8 in the google-earth install dir to something else, so the libcrypto installed on the system is used."

This worked, thank you!

Reminder to self: search forums before posting :lolflag:

---

### Post by raywood on 2009-05-08
Worked for me too.  Thanks!

---


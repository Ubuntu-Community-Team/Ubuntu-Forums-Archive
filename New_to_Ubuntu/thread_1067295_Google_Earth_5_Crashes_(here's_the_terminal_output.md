---
title: "Google Earth 5 Crashes (here's the terminal output)"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by diablo75 on 2009-02-11
Just downloaded the latest version of Google Earth.  I recently did a fresh install of Ubuntu and have not yet re-installed Google Earth until today.  Right when the viewing window appears, the program crashes.  When I run it in terminal, the following is displayed (username altered):

```
user@user-desktop:~$ google-earth/googleearth
Warning: Unable to create prefs directory '/home/user/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
user@user-desktop:~$ 

```

Not sure what to make of this.  Anyone know what's wrong??

(Just to note, I tried the above command using sudo and it still crashed).

---

### Post by SentientFluid on 2009-02-11
> **diablo75 said:**
> Just downloaded the latest version of Google Earth.  I recently did a fresh install of Ubuntu and have not yet re-installed Google Earth until today.  Right when the viewing window appears, the program crashes.  When I run it in terminal, the following is displayed (username altered):

```
**Warning: Unable to create prefs directory '/home/user/.googleearth'. File exists.**
```

The part I bolded above may be the cause.  Try renaming /home/user/.googleearth to something like /home/user/.googleearthOLD and then running it to see what happens.

```
mv /home/user/.googleearth /home/user/.googleearthOLD
```

---

### Post by diablo75 on 2009-02-12
Tried what you suggested twice, and it still fails.  This is the error output in terminal:

```
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

```

---

### Post by Snowjack1 on 2009-02-23
I was getting the same error and found a fix here:

[http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/](http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/)

---

### Post by binbash on 2009-02-23
go to google earth folder and rename this file to any name you want : 

libcrypto.so.0.9.8

---


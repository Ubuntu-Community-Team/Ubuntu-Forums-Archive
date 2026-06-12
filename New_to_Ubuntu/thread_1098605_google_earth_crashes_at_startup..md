---
title: "google earth crashes at startup."
date: 2009-03-17
forum: New to Ubuntu
---

### Post by steve101101 on 2009-03-17
i installed the program as the instructions stated on this website ([https://help.ubuntu.com/community/GoogleEarth#Installation]("https://help.ubuntu.com/community/GoogleEarth#Installation")) and all seemed well. but when the program is opening it crashes. Here is the code from the terminal. 

```

steven@ubuntu:~/Desktop$ googleearth 
Warning: Unable to create prefs directory '/root/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
steven@ubuntu:~/Desktop$ 

```

whats the problem?

---

### Post by gandaran on 2009-03-17
> steven@ubuntu:~/Desktop$ googleearth 
do you need to run GE from desktop directory?
how about just typing googleearth

---

### Post by steve101101 on 2009-03-17
same thing. still crashes.

---

### Post by gandaran on 2009-03-17
try running root
**sudo googleearth**
what happens?

---

### Post by marcelofontenele on 2009-03-17
Hi 

Try this in terminal:

sudo su -
cd /usr/local/googleearth
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak

This dir usr/local/googleearth can be replaced for /opt/googleearth or /home/opt/googleearth, depending of your installation version.

Bye,

Marcelo

---

### Post by tikey on 2009-03-17
I had the same problem but it looks like your suggestion solved it.
The rest of my monitor (everything but the googleearth window) gets kind of flickering but that might be due to the problems I have with my ATI graphic card.

Thanks!!!

---

### Post by stchman on 2009-03-17
I had a similar problem with Googleearth starting and then exiting right away.

There was an information screen that initially pops up when you first launch GE.  I had to quickly uncheck the "Show this dialog on startup" and click Close.

If I did that quickly enough all was good.  If not I would have to retry.

You can give that a try.

---

### Post by steve101101 on 2009-03-21
> **marcelofontenele said:**
> Hi 

Try this in terminal:

sudo su -
cd /usr/local/googleearth
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak

This dir usr/local/googleearth can be replaced for /opt/googleearth or /home/opt/googleearth, depending of your installation version.

Bye,

Marcelo

this worked. thanks

---

### Post by binbash on 2009-03-21
[How to fix google earth beta 5]("http://www.ubuntu-inside.me/2009/02/howto-install-google-earth-50-beta-on.html")

---

### Post by trystan.lea on 2009-03-29
This worked for me, thanks! 

I also got the flickering, but it went away when I disabled desktop effects.

---


---
title: "Ubuntu 10.04 Netbook -- Internet Access?"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by JDMR on 2010-06-19
Hello Ubuntu forums,

I have just recently downloaded Ubuntu to my USB drive so I could boot it alongside my Windows OS. I have never used Linux before, and I planned on using Ubuntu to study the Unix code, and play around with the applications and see the difference from Windows. Really, I'd just like to learn a new language with it, as I'm trying to learn Python and Java.

In the Terminal, I have been requesting the sources of some applications, but it can't find access to them because it is not connected to the internet. I'm having trouble setting up the connection, and it tells me I need some new drivers (b43-fwcutter... and something else).

I've been trying to download the drivers on the Windows OS and get them on the USB, but no success. I'm very lost.

Please help, your words are appreciated.
        JDMR

---

### Post by gandaran on 2010-06-19
if you have the possibility of connecting the laptop to ethernet cable internet and update software sources (run sudo apt-get update in terminal) then you can install the broadcom driver from system » administration » hardware drivers.

---


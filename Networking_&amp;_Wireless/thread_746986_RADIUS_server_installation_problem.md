---
title: "RADIUS server installation problem"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by jamess_jack on 2008-04-06
I downloaded the "freeradius-server-2.0.3" ..

When I start to install it by ... 

./Configure command it gives the error as below :

checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Can anybody tell me the solution.

THANKX..

---

### Post by Paris Heng on 2008-04-06
> **jamess_jack said:**
> I downloaded the "freeradius-server-2.0.3" ..

When I start to install it by ... 

./Configure command it gives the error as below :

checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Can anybody tell me the solution.

THANKX..


Possible Problems:
1. ./configure (the letter c is in lowercase)
2. You must set the config file before you install it.

---

### Post by lotacus on 2008-06-23
I had to download a couple packages that were not installed by default with Ubuntu in order to install freeradius, however, now I am at a standstill because upon running radiusd I get an error:

*radiusd: error while loading shared libraries: libfreeradius-radius-2.0.5.so: cannot open shared object file: No such file or directory*

I thought for a second that it needed to be linked, but as the error states, it just doesn't exist, or it's in another location? Any solution to get this fixed?

---

### Post by lotacus on 2008-06-24
I did an update to ubuntu. do this through the update manager or through CLI by running sudo apt-get update

rebooted the PC (or VM in my case)

went back into the main dir where it was extracted to using the console.

then "make clean"

then "./configure"

then "make"

then "sudo make install"

then I tried "sudo radiusd -X" and it seemed to work as normal.

---


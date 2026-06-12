---
title: "sudo radiusd command not  wokring"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by jamess_jack on 2008-04-07
Hi, 

I want to install FREERADIUS server.

As per the INSTALL file I can do the

./configure
make 
make install 

but when I give  ...."sudo radiusd -X" command 
-----------------------------------------------------------------------------------------------------------------------------
radiusd: error while loading shared libraries: libfreeradius-radius-2.0.3.so: cannot open shared object file: No such file or directory
-----------------------------------------------------------------------------------------------------------------------------

What could be the reason ???

Thankx..

---

### Post by lotacus on 2008-06-24
I got this exact error when compiling the newest release.

I am not sure how I solved it. I did only two things. that could have solved it.

I did an  update to ubuntu. do this through the update manager or through CLI by running sudo apt-get update

rebooted the PC (or VM in my case)

went back into the main dir where it was extracted to using the console.

then "make clean"

then "./configure"

then "make"

then "sudo make install"

then I tried "sudo radiusd -X" and it seemed to work as normal.

Did about 8 hours of configuration, just to run it again and have it throw an error about not finding the TLS module! for pete's sake! one would think freeradius would include all needed modules. Guess not..

So good luck ;)

---


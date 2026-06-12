---
title: "Wireshark won't install"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by acidblue on 2007-03-28
Using dapper:
I found a .deb pkg for Wireshark and am tring to install it,  but it 
kicks an error 'dependicies not met libatk1.0-0'
I checked synaptic and libatk1.0-0 is installed in fact i installed dev and dbg versions
as well but i still get this error.
I am trying to replace ethereal since i am told it is old and buggy and should upgrade to Wireshark, but it's next to impossible to get installed in dapper.
its not even in the dapper repositories.

tried compiling from source but got a 'GTK+ not found" error, that too is intsalled
according to synaptic.

AAAARRRRGGG! why is wireshark being so difficult?
please help!

---

### Post by chr3681 on 2007-05-20
use automatix to install it... it will include all dependencies and install it for you without having to go out and download and install from source

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by compiledkernel on 2007-05-21
I do believe that wireshark is in Add/remove, but additionally you could probably just do a 

sudo apt-get install wireshark

---

### Post by Oleg Petrov on 2007-05-21
> **acidblue said:**
> Using dapper:
I found a .deb pkg for Wireshark and am tring to install it,  but it 
kicks an error 'dependicies not met libatk1.0-0'

please help!

Hi,
Which version of libatk do you  actually have? Wireshark requires  libatk1.0-0 (>= 1.12.2). By the way, apt-get did not manage to resolve all the dependencies of wireshark, so I had to 'dpkg' some libraries manually.

---

### Post by cashen on 2007-06-19
I tried the apt-get install for Wireshark and get the error - "E: Couldn't find package Wireshark".  Do I need to add a repository?
Thanks

---

### Post by tturrisi on 2007-06-19
It should be in the repos.  Try enabling the Universe & MultiUnivers repos.  Hell, Debian Etch has wireshark in its repos!

---


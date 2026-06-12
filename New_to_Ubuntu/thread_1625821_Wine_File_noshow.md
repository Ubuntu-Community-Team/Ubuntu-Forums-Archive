---
title: "Wine File noshow"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by nnjond on 2010-11-19
Hi,

I want to install kindle in kubuntu.

I seem to have sucssefully installed wine and and added ms explorer.exe. but when I click on Browse C drive...

Unable to run the command specified. The file or folder file:////Documents/.wine/dosdevices/c: does not exist.

And it isn't there? 

Can you advise me on my next move?

Thanks for your time.

---

### Post by wishyjr on 2010-11-20
hmm i think that the .wine directory can be found in the home directory, maybe try looking in:

/home/nameofuser/.wine/dosdevices/c:/


maybe that might help?

Also, in winefile, the native (ubuntu) filesystem is mounted as drive z: under wine. not sure if that might help.

---


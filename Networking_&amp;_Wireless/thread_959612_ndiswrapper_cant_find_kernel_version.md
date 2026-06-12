---
title: "ndiswrapper cant find kernel version"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by NoSmokingBandit on 2008-10-26
Im trying to install ndiswrapper from source and i get this error:

steven@ubuntu:~/ndiswrapper/nd$ make distclean
make -C driver clean
make[1]: Entering directory `/home/steven/ndiswrapper/nd/driver'
Makefile:34: *** Cannot find kernel version in /lib/modules/2.6.24-21-386/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/steven/ndiswrapper/nd/driver'
make: *** [clean] Error 2


Whats the deal with that?

I installed the mini-cd then added kde. My wireless doesnt work (unsurprisingly) so i kinda need ndiswrapper. What to do>?

---

### Post by cariboo on 2008-10-26
Why install ndiswrapper form source, when the debs are on the LiveCD, just make sure the cd is enabled in System-->Administration-->Software Sources, then search for ndiswrapper in System-->Administration-->Synaptic Package Manager. Make sure you isntall ndisgtk as it is a gui tool to help install ndiswrapper.

Jim

---

### Post by NoSmokingBandit on 2008-10-26
i had it installed via synaptic, but every driver i loaded into it had an error. It said they were an "invalid driver" or something. I read somewhere that installing it from source makes it work better. Ill try it again in synaptic and let you know what happens.

edit:
I tried reinstalling via synaptic but every driver i try to install is "invalid"
hmmmm

---


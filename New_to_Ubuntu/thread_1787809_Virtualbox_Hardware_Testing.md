---
title: "Virtualbox Hardware Testing"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by Redblade20XX on 2011-06-21
Hey everyone,

My computer came with a wifi card that wasn't supported by kernel 2.6.38 on Ubuntu 10.10 but there was a patch that enabled it. I want to test newer kernels on the hardware and would like to know if I can use virtualbox to do a fresh install (within the patched os) to test whether or not newer kernels resolved the bugs I've had with the hardware such as wifi? 

Thanks for any responses! :)

-Red

---

### Post by Redblade20XX on 2011-06-22
Any1 ever tried this??

---

### Post by ixtok on 2011-06-22
I use virtualbox and I believe that the guest operating system thinks it is using a wired network connection, connecting to the internet through the already set up network of the host system. So you would not be able to test different kernals this way. All my virtualbox guest systems show a wired connection when in operation even though the host is using a wifii connecton.

---

### Post by crispy_420 on 2011-06-22
The physical hardware can not be tested in that manner since it is not seen. Either you have a connection or don't, VirtualBox sees it all as the same.

---

### Post by Redblade20XX on 2011-06-22
Oh, okay guys!!! Thanks for the help. Thread Closed!! :p

- Red

---


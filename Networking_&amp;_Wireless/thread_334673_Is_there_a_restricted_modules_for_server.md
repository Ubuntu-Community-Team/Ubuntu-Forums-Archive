---
title: "Is there a restricted modules for server?"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by Sunnz on 2007-01-09
Hi, I have installed the server edition of Ubuntu.

I need to get madwifi working, which is in the restricted modules... I tried to install the 2.6-*-386 modules, but the default kernel is Ubuntu Server is 2.6-*-server... so it didn't work.

I have to use 2.6-*-386 kernel now. But if there is a restricted modules for server, that would be great!

Thanks.

---

### Post by az on 2007-01-09
There is no restricted modules package for the server kernel.  Perhaps, install build-essential and the linux-headers-server packages, get the madwifi source and compile it from source.

Depending on your needs, you can just stick with the generic kernel.  Unless you are running a high-performance server, you probably won't see that much difference between the two kernels anyway.

---

### Post by Sunnz on 2007-01-09
I see...

I might compile it from source, just for the sake of learning how things worked...

Does anyone know which version of madwifi was compiled in the restricted modules? (madwifi-ng of just madwifi?)

---


---
title: "help - cant detect wirless and getting error installing ndiswrapper"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by greenw40 on 2008-07-02
Ive tried connecting to my wireless network but it cant detect anything. I have Ubuntu 8.10 and I can connect to the internet directly through my router (with a cable). Ive tried a lot of things people suggest on the discussion boards. This is what i've done most reciently which is usually how it goes:
 1 Download ndiswrapper
 2 make distclean
 3 make
 4 make install

then i get this: make[2]: *** [_module_/home/chris/ndiswrapper/ndiswrapper-1.48/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/chris/ndiswrapper/ndiswrapper-1.48/driver'
make: *** [install] Error 2

By the way, I have a laptop with a Realtek 8185 a/b/g wireless adapter.

Any help would be greatly appreciated.

Thanks

---


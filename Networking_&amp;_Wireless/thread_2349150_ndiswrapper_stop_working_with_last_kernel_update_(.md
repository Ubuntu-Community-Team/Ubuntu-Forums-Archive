---
title: "ndiswrapper stop working with last kernel update (14.04)"
date: 2017-01-11
forum: Networking &amp; Wireless
---

### Post by intheopen on 2017-01-11
Hello guys, someone else have problems in ndiswrapper since the last kernel update in ubuntu14.04? I'm using xubuntu but I suppose that it's the same.

ndiswrapper(1.61) stopped working today, and it was working flawlessly since today, I've tried to compile many versions but I can't, and I compiled the version that I was using since today 2 weeks ago without problem and nothing has been changed since then, just the normal updates from ubuntu.

Thanks!

---

### Post by praseodym on 2017-01-12
Please check:
```

sudo dkms autoinstall
dkms status
```

---

### Post by intheopen on 2017-01-13
Thanks for your help,

I removed ndiswrapper yesterday when trying different versions, so I can't give you the status because I can't install it again, here is the message that 'make install' gives.

```

albert@cova:~/sources/ndiswrapper/ndiswrapper-1.61$ sudo make install 
make -C driver install
make[1]: se ingresa al directorio «/home/albert/sources/ndiswrapper/ndiswrapper-1.61/driver»
ndiswrapper.ko is not for Linux 4.4.0-59-generic
make[1]: *** [install] Error 1
make[1]: se sale del directorio «/home/albert/sources/ndiswrapper/ndiswrapper-1.61/driver»
make: *** [install] Error 2

```

---


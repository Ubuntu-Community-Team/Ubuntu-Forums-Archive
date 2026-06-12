---
title: "Downgrading my C compiler"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by chandin69 on 2011-04-04
Im trying to install NS2.30 and apparently it only works properly with gcc3.4 so I need to downgrade the existing verison in my ubuntu 10.10

The follwing instructions are for fedora. How do i do the same thing in ubuntu?

```
yum install \
gcc-c++ compat-gcc-34-c++ automake autoconf libtool libX11-devel \
libXext-devel libXau-devel libXmu-devel xorg-x11-proto-devel

```

---

### Post by gmargo on 2011-04-04
Why so old a version of the Network Simulator? (Assuming that's what you're talking about.)

I downloaded ns-allinone-2.34.tar.gz from [http://sourceforge.net/projects/nsnam/](http://sourceforge.net/projects/nsnam/), and it compiles just fine under 10.10 Maverick. (Optional xgraph needs a patch though.)

---


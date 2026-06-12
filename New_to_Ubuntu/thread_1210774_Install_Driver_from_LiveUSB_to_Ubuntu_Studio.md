---
title: "Install Driver from LiveUSB to Ubuntu Studio"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Jolzath on 2009-07-11
Hello, I have Ubuntu Studio x64 (Jaunty) and a Belkin Wireless G Dongle. Ubuntu Studio does not know to connect to the internet with it, but a standard Ubuntu x64 LiveUSB (Jaunty) can detect and use my Dongle, Might I inquire as to how do I get that driver to install over to my Ubuntu Studio install?

---

### Post by nhasian on 2009-07-11
i havent tried studio yet but i thought they were identical except for including extra multimedia packages?  anyhoo, i recommend going to System->Administration->Software Sources and clicking the updates tab.  in there tick the box marked "Unsupported Updates backports"

then see if there are any new restricted hardware drivers in system->administration->hardware drivers

if all else fails you can use the ndiswrapper

---

### Post by Jolzath on 2009-07-11
> **nhasian said:**
> i havent tried studio yet but i thought they were identical except for including extra multimedia packages?  anyhoo, i recommend going to System->Administration->Software Sources and clicking the updates tab.  in there tick the box marked "Unsupported Updates backports"

then see if there are any new restricted hardware drivers in system->administration->hardware drivers

if all else fails you can use the ndiswrapper

It isn't propriatary

---


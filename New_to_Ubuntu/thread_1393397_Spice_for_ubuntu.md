---
title: "Spice for ubuntu"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by fendy87 on 2010-01-29
i want run my netlist..i only know quartus software but that software can't run in ubuntu..i want to know,ubuntu got compatible software to run netlist?..im new in ubuntu..(-.-)

---

### Post by audiomick on 2010-01-29
If you go to the synaptic package manager in system> administration
and search "netlist" you should find a package called geda-gnetlist

The description is
> GPL EDA, an electronics design package, including
 gschem, a schematic editor.

This package contains the netlist generator, gnetlist.

does that sound useful?

---

### Post by fendy87 on 2010-01-29
thx..:-)..very useful...

---

### Post by fendy87 on 2010-01-29
go to the synaptic package manager in system> administration
and search "netlist" you should find a package called geda-gnetlist


i done installation but not appear in my applications?y?

---

### Post by audiomick on 2010-01-29
> **fendy87 said:**
> go to the synaptic package manager in system> administration
and search "netlist" you should find a package called geda-gnetlist


i done installation but not appear in my applications?y?

wait. I will install it and have a look.

---

### Post by audiomick on 2010-01-29
Got it. The package is part of something bigger.
go back to synaptic and search "geda"

There is a meta-package called "geda" that looks like it pulls in everything you need.

Description:
> GPL EDA, an electronics design package.

This is a metapackage which depends on the components required
for a typical gEDA installation.

Installed that, and now I have an "electronics" entry in my applications menu.

There is a Wikipedia page
[http://en.wikipedia.org/wiki/Geda](http://en.wikipedia.org/wiki/Geda)

---

### Post by fendy87 on 2010-01-29
done installation..thx Michael..the application is under electronics....now i can do my assignment..hehe..thx again

---

### Post by audiomick on 2010-01-29
You are welcome. Have fun with it.

---


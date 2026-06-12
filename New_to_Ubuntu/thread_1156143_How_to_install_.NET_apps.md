---
title: "How to install .NET apps?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by rams123 on 2009-05-11
I wanna install one .NET apps in Ubuntu and I'd heard Mono can do that.

Can anyone pls give tell how to do that?

---

### Post by alexandari on 2009-05-11
[http://ubuntuexperiment.wordpress.com/2009/01/29/running-aspnet-applications-in-ubuntu-using-modmono/](http://ubuntuexperiment.wordpress.com/2009/01/29/running-aspnet-applications-in-ubuntu-using-modmono/)

I think this can help.

---

### Post by directhex on 2009-05-11
Just copy all the assemblies to someplace smart, and try running "mono foo.exe"

If you get an assembly not found error, then install the missing assembly (use apt-get file search System.foo.dll to find the package to install if it says System.foo is missing, work from there)

---


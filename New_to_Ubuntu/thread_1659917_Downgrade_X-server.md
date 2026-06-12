---
title: "Downgrade X-server"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Mombie on 2011-01-04
Hello everyone.

I'm working on a project.

But the touchscreen driver requires a X-server version below 1.5

Is it possible to downgrade 10.10 that low?

I'm currently having to use 8.04 and the only internet access is through a mobile stick which it doesn't want to play nice with.

The 64bit USB driver is the one I will be using.
[http://www.elotouch.com/Support/Downloads/dnld.asp](http://www.elotouch.com/Support/Downloads/dnld.asp)

Thanks for the help
-Brad

---

### Post by khelben1979 on 2011-01-05
I would recommend you not to downgrade the X server. 

If you decide to compile up the whole X server from source code, you might have better luck, though. The biggest reason would be because of the risk of ending up in a lot of dependency package problems and a more buggy and untested system.

---


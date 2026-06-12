---
title: "WeatherReport 2.26.0 Forecast &amp; Radar Map broken?"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Jock McJock on 2009-05-04
Ubuntu 9.04 NEW install.



WeatherReport 2.26.0. Forecast not currently available for this location and Radar Map are these broken ?

  I cannot get the Forecast and Radar Maps working on Weather 2.26.0 is there a fix/patch or are these features not supported in 9.04 anymore?

---

### Post by jerrrys on 2009-05-05
don't use it myself, find it much easer to let firefox or my local .com tv station to tell me whats happening. i did run across this though, if its any help...

[https://bugs.launchpad.net/ubuntu/+source/libgweather/+bug/367291](https://bugs.launchpad.net/ubuntu/+source/libgweather/+bug/367291)

---

### Post by Youresorock on 2009-05-19
It's broken for me as well after my 8.10 -> 9.04 upgrade.

---

### Post by Youresorock on 2009-05-21
I booted from a 9.04 64bit Live CD, and weather worked fine there.  Can someone tell me where the weather app's config files are?  

I'm betting the 8.10 -> 9.04 upgrade kept the old config which is not compatible in some way.

---

### Post by Youresorock on 2009-05-21
Found this thread: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/372647](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/372647)


Looks like for some ppl when you upgrade from 8.10 to 9.04 your proxy settings get hosed mildly.  I went to System->Pref->Network Proxy, and it was enabled, but with no settings.  I selected Direct Connection and saved.  After that my weather updates properly.

---


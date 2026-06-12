---
title: "Installed ubuntu netbook remix on laptop for laughs and can't fully uninstall it"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by samh785 on 2009-11-03
I installed the ubuntu-netbook-remix package in synaptic to see what it looks like when running on a computer (thought it looked quite good btw). After I looked at it for a while, I tried to uninstall it. I uninstalled the package and rebooted the computer. At first all looked normal, but what I have now is a hybrid between the normal ubuntu and the netbook remix. I cannot minimize/maximize firefox or any of the main apps that start out fullscreen in the netbook remix. 

here is a screenshot of firefox:
[[IMG]http://img402.imageshack.us/img402/8710/screenshottd.th.png[/IMG]]("http://img402.imageshack.us/i/screenshottd.png/")

---

### Post by samh785 on 2009-11-03
Got it. The culprit was a package called "maximus"
Removed it by the usual
```
sudo apt-get remove maximus
```

---


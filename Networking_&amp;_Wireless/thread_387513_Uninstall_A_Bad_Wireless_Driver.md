---
title: "Uninstall A Bad Wireless Driver"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by phosphorusdeathcamp on 2007-03-18
How do you uninstall a bad wireless driver. I installed a bad driver and now my wireless card doesnt show up. Im very confused. 

I have a Linksys WMP54G 802.11g wireless adapter
it was recognized before but now its not

---

### Post by gradedcheese on 2007-03-18
what did you install?  are you using ndiswrapper?

---

### Post by gameman12 on 2007-03-18
if you are using ndiswrapper here are the codes

```
ndiswrapper -e <drivername>
```

for the actuall code, replace <drivername> with the name of your driver and don't put it inside these symbols (< >)

---


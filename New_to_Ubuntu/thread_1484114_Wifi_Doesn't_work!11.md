---
title: "Wifi Doesn't work?!?1?1"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by strib on 2010-05-15
I have the 10.04 version of ubuntu and i can't make it connect to my wifi. 

if anyone could help that would be great

thanks
strib

---

### Post by readycarpenter on 2010-05-15
most wireless cards do not have a free open source driver, so it is not bundled with ubuntu, but if you can get online once via ethernet you can run 

system> admin> "hardware drivers"

your wireless card drivers should show there, install and reboot, remember you need to be online as it downloads the drivers from the Internet.

cheers

---

### Post by nhasian on 2010-05-15
can you give us more specific detail about your problem?  Like is your wifi adaptor seen by ubuntu but you are unable to connect to your wifi network?  or is your wifi adaptor not seen at all?  which network adaptor do you have?

```
lshw -C network
```

---


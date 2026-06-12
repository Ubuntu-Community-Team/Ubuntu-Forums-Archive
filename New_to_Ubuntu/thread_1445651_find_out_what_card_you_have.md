---
title: "find out what card you have"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-04-02
how do you find out what graphics card you have ...and the driver....  
and can you use envy or something to see if there is something better or older or newer....??
9.10

---

### Post by warfacegod on 2010-04-02
Open a Terminal and type:

```
sudo lshw
```

That will give you a list of your hardware.

Generally, it is a good idea to use which ever driver is "Recommended" in Jockey (envyng will show you pretty much the same drivers). System> Admin.> Hardware Drivers.

---


---
title: "hardware check?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by TroyStachnik on 2010-02-05
i have a sound card but i am not sure what drivers to download, is there a way in ubuntu 9.10 to see what hardware is installed into the pc?

---

### Post by wojox on 2010-02-05
#List hardware

```
sudo lshw -html > ~/hardware.html
```

---

### Post by switch10 on 2010-02-05
...or you could try a GUI program called sysinfo.  Type this into a terminal:

```
 sudo apt-get install sysinfo 
```

---


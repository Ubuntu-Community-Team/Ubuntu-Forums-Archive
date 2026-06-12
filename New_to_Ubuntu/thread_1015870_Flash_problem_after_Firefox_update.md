---
title: "Flash problem after Firefox update"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Gone fishing on 2008-12-19
This is a why question:

After the last update of Firefox 3 on Intrepid The flashplugin-nonfree stopped working. Firefox would tell me that the plugin needed installing. However if I went to synaptic I could see that it was installed. Anyway I tried complete removal in synaptic then reinstall this did not solve the problem,

However, when I opened a terminal and typed 

```
sudo apt-get purge flashplugin-nonfree
```

followed by

```
sudo apt-get install flashplugin-nonfree
```

everything works why?

Isn't synaptics complete removal the same as apt-get purge? and synaptics install the same as apt-get install?

---

### Post by howefield on 2008-12-19
I reinstalled my system from scratch last night, and flash had the same issue as you had, an update today to flashplugin-nonfree has fixed whatever the issue was.

Maybe it was the updated version you got with your last attempt.

---

### Post by Gone fishing on 2008-12-19
Possible

Synaptic didn't install from on-line just from the cache whilst apt-get installed on-line. I hadn't done a refresh but as update manager was running maybe it was refreshed between running synaptic and apt-get.

Synaptic is just a GUI for apt isn't it?

---

### Post by howefield on 2008-12-19
> **Gone fishing said:**
> Synaptic is just a GUI for apt isn't it?

That's my understanding.

---


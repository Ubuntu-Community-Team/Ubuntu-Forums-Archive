---
title: "Synaptic Package failing to connect sourceforge.net"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by nauman.mustafa on 2011-01-28
Dear,

I am having a weired problem after a new installation of Linux 10.04. None of my software downloading softwares is working. There are giving the following message:

Connecting to voxel.dl.sourceforge.net|208.122.31.29|:80... failed: No route to host.

I am unable to install anything new.

Please help.

---

### Post by mharrison on 2011-01-28
Can you post what your /etc/apt/sources.list  file looks like?

This will bring it up in a text editor so you can copy and paste it.
```
gedit /etc/apt/sources.list
```

---

### Post by peculiar penguin on 2011-01-28
Dunno what "software downloading softwares" is, but they've shut down some servers/services: [http://sourceforge.net/blog/sourceforge-net-attack/](http://sourceforge.net/blog/sourceforge-net-attack/)

---

### Post by nauman.mustafa on 2011-01-28
I have solved it.

There was a respiratory from source forge was missing. Thanks I have added it and now it is running like anything

---


---
title: "Help a noob with a LInksys router?"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by Seamless in Northampton on 2008-08-24
Pardon my ignorance here, but I'm in search of some basic understanding of just exactly what I need to do to get my new wireless setup working--a Linksys router going to one wired and one wireless system, both Ubuntu. I have a reasonable grasp of Ubuntu after running it for several months, but I'm utterly lost about how to get this router working with my wired system. The wireless bit seems clearer (the PCI adapter seems to be installed properly), though it may get muddled fast! 

All the talk of Ndiswrapper and so on seems geared toward adapters, but what I can't get working is the wired connection through the actual router. What do I do? Any points in the right direction would be appreciated.

---

### Post by caljohnsmith on 2008-08-24
To give us a place to start, please post the output of the following commands:
```
sudo lshw -C network
ifconfig
```

---

### Post by Seamless in Northampton on 2008-08-24
OK, thanks! Will do as soon as I'm back at my machine in the morning.

---


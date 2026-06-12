---
title: "Wireless with Dell 1395 wireless mini-card (802.11b/g)"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by levic77 on 2008-08-13
I just bought a Dell- Inspiron T5750 with the Dell 1395 wireless mini-card (802.11b/g)used for wireless connectivity. I downloaded the Wubi 8.04.1 from the Ubuntu site. I am unable to get online. I tried following the online documentation 'Install ndisgtk (System &#8594; Administration &#8594; Synaptic Package Manager).', but when I search for ndisgtk there it does not find it. I have my original drivers disk from when I bought the laptop. Any ideas?  Thanks in advance for any help..

---

### Post by Kralizec on 2008-08-13
I've personally never used ndisGTK, I always use the command line for working with ndiswrapper, which is very simple. Try searching the repositories for ndiswrapper, and install that. Then to work with it on the command line, you can use these commands (as root, since they work in system directories):
```
ndiswrapper -i
``` to install the .inf file for your driver, ```
ndiswrapper -l
``` to see if it finds your device, ```
ndiswrapper -m
``` to create a network device that uses ndiswrapper, and then finally ```
modprobe ndiswrapper
``` to make it active.
If this doesn't work, or you have any questions about these directions, please ask.

---


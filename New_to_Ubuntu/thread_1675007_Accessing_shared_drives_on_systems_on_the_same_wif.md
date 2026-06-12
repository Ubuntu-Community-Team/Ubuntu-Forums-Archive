---
title: "Accessing shared drives on systems on the same wifi network"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by rlowrance on 2011-01-24
My Ubuntu system is on my home wifi work. I get access to the Internet and the system can see network printers.

I'd like to 
(a) access one of disk drives on one of the mac's on the network
(b) allow the mac's to access one of the drives on the Ubuntu system.

On the mac side, I need to turn on file sharing. I access another system's shared drives by selecting in the Finder, Go>Connect to server and browsing the network.

How do I do this in Ubuntu?

Specifically,
1. How to I turn on file sharing?
2. How do I access the shared drives on another system?

Thanks, Roy

---

### Post by rlowrance on 2011-01-24
On the mac side, one needs to turn on file sharing and select the option to enable Windows shares. One should also specify on the mac which users and folders will be shared.

Then in Ubuntu, select Places>Network, and the name of the Mac system will appear and can be selected.

Does anyone know how to tell Ubuntu to share all or a portion of its file system?

- Roy

---

### Post by alphacrucis2 on 2011-01-24
> **rlowrance said:**
> On the mac side, one needs to turn on file sharing and select the option to enable Windows shares. One should also specify on the mac which users and folders will be shared.

Then in Ubuntu, select Places>Network, and the name of the Mac system will appear and can be selected.

Does anyone know how to tell Ubuntu to share all or a portion of its file system?

- Roy

Right click on the required folder in nautilus and select sharing from the context menu.

---


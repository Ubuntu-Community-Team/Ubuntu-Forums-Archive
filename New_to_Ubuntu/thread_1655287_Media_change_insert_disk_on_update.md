---
title: "Media change insert disk on update?"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-12-29
I was adding a PPA and when i did sudo apt-get update command i was asked to insert the ubuntu 10.10 disk then hit enter to continue, it wont let me finish my update without doing this. How do i get rid of this?

---

### Post by drs305 on 2010-12-29
The reason is that your installation CD is listed in the repository sources list. Open Synaptic or Software Sources (System, Administration ... ). Settings > Repositories > Ubuntu Software tab. Untick the lower panel's CD reference. 

If you still get the message, check also for a CD listing in the Third Party tab.

---


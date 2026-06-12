---
title: "How to edit GRUB boot menu?"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by 7mm on 2010-04-04
**Hi there, I've regularly updated Ubuntu 9.10 & now my GRUB boot menu shows more than single choices for Ubuntu. I can see all the previous versions in the menu as well. How can I get rid of them, please suggest. Though, I've never edited bood menu before!**

---

### Post by koma77 on 2010-04-04
Here, take a look at this:

[https://wiki.ubuntu.com/Grub2#Automatic%20Entries]("https://wiki.ubuntu.com/Grub2#Automatic%20Entries")

---

### Post by quinnten83 on 2010-04-04
[http://www.howcast.com/videos/329221-Configuring-Grub-2]("http://www.howcast.com/videos/329221-Configuring-Grub-2")

---

### Post by vallvi on 2010-04-04
The simple GUI way is to install and use the 'Startup-Manager' with which you can define how many options you get at startup.

---

### Post by Elfy on 2010-04-04
All of those change the boot options shown - searching for linux-image in synaptic and marking the old kernels for complete removal will both update the boot menu and remove the old unused kernels.

---


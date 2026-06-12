---
title: "virtual desktop in linux"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Jynxx on 2009-02-09
Hello all. Is there a program for linux which allows us to run windows virtually in linux?

---

### Post by jbrown96 on 2009-02-09
VirtualBox is an fantastic virtualization tool. There is an open-source version available in Synaptic, but the closed-source version has some cool features like seamless mode USB pass-through. You can get the newest ones from [here]("http://virtualbox.org") Once you install the .deb package. You need to add yourself to the vboxusers group. Run ```
sudo usermod -aG vboxusers $USER
``` Then restart. The virtual machine manager is available in Apps--->System Tools. Make sure to install the guest additions; it makes all the difference.

---

### Post by Jynxx on 2009-02-09
wow, thank you! That's the coolest thing I've seen since sliced bread! lol

---


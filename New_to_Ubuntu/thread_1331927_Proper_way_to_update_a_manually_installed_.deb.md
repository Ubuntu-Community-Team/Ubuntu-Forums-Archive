---
title: "Proper way to update a manually installed .deb?"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by klemperal on 2009-11-19
I have always updated manually installed .debs (like virtualbox) by first removing the old version through synaptic or the terminal, and then installing the newer .deb.  Just now however, I accidentally installed the latest version of virtualbox without having first removed the old version...and it works just fine.  My question  is, is it necessary or even a good idea to first remove old .deb files before installing newer versions of that same program?

---

### Post by Cheesemill on 2009-11-19
I know I'm not really answering your question but if you add the VirtualBox repository to /etc/apt/sources.list then it will update itself along with the rest of the system everytime you check for updates (either through Update Manager or apt-get upgrade).

Repository details can be found on this page after the download links: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by jorgecarrillo150990 on 2009-11-19
I think the deb files overwrite themeselves, so there is no reason to uninstall then install :)

---

### Post by klemperal on 2009-11-19
> **jorgecarrillo150990 said:**
> I think the deb files overwrite themeselves, so there is no reason to uninstall then install :)

Thanks for the reply.  I had been removing, then installing debs for so long that I never stopped to question if it was necessary.  Truly we are creatures of habit--thanks again for the response.

---


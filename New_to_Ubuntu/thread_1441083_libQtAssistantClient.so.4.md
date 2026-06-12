---
title: "libQtAssistantClient.so.4"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by smillion on 2010-03-28
Just built a computer and installed Ubuntu 9.10 64-bit. I need to use a software and I received this message:

error while loading shared libraries: libQtAssistantClient.so.4: cannot open shared object file: no such file or directory.

I'm assuming it means I need to get libqt-dev or something. Am I right?
So I looked in Synaptics and it wasn't in there. Do I have to be connected to the net to download it then?

---

### Post by gmargo on 2010-03-28
Install the **libqt4-assistant** package.

---

### Post by smillion on 2010-03-29
> **gmargo said:**
> Install the **libqt4-assistant** package.

the libqt4-assistant package isn't in the synaptics. So I'm assuming i need to reload and download it.

---

### Post by Perfect Storm on 2010-03-29
libqt4-assistant is available from kubuntus PPA; 

ppa:kubuntu-ppa/backports

---

### Post by smillion on 2010-03-29
> **Artificial Intelligence said:**
> libqt4-assistant is available from kubuntus PPA; 

ppa:kubuntu-ppa/backports

Thanks AI but I might first consider getting my wireless to work before I download this.

---

### Post by gmargo on 2010-03-29
> **smillion said:**
> the libqt4-assistant package isn't in the synaptics. So I'm assuming i need to reload and download it.

The **libqt4-assistant** package is in the main repository for 9.10 Karmic. You should see it in the Synaptics tool.  However, if you've just installed, perhaps your system is configured to only load packages from the cdrom?  Check your System Sources under the Synaptics menu Settings -> Repositories.  Make sure that the "Downloadable from the Internet" section has the "main" section checked.  Or just hit the Reload button?

> Thanks AI but I might first consider getting my wireless to work before I  download this.Oh, just saw this... Yes you'll certainly need a network connection working first.

[http://packages.ubuntu.com/karmic/libqt4-assistant](http://packages.ubuntu.com/karmic/libqt4-assistant)

---


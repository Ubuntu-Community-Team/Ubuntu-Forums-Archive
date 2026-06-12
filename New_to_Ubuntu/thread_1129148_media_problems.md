---
title: "media problems"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by thesuperjman on 2009-04-18
im having problems with streamed media online with simple things like youtube, and music players, etc. i've installed flash player and the restricted extras. ive also ran medibuntu but nothing works still. what is my problem and how can i fix it?

edit, also, if it helps, im running ubuntu 8.10 32 bit.

---

### Post by hovzio on 2009-04-18
Have you tried manually installing the flashplugin that adobe provides at their site, I've had to do this as a last resort, download the .tar file. Download and follow the instructions on the site:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

I would first remove any prior flash installs. You do not have to install this .tar download as root, you can also do it on a per user basis.

---

### Post by thesuperjman on 2009-04-18
i tried this and it opened it as read only....?

---

### Post by hovzio on 2009-04-18
you need to make the file executable before you can install it,

cd /to/2/dirctory/containing_flashinstaller

chmod 750 "flash_installer"

DO not copy and paste but replace "flash_installer" with the actual name of the installer. Chmod 750 will give it read, write and execute permisions for the owner, and read/write perms for the group.

---

### Post by thesuperjman on 2009-04-21
so what's my installer?

---

### Post by thesuperjman on 2009-04-21
it's still not working, can anyone help me? i'm tired of these problems.

---

### Post by thesuperjman on 2009-04-23
bump

---


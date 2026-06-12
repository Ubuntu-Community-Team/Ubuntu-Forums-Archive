---
title: "MTP mounting"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Commander_Bob on 2010-02-05
I am developing for the [Zii Egg]("http://www.ziilabs.com/") and it uses MTP. Everytime I plug it in I have to unmount it and issue ```
sudo mtpfs ~/egg -o allow_other
``` to mount it properly and ```
sudo fusermount -u ~/egg
``` to unmount it. Is there a way to automate this? It is a real pain.

---


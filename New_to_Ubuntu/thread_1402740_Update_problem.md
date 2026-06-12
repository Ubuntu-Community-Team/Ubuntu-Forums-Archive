---
title: "Update problem"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by lizdoesn'tknowanything on 2010-02-09
I'm having some issues with my update thingy. It has been telling me I need to install updates but when I click on it and it asks me for my password it doesn't do anything. Then, when I click check for updates it gives me this message:

Failed to fetch [http://archive.getdeb.net/ubuntu/dists/hardy-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/hardy-getdeb/apps/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead. 

So, what do I do about this?

---

### Post by snowpine on 2010-02-09
Hi Liz, getdeb.net is not part of the software sources for a default Ubuntu install. Please explain why you added this 3rd-party repository to your software sources so that we can better assist you. You might also find some answers at the getdeb.net website. Good luck! :)

---

### Post by lizdoesn'tknowanything on 2010-02-09
I believe I added it while trying to get Cmap Tools to work on Linux, which I was eventually able to do. I'm not so sure that was what caused it to work but someone suggested I use it.

---

### Post by snowpine on 2010-02-09
Try unchecking the getdeb repository in System->Administration->Software Sources, then doing your update again. I tried clicking the link and it is broken. (Maybe Getdeb doesn't support 8.04 any more? I just don't know...)

---

### Post by halitech on 2010-02-09
looking here ( [http://archive.getdeb.net/ubuntu/dists/](http://archive.getdeb.net/ubuntu/dists/) ) they are only supporting Juanty and Karmic now

---

### Post by lizdoesn'tknowanything on 2010-02-09
Thanks

---


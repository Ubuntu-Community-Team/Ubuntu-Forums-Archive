---
title: "How to resume a WGET download? -c will not work."
date: 2009-08-04
forum: New to Ubuntu
---

### Post by harry71194 on 2009-08-04
Okay, I am trying to download Sauerbraten for my Ubuntu. The download keeps timing out, so I thought I would try wget.

wget -r -np -c -U "Mozilla/5.0 (X11; U; Linux i686; nl; rv:1.7.3) Gecko/20040916" -e robots=off [http://voxel.dl.sourceforge.net/project/sauerbraten/sauerbraten/2009_05_04/sauerbraten_2009_05_04_trooper_edition_linux.tar.bz2](http://voxel.dl.sourceforge.net/project/sauerbraten/sauerbraten/2009_05_04/sauerbraten_2009_05_04_trooper_edition_linux.tar.bz2)

Now, that command SHOULD work, right? Wrong. When the download times out, it starts me again at 0 Bytes. :( Obviously the server is telling my client the HTTP response 200, which is making the download start from 0, not 206 - Partial content.

"HTTP request sent, awaiting response... 200 OK"


*So, help, how do I FORCE wget to resume the download, regardless of the HTTP code the server sends?* Or is it impossible? The download keeps timing out at ~1%, so then it forces me to start at 0%. My Internet fails, but wget -c'ing stuff normally works, like for YouTube videos.


Thanks in advance.

---

### Post by Clorow on 2009-08-04
I really have no idea, as I mostly use curl instead of wget. Although, you can install Sauerbraten from the repositories [here]("apt:sauerbraten").

---

### Post by harry71194 on 2009-08-04
Thanks for the reply. The version in the repos are outdated. And people at IRC told me I am so out of luck... if they server does not allow resuming downloads, then it won't work.

---

### Post by credobyte on 2009-08-04
Depends on server settings .. resume ability can be disabled ( by using various *redirects* and *slot reservation* ).

---

### Post by markharding557 on 2009-08-04
you can find updated debs at getdeb it's in my sig.
also try the downloadthemall plugin for firefox

---


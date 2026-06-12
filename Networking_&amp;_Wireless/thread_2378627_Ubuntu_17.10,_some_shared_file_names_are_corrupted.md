---
title: "Ubuntu 17.10, some shared file names are corrupted looking, truncated"
date: 2017-11-25
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2017-11-25
The file will play off the shared folder, these are videos.
Win7 looks at the folder and displays as this.
[[img]https://s20.postimg.org/kkek1uxod/corrupted_names.png[/img]](https://postimg.org/image/h0smc1uyh/)

and here is how they look in ubuntu, no problem there.
[[img]https://s20.postimg.org/99bwd5yfh/ub1.png[/img]](http://postimg.org/image/v8ib0df9l/)

[[img]https://s20.postimg.org/nfrn8e1kt/ub2.png[/img]](http://postimg.org/image/5076azng9/)

---

### Post by sdowney717 on 2017-11-25
I fixed the issue
[https://superuser.com/questions/458995/files-folders-get-weird-names-and-become-inaccessible-on-samba-share](https://superuser.com/questions/458995/files-folders-get-weird-names-and-become-inaccessible-on-samba-share)
It's a file name mangling problem. Samba is converting filenames down to old style DOS 8.3 filenames.

Edit /etc/smb.conf (*) and add mangled names=no to the [global] section and restart the smb service.

Reference: [http://oreilly.com/openbook/samba/book/ch05_04.html](http://oreilly.com/openbook/samba/book/ch05_04.html)

---


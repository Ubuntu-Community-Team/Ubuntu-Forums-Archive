---
title: "Package Update Manager can't find repository"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by mrearl on 2009-02-19
Hi:

I'm running Hardy on a Dell mini 9.  The package Update Manager consistently cannot find one repository as follows:

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored, or old ones used instead.

It doesn't seem to affect anything but it's annoying and I'd like to fix it if I can.

Can anyone tell me why this is happening and what I can do about it?

Thanks

---

### Post by cariboo on 2009-02-19
Have you tried a different server? Go to System-->Administration-->Software Sources and click the download from drop down and choose the main server.

Jim

---

### Post by mrearl on 2009-02-19
Thanks, Jim.

When I looked at the Software Sources I was already pointing to main, *but* while I was under the Ubuntu tab I noticed that I was allowing restricted (multiverse) updates.  I'm still kind of new to Ubuntu but I would like to keep things as open source as possible, so I unchecked multiverse and the problem went away.

If I understand things correctly, I really don't need anything from multiverse anyway and now I don't have to see the error anymore.

Thanks for pointing me in the right direction.

Roger

---


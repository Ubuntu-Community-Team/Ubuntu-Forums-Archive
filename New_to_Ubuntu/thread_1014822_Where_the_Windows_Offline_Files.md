---
title: "Where the Windows Offline Files?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by lucasl on 2008-12-18
Hi,
I recently installed Ubuntu on a laptop of mine. It had XP on it, and "My Documents" was set up to synchronise with a server with the Offline Files feature.

Now I'm in Ubuntu, I can't find My Documents anywhere? It isn't in Documents and Settings like it normally is because technically it is located on the server. But they have to be on my computer somewhere, because I use them at home.

Thanks!

---

### Post by lovelyvik293 on 2008-12-18
The XP's My Document is present inside one of the partitions which are mounted in the /media.Just check the /media.

---

### Post by lucasl on 2008-12-18
Well obviously it is in there *somewhere*, but where? It isn't in all the usual locations, and a search for "My Pictures" came up with no results.

I'm thinking its stored in some sort of cache.

---

### Post by lovelyvik293 on 2008-12-18
If you have the windows drive mounted?

---

### Post by lucasl on 2008-12-18
> **lovelyvik293 said:**
> If you have the windows drive mounted?
Yes, and looked in <drive>/Documents and Settings/<user> but there is no Documents folder, because it is stored on the server, just like I said in the OP :P.

---

### Post by sges on 2008-12-18
This may or may not work.

Boot XP. In Windows explorer right click on a file and select properties. Select the General tab. Hopefully Location will be the real location and the just the mapped location.

I suspect the location will be a hidden directory.

---


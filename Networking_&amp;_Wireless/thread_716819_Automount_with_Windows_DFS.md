---
title: "Automount with Windows DFS"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by alvinbennett on 2008-03-06
Greetings!

I have a little bit of an odd automount/autofs situation. I have a Windows fileserver with Ubuntu desktops. I have setup NFS shares on the Windows fileserver and use automount/autofs to mount them on the Ubuntu 7.10 desktops. Everything works great!

Enter DFS. We are moving our filesharing strategy to make use of Windows DFS. Instead of remembering that your windows share is at \\server-57\myshare, you'll just use \\shares\myshare for example (on Windows).

So, does anybody know if it's possible (and if so how) to get automount/autofs to mount NFS shares on a Windows fileserver by using the Windows DFS path?

Thanks!
Alvin

---


---
title: "&quot;last&quot; command with NIS"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by TJCIB on 2008-12-11
I have scoured google and NIS pages looking for an answer with no luck.

I want the "last" command to be used on my NIS server to show who is logging into all of the clients.

Using "last" on the clients shows who logged in on that workstation, but using it on the server only shows when someone (me) logs in on the server.

The only way I have gotten the same result is to use
```
last >> /NFS/mount/txt
```
If I run that on each workstation and have it append a text file in a mounted directory, I get all the information, but it isn't organized and will not be chronological.

Any thoughts or help would be great.  I'm not a script writer, but am willing to give it a shot if that's the way.

Thanks

---

### Post by TJCIB on 2008-12-12
any ideas?

*aka...bump*

---


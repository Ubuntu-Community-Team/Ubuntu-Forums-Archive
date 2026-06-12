---
title: "ndiswrapper won't compile"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by mocomber on 2008-11-01
So in my newbie status, when I updated to 8.10 my wireless got messed up somehow. But now, when I try to reinstall ndiswrapper, I get these errors in the terminal: 

/home/ryan/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type.


This occurs about 8 times, then it eventually leaves the directory and closes out on error. Can anyone help with this? Thanks

---

### Post by Ayuthia on 2008-11-01
> **mocomber said:**
> So in my newbie status, when I updated to 8.10 my wireless got messed up somehow. But now, when I try to reinstall ndiswrapper, I get these errors in the terminal: 

/home/ryan/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of 'iwe_stream_add_point' from incompatible pointer type.


This occurs about 8 times, then it eventually leaves the directory and closes out on error. Can anyone help with this? Thanks

You might try to use ndiswrapper from the repositories.  Just install ndiswrapper-utils-1.9.  Or you can try ndisgtk.  It is also there.  It is the GUI version of ndiswrapper.  Once installed, just go to System->Windows Wireless Drivers (if I recall correctly).

ndiswrapper 1.53 does not seem to compile in 2.6.27 and I have not seen the patches for it yet.

---

### Post by mocomber on 2008-11-01
I can't get online to get that repository. Any other possibility if I plug it in directly it will work?

---


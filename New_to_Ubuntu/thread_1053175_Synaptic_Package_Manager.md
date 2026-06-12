---
title: "Synaptic Package Manager"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by meddyliol on 2009-01-28
I tried to run the Synaptic Package Manager and it came up with the following message: 

'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.'

I ran 'dpkg --configure -a' from the terminal and received the message:

'requested operation requires superuser privilege'

The question is, how do I get a superuser privilege?

Cheers

Brian :(

---

### Post by Nepherte on 2009-01-28
You can run a command with root (admin) privileges if you prefix it with sudo, so:
```
sudo dpkg --configure -a
```

---

### Post by meddyliol on 2009-01-28
Brilliant, thanks a lot. That solved the problem. I just re-booted and it wouldn't perform some updates until I did that.

Cheers

Brian :D

---


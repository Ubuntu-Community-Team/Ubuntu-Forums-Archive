---
title: "bad resolution file"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by nodyl on 2007-05-02
Hiya, I was wondering if anyone knows a way to stop my resolution file from updating itself.  My roommate has the router misconfigured and refuses to do it properly so everytime I turn on my computer I have to edit the resolution file to connect to the net.  It's really annoying.

---

### Post by Floppyjoe on 2007-05-02
> **nodyl said:**
> Hiya, I was wondering if anyone knows a way to stop my resolution file from updating itself.  My roommate has the router misconfigured and refuses to do it properly so everytime I turn on my computer I have to edit the resolution file to connect to the net.  It's really annoying.

This link may help:
[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

---

### Post by nodyl on 2007-05-02
I actually need to erase things in my resolution file, not prepend.

---

### Post by Floppyjoe on 2007-05-02
prepend will move the dns servers of your choice in front of what ever is in that file so it will use those first all the time.

---

### Post by nodyl on 2007-05-02
Wow, I kind of feel like a moron.  I'll try it, thanks!

---

### Post by hyperair on 2007-05-02
```
sudo chattr +i /etc/resolv.conf
```

I faced this problem before and used the command above. It worked for me.

---

### Post by nodyl on 2007-05-02
Thanks floppyjoe, that totally worked!

hyperair, I'll keep your fix in mind if stuff breaks!

---


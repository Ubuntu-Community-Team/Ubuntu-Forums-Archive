---
title: "@ sign in username for proxy"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by kLy on 2006-10-24
Hi

I'm having a problem with the http proxy. Generally for all CLI apps, you only need to export the env var http_proxy in the form of:

http://user:pass@host:port

My problem is that I have an "@" sign in the username itself (and password too), now programs don't know how to deal with this. Is there some way of escaping the "@"?

Thanks!
kLy

---

### Post by ciscosurfer on 2006-10-24
Don't use the @ symbol in your usernames and passwords -- there's plenty of other characters you can use and you won't have this problem anymore!

---

### Post by kLy on 2006-10-25
Of course, that would have been the obvious thing to do given the choice, which I'm not. If you think about it, for most of the situations where proxy auth would apply would be for large institutions (eg. university), and of course I don't have a choice of just arbitrarily changing my username to something more useful to me.

---

### Post by ciscosurfer on 2006-10-25
The best way to deal with this, then, is to not add your username/pass to the URL line; simlply wait for the username/pass dialog to popup and then enter them.  Sorry, mate.

---

### Post by kLy on 2006-10-25
Yeah that would be useful, but for CLI apps, most don't have this user / pass prompt :(

---


---
title: "[SOLVED] 403 Error from my own server??"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by doctorbighands on 2009-01-03
I'm trying to call up a webpage in Firefox that I'm hosting on my home server. When I do, I get a 403 Forbidden error. Why is that, and how do I fix it?

Thank you!

---

### Post by doctorbighands on 2009-01-03
...bump

---

### Post by Kellemora on 2009-01-03
Hi DBH

When you PUT the file onto your server it probably changed the PERMISSIONS on it.

We had that problem big time, for a long time.  Any file we would PUT somewhere else the permissions would change.  So we made it a policy to only FETCH files, never PUT files.

Since building the new file server, that has not been a problem anymore, and sorry to say, I have no idea why either.

Just go to the file in question and change the permissions back to what you want them set to and it should work just fine after that.  Don't forget to SAVE after making your changes!

TTUL
Gary

---

### Post by efexD on 2009-01-03
Error Code 403 -

Your Web server thinks that the HTTP data stream sent by the client (e.g. your Web browser) was correct, but access to the resource identified by the URL is forbidden for some reason.

In other words, something probably doesn't have permission.

---

### Post by doctorbighands on 2009-01-03
Hmm...so we've established what the problem is (thank you!), but not how to fix it. Any ideas? I'm still clueless.

---

### Post by doctorbighands on 2009-01-03
SOLVED! I figured it out!

I typed in the following command:
```
sudo chmod -R a+rwx /var/www/<folder>
```

Now I can access the page!

Thank you to everyone for your help.

---


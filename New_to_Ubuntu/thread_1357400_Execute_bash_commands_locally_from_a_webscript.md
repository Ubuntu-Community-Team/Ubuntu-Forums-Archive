---
title: "Execute bash commands locally from a webscript?"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by firebirdworks on 2009-12-17
I've been searching for this one for quite a while, and still no luck.

Is it at all possible to have a program launch itself, for the local user, because I clicked a hyperlink on a website I am working on?  I'm not the best bash programmer, thats for sure, but web stuff is kinda my thing.  So is there a way to do this in Ubuntu?

---

### Post by xifer on 2009-12-17
Don't think so with javascript but with php you can 

[http://www.php.net/manual/en/function.shell-exec.php](http://www.php.net/manual/en/function.shell-exec.php)

---

### Post by firebirdworks on 2009-12-17
> **xifer said:**
> Don't think so with javascript but with php you can 

[http://www.php.net/manual/en/function.shell-exec.php](http://www.php.net/manual/en/function.shell-exec.php)

That is a server side thing though, right?  That isn't a local execution?

---

### Post by xifer on 2009-12-18
> **firebirdworks said:**
> That is a server side thing though, right?  That isn't a local execution?
You're right - I don't think this can be done for obvious security reasons. You'd have to download a script from the server to the client and have the user manually run it...

---


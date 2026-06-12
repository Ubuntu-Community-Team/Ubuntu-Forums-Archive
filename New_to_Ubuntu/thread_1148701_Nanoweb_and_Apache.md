---
title: "Nanoweb and Apache"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by mackristo on 2009-05-04
This may be a ridiculous question but here goes, I downloaded Nanoweb in order to perform a wordpress installation, which seemed to work just fine.  Now I've noticed that the other projects I had running under Apache, such as Joomla, can't be found when I type in the appropriate localhost address (localhost/joomla).  Instead, the Nanoweb logo appears so it's clear that localhost is running under Nanoweb.  Is there some way to run Nanoweb under Apache, or some other way, so that they can both be run for various projects?

---

### Post by mpsii on 2009-05-04
You could always change the default listen port to something other than 80 (8000, 8080 are some suggestions).
 
[http://nanoweb.si.kz/manual/core.html#listenport](http://nanoweb.si.kz/manual/core.html#listenport)

---

### Post by mackristo on 2009-05-04
Just in the .conf file?  Do you think I would need to move the nanoweb directory under the Apache directory?

Thanks for your help.

---

### Post by mpsii on 2009-05-04
> **mackristo said:**
> Just in the .conf file? Do you think I would need to move the nanoweb directory under the Apache directory?
 
Thanks for your help.
 
All you are doing is changing the configuration file. You do not need to move content. Once you have finished and bounced nanoweb, you should find your Apache content on [http://localhost](http://localhost) and the nanoweb content on whatever port you chose [http://localhost:8080](http://localhost:8080)

---

### Post by mackristo on 2009-05-04
Yep,
That did it.  Much thanks.  I had to tinker with the urls a little and ended up having to clear the db and reinstalling but it seems fine now.  Thanks for your help.


CM

---


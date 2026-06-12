---
title: "Simple internal redirect in Apache"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by Cuddles McKitten on 2009-09-04
I'd like my web server to automatically send users who type in domain.com  (from my index.html) to domain.com/higherdirectory/index.html.  Currently, I have a 1 second HTML redirect, but I don't think this is a terribly elegant solution.

[SIZE=1](I'm sure this has been asked before but, for whatever reason, I can't seem to get the right keywords to find exactly what I'm looking for).

Edit.  Thanks.  Now if I could just somehow edit this to be marked as solved, everything would be well. :)
[/SIZE]

---

### Post by Bachstelze on 2009-09-04
```
Redirect /index.html /higherdirectory/index.html
```

into your .htaccess or Apache config file.

---


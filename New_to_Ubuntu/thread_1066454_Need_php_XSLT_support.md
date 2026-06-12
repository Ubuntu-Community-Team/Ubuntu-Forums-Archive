---
title: "Need php XSLT support"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by jaanleva on 2009-02-10
(I am new to linux/ubuntu) while trying to build a symfony project I realized that I don't have XSL with PHP.

How do I build/configure php with xsl support?

I tried '*yum install php-xsl*' and it didn't quite work...

thanks

---

### Post by kford on 2009-12-14
This is old and you've probably found your answer, but just for completeness's sake:

For PHP5
```

sudo apt-get install php5-xsl

```

If you are using apache, you might have to reload apache after installing XSL support (you don't if you are using PHP5 on the command line).

---

### Post by joedeluca on 2011-04-09
Thanks for the follow-through - you just answered my question exactly!

---


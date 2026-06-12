---
title: "svn question"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by carrarin on 2010-09-28
Hey, why cant I commit to my svn repository

```
svn: Commit failed (details follow):
svn: Server sent unexpected return value (500 Internal Server Error) in response to MKACTIVITY request for '/svn/!svn/act/9ed66992-8844-4c24-a307-6daca8dad0ed'
```

thanks

---

### Post by andrewthomas on 2010-09-29
Are you behind a proxy?

```
Next, you need to make sure the proxy server itself supports
 all the HTTP methods Subversion uses.  Some proxy servers do not
 support these methods by default:
 PROPFIND, REPORT, MERGE, MKACTIVITY, CHECKOUT.
```**For Squid, the config option is**

```

   #  TAG: extension_methods
   #       Squid only knows about standardized HTTP request methods.
   #       You can add up to 20 additional "extension" methods here.
   #
   #Default:
   # none
   extension_methods REPORT MERGE MKACTIVITY CHECKOUT
```from [http://subversion.apache.org/faq.html](http://subversion.apache.org/faq.html)

---


---
title: "Webserver is wacky"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by vanhornd on 2009-12-23
Hello Ubuntu users and admirers,

When I set my apache web-server up, I was able to see all of the appropriate pages on my website.  This morning I enabled vsftpd so I could FTP to my webserver and edit pages that needed updating.  Now I can see only three pages out of about a thousand!  

I get this message:
**Forbidden**

 You don't have permission to access /index.html/html/FT_M&A1.htm on this server.


All of the pages have identical permissions -- why is the Apache server discriminating against most of my pages?

---

### Post by Geoff918 on 2009-12-23
> **vanhornd said:**
> Hello Ubuntu users and admirers,

When I set my apache web-server up, I was able to see all of the appropriate pages on my website.  This morning I enabled vsftpd so I could FTP to my webserver and edit pages that needed updating.  Now I can see only three pages out of about a thousand!  

I get this message:
**Forbidden**

 You don't have permission to access /index.html/html/FT_M&A1.htm on this server.


All of the pages have identical permissions -- why is the Apache server discriminating against most of my pages?

Sounds like an ownership issue. Who owns the directories you're trying to access?

Is it www-data?

You should be able to find out with the following:

ls -a (I think that's the command. I'm away from my home machine on another system, so that's what I remember)

It should give you something like

www-data  www-data w-rwrwr--x-x something like that.

might say

root root

---


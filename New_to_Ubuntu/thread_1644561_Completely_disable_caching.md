---
title: "Completely disable caching"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by tbrammer on 2010-12-13
All,

I'm not sure if this is beginner enough for the beginner forum, so feel free to move me if necessary.

I've installed Apache and have the nice "It works!" page displaying fine. The issue I'm having is with caching, specifically in disabling it. I'm running a digisign system called Xibo, that utilizes Awesomium to embed web pages and content. Trouble is that it caches the pages as long as its running, so the same page is constantly displayed regardless any modifications made to it. In attempting to correct this, I've come across some .htaccess directives to disable caching in pretty much every way, but I can't get it to work.

at this point I have created a .htaccess file and put the following lines into it:

```
<FilesMatch "\.(html|htm|js|css)$">
FileETag None
<IfModule mod_headers.c>
Header unset ETag
Header set Cache-Control "max-age=0, no-cache, no-store, must-revalidate"
Header set Pragma "no-cache"
Header set Expires "Wed, 11 Jan 1984 05:00:00 GMT"
</IfModule>
</FilesMatch>

```No dice. The page still won't update. Any suggestions?

Thanks,
-Tim

---

### Post by wep940 on 2010-12-13
Do you mean Apache or Xibo is doing the caching that is causing the problem?
 
I don't know anything about Xibo, but did spend a few minutes looking at the website and trying to find information in a basically empty online manual - most pages weren't created yet.  However, have you found any type of flush or refresh administrative command for it?

---

### Post by tbrammer on 2010-12-13
If the HTTP headers don't contain specific cache timeouts (ie they  allow the browser to decide how long to cache content for) then the  pages are never updated. This is because Xibo has an in-memory  cache which lasts for the entire time the webcore is running. Pages that  do specifically specify no-cache in the headers are correctly pulled  fresh each time.


 My understanding was that the webcore is destroyed each time a region  moved to the next item, but clearly it can't be as there is still this  persistence.


I've got the solution, but I'm struggling to implement it. I just need the correct configs in .htaccess and where ever else in apache. The problem is with Xibo, but the solution is in Apache.

---


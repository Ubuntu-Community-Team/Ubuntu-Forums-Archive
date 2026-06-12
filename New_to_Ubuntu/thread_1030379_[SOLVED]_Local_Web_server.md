---
title: "[SOLVED] Local Web server"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by xsilvergs on 2009-01-04
Hi,

I'm having a go at web page design and using my Xubuntu laptop as a web server.

It has a folder /var/www/BWAM_V2, if I [http://192.168.1.5/BWAN_V2/home.html](http://192.168.1.5/BWAN_V2/home.html) from another PC I can view my web creation.

Now I have more than one version, so in /var/www/BWAM_V3 resides also.

So I thought I'd create an index.html file, this also resides in /var/www.

I can [http://192.168.1.5/index.html](http://192.168.1.5/index.html) and see my index for BWAM_V2 and BWAM_V3.

What should the <a href="http://???? be in the index.html to allow me to get to the home.html in either the BWAM_V2 or BWAM_V3.

Hope this makes sense.

Tony

---

### Post by albinootje on 2009-01-04
> **xsilvergs said:**
> 
So I thought I'd create an index.html file, this also resides in /var/www.

I can [http://192.168.1.5/index.html](http://192.168.1.5/index.html) and see my index for BWAM_V2 and BWAM_V3.

What should the <a href="http://???? be in the index.html to allow me to get to the home.html in either the BWAM_V2 or BWAM_V3.

Assuming that you really meant to use "home.html" as a file :
[http://192.168.1.5/BWAM_V2/home.html](http://192.168.1.5/BWAM_V2/home.html)

But if you have an index.html file in there too, then this should be enough :
[http://192.168.1.5/BWAM_V2](http://192.168.1.5/BWAM_V2)

---

### Post by kestrel1 on 2009-01-04
Just a small suggestion: Always use lowercase for folder & file names when creating a website, so BWAM_V2 would become bwam_v2
Only a suggestion, but I have used upper case in the past & it doesn't always work correctly lower case does.

---

### Post by nemilar on 2009-01-04
Really you would want to use relative URLs in your tags:

```
<a href="BWAM_V2/home.html">bwam_v2/home</a>
```
or 
```
<a href="/BWAM_V2/home.html">bwam_v2/home</a>
```




But this is more of an HTML question than a linux question.

---

### Post by xsilvergs on 2009-01-04
@ nemilar

Thank you, that did it. Yes I see it is more HTML but I usually get stumped by permissions so this makes a change.

---

### Post by xsilvergs on 2009-01-04
Now I seem to have a permissions problem. Index has <a href="BWAM_V2/home.html"> blah and <a href="BWAM_V3/home.html"> blah.

the link to the BWAN_V2 works but the the link to BWAN_V3 has an error message in Firefox You don't have permission to access /www_bwam/bwam/BWAM_V3/home.html on this server.  Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch Server at 192.168.1.5 Port 80.

If I ls -l /var/www/www_bwam:
drwxr-xr-x 3 root root 4096 2009-01-04 18:58 BWAM_V2
drwxr-xr-x 3 root root 4096 2009-01-04 18:58 BWAM_V3

Any ideas?

Have done some more ls-l and find the Folder that works has files with permissions -rwxr-xr-x , the Folder that won't work has files with permissions rw and rwx.

Is it possible to do batch chages of permissions and if so how?

---

### Post by xsilvergs on 2009-01-04
All sorted now slow process but I think I understand a bit more. The numbers are easier to understand than the letters.

Thanks for help.

---

### Post by make haf on 2009-01-05
Washington DC is convenient & affordable in providing solutions to logo design, web design, [graphic design ]("http://www.imageworksstudio.com/marketing/marketing-strategy-direction.html")services, internet marketing & search engine marketing services

---


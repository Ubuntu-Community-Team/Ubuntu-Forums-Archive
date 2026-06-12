---
title: "Reading apache logs"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Cyked on 2009-06-05
Not sure where this should go, but I'm a noob so I'm posting here.

I looked around a bit on how to read through the apache access.log files and have a question.

```
x.x.x.x - - [05/Jun/2009:13:43:39 -0700] "GET /directory1/directory2/file1.jpg HTTP/1.0" 200 114743 **"http://www.somewebsite.com"** "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.10) Gecko/2009042316 Firefox/3.0.10"
```

I've found examples on blogs and such but the examples I have found only go up to the HTTP/1.0 part of the logged item.  I'm curious as to after the 200 successful item and how big the file was that was accessed, what is the next item?  In this case the somewebsite.com part of my log.....

EDIT: I think I just answered my questions.  It would be the site that accessed the file on my server.  So if the item after the file's size if my web address, it was accessed from the site itself.  If its another site its hotlinked, and if that is the case the IP accessing it would be the originating source IP viewing the image.... Correct?

However, I am not understanding what this line is...

```
X.X.X.X - - [05/Jun/2009:14:15:59 -0700] "GET **/icons/image2.gif** HTTP/1.1" 200 309
```

I don't know what this is. Its showing like it was successfully downloaded, but that's not a valid file or directory.  the rest of it, like jonobr references below, is being referred from the site itself.  So if my browser is connecting to the root page, why is it requesting a file that doesn't appear to exist?

---

### Post by jonobr on 2009-06-05
I found the following at the [Apache org website]("http://httpd.apache.org/docs/1.3/logs.html#common"), after I checked my own dev website and saw  a dash......


> 

"http://www.example.com/start.html" (\"%{Referer}i\")
    The "Referer" (sic) HTTP request header. This gives the site that the client reports having been referred from. (This should be the page that links to or includes /apache_pb.gif).
"Mozilla/4.08 [en] (Win98; I ;Nav)" (\"%{User-agent}i\")
    The User-Agent HTTP request header. This is the identifying information that the client browser reports about itself.



---

### Post by Cyked on 2009-06-05
I found the files being referenced in the apache access logs.
It's  /usr/share/apache2/icons

So... cool, I figured it out.  Thanks for reading. :lol:

---


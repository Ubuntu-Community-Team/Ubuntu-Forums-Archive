---
title: "Apache2 prompt to download application x-trash"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by jshock on 2009-02-10
Okay, I'm experiencing the same problem as described in a very old post listed below and I'm not able to post in the ancient read-only forum.
Is there a fix for this?  I've googled, googled and searched forums.

I use Firefox and i browse to my [http://mysite.com/lists](http://mysite.com/lists)
and it prompts to dload a application/x-trash file.

if i Firfox and browse to my [http://mysite.com/lists/index.php](http://mysite.com/lists/index.php)
it works fine.

if i use IE and browse to [http://mysite.com/lists](http://mysite.com/lists)
it works just fine.

there where two files in the lists folder:
index.php and index.html

I think it might of occurred when i renamed the index.html to index.old  I tried to put everything back the way it was but no luck.

Can anyone help out?

>Original Post:
 fr3ak
First Cup of Ubuntu
 
Join Date: Apr 2006
Posts: 1
	
Re: Apache2 is sending deleted files as mimetype application/x-trash
OK... I spent ages trying to figure it out, the problem only exists for mozilla based browsers (I hate to say it but IE is not affected) but I have found out where the MIME types is found and controlled from... /etc/mime.types in there is where it points to .old .bak etcetera, thinking that this may be the cause i just changed the types to html php... bingo no file trying to be downloaded, but also no page being found at all... so weird. So if you type the whole address [http://foo.com/index.html](http://foo.com/index.html) or php it loads the page no problem but if you just try to load the root it can't find the file... so who is being to tricky? Firefox or Apache? Please enlighten him ^ me the rest of the world if you have found a solution.

---

### Post by coCoKNIght on 2010-03-04
I just experienced the same problem. After deleting an **index.html~** file which is created when I edit files with gedit AND deleting my old backup **index.html.bak** everything worked as expected again.

---


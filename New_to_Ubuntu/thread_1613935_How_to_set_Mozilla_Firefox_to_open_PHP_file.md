---
title: "How to set Mozilla Firefox to open PHP file ?"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by Linux-is-super on 2010-11-05
Hi !
I downloaded a site for off line browsing by using WGET . But I can only open "index.html" and whenever I want to open some link on index page Mozilla Firefox shows me following :
"you have chosen to open .... (i.e. file that is linked to index.html)
which is a: PHP file
from: ... (location)
What should Firefox do with this file ?

Open With (Browse button)
Save file

How can I solve this problem so Mozilla Firefox can open PHP files ?

---

### Post by Linux-is-super on 2010-11-05
And here is the the screen photo.

---

### Post by Linux-is-super on 2010-11-05
Is there some application other than Mozilla Firefox to view these files ?

---

### Post by P4man on 2010-11-05
You can just select open with, then browse to /usr/bin/firefox.
However, the website may not work offline. PHP files are server side scripts which generate HTML, but these pages may not exist or work statically.

Alternatively, you try to use a proper website grabber, like WebHTTrack which is in the software center. Although that wont work with every site either.

---

### Post by mcduck on 2010-11-05
You are not supposed to ever get a .php file form any web site, it's not something you could actually view yourself (apart from using a normal text editor to read the code), it's intended for the web server.

When things work as they should, the web server reads the .php code, and based on it creates HTML code that is sent to your web browser.

If some web page you are trying to access is offering you a .php file, that's *always* an error (or bad configuration) on the server itself.

(if you really want to view a .php file you need to install a web server with PHP, put the file in the server's root directory and then access the server through your browser)

---

### Post by P4man on 2010-11-05
> **mcduck said:**
> You are not supposed to ever get a .php file form any web site, it's not something you could actually view yourself (apart from using a normal text editor to read the code), it's intended for the web server.

Ahm.. no. Check the url on top of this very forum. Its PHP. And thats quite normal. The actual page no longer contains PHP code, but the extension isnt changed. The page just contains HTML and firefox should be able to open it.

---

### Post by Goldfissh on 2010-11-05
> **P4man said:**
> Ahm.. no. Check the url on top of this very forum. Its PHP. And thats quite normal. The actual page no longer contains PHP code, but the extension isnt changed. The page just contains HTML and firefox should be able to open it.

We're able to read the php file because it's being read from the webserver. You can't just open a PHP file at home and read it. You can however...

[LIST]
[*]Install some webserver software and view the page from your localhost, OR
[*]Rename the page as .html and view it without the PHP script running.
[/LIST]

---

### Post by mcduck on 2010-11-05
> **P4man said:**
> Ahm.. no. Check the url on top of this very forum. Its PHP. And thats quite normal. The actual page no longer contains PHP code, but the extension isnt changed. The page just contains HTML and firefox should be able to open it.

I didn't you you couldn't open a web page with .php name, I said you can't open a .php file itself.

The server reads the code and sends the viewer HTML code, but that doesn't change the name of the web page you are viewing. You just get completely different content than what's inside thee actual .php file itself.

In other words, when  you browse ubuntuforums your URL may have a .php file in it, but that doesn't mean that you'd ever see the actual .php file itself, only the code the server generated from the .php file.


Anyway, you are correct in the sense that the OP has actually downloaded the stuff using wget, so the .php file he has already contains the generated HTML instead of what's in the original .php file on the server. So the best way would probably to simply rename the file to .html (which is correct for the content of the fle). Of course that would break lots os stuff o the site, but most likely it's already pretty much broken if it relies heavily on PHP to function.

---

### Post by P4man on 2010-11-05
> **Goldfissh said:**
> We're able to read the php file because it's being read from the webserver. You can't just open a PHP file at home and read it. You can however...

Sure you can. Its just an HTML file now. Look at the page source, its only html and javascript.  For the browser it doesnt matter if its a PHP served by a webserver who generated the HTML on the fly (from PHP code) or if its a static HTML file from disk or served via http.

What you can not do without a webserver is open the **source** PHP file which is on the forum server, but we dont even have access to that. All we get is HTML, regardless of the page extension.

Now if the original poster grabbed a site by copying from the server's /var/wwwroot, then indeed it wont work without a local webserver. I understood it as he fetched the files through HTTP from a running webserver, in which case, he only has HTML pages now.

---

### Post by Linux-is-super on 2010-11-06
Thank you all ! 
Finally solution !!! Solution is to use the WebHTTrack. You can find it in the Ubuntu Software Center. 

Buy the way, renaming some_file.php to some_file.html will not work

---

### Post by ieee488 on 2010-11-06
> **Linux-is-super said:**
> Thank you all ! 
Finally solution !!! Solution is to use the WebHTTrack. You can find it in the Ubuntu Software Center. 

Buy the way, renaming some_file.php to some_file.html will not work

It will work if all you want to do is **view** the file. 

I don't know exactly how you were using wget, but if you use it in FTP mode, you would get the "pure" PHP file.

However, without a webserver to process the PHP file, I am not sure what use the PHP file is to you, unless you are trying to copy code someone else has written.

---


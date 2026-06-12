---
title: "Lampp installation - where to put files?"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by kramer65 on 2011-08-07
Hello,

I think I once installed the elements of a lamp server on my pc, but I never really finished it. I now thought I would use the Xampp package so I followed [this guide]("http://ubuntuforums.org/showthread.php?t=223410") to install Xampp.

The guide says that when I go to localhost I should get the xampp startpage. I do get a page on [http://localhost/](http://localhost/) but it just says "*It works! This is the default web page for this server. The web server software is running but no content has been added, yet.*"

I also made the public_html folder in my home folder but I can't seem to visit any files I put in there from the browser. Also, I don't understand where I can find the file which says the "*It works! This is the default web page..."* etc.

All in all I am just a bit lost on where to put my web files to test them on my pc. And I am also a bit unsure of whether the previous installed lamp components may be conflicting with the present xampp installation. How do I know that the page I see on localhost isn't the previous lamp installation, but the newly installed xampp..?

Does anybody have a tip on how to proceed from here..? All tips and help are welcome!

---

### Post by Wim Sturkenboom on 2011-08-07
> **kramer65 said:**
> ... Also, I don't understand where I can find the file which says the "*It works! This is the default web page..."* etc.
Check /var/www; probably a file called index.html

xampp seems to have their own forum on [http://www.apachefriends.org/f/viewforum.php?f=34](http://www.apachefriends.org/f/viewforum.php?f=34)

---

### Post by ~!geek!~ on 2011-08-07
The default location to put all the web projects in ubuntu with LAMPP is :
/var/www/
You may make symbolic link to public_html directory from this directory.

---

### Post by kramer65 on 2011-08-07
Ah, thanks! It was indeed in /var/www/. I decided to totally remove lampp and after that xampp suddenly worked like a charm.

I just have a problem now since it says that [http://localhost/myusername](http://localhost/myusername) is prohibited (error 403) since I have no permission to visit the folder (/home/myusername/public_html). I tried to chmod 777 -R /home/myusername/public_html, but that doesn't help at all.

Any idea what could be wrong here..? Could it be that it doesn't work because my /home is encrypted?

---


---
title: "Install w3c markup validator on local apache webserver"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by InfernalAngel on 2010-06-10
Uhm plzz help me out before I've messed up with my server setting. 

I've Install w3c-markup-validator from application software center

after that I've coy the file check from /usr/lib/cgi-bin/check to /home/username/public_html/cgi-bin/

The when I'm go to borwser by go to localhost/cgi-bin/check?uri=www.google.com&charset=(detect+automatically)&doctype=Inline&group=0

the response was 
______________________
**Software error:**

 HTML::Template->new() : can't mkdir /tmp/validator/65 (file_cache => 1): Permission denied at /home/username/public_html/cgi-bin/check line 290
 For help, please send mail to the webmaster (webmaster@localhost), giving this  error message  and the time and date of the error.
______________________

I've installed mod perl and I've tested other perl script working well on web server

---

### Post by hellblazer on 2010-06-10
As far as I can tell you need to make the directory /tmp/validator/65 writable for the user www-data.

The www-data user is your webserver user.

It might be a good idea to make the /tmp/validator directory and all it's sub-directories writable for www-data.

```
sudo chgrp -R www-data validator
```
```
sudo chmod -R 775 validator
```
in your terminal when in the /tmp directory

Hope that helps

---

### Post by InfernalAngel on 2010-06-13
tks. 
Think I've figured it out in the config file
cache=/path/to/temp should change to some folder which www-data has the permission to write or create file.
Solved

---


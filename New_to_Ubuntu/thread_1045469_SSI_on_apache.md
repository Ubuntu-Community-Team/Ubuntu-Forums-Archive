---
title: "SSI on apache"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by TheDarkMaster on 2009-01-20
Hi all,
has been some time sice I last posted here. But I've a question.
I got apache on my Ubunut 8.10 desktop edition and I want to enable SSI.
I got it enabled finnaly but now it's doing something really weird.
I got a file named index.shtml in my /var/www/ directory and enabled SSI for that directory. Now always when I directly type [http://localhost](http://localhost) I get a empty page with my SSI as comment. But if I type [http://localhost/index.shtml](http://localhost/index.shtml) I get the correct output from the SSI.

To anyone who knows the answer Im in your debt.
Thanks to anybody who reaplys cause my last post was just ignored:(

---

### Post by louieb on 2009-01-20
In the apache configuration file there is a directory index section. It lists the files it should display if no specific file is given.  Believe the configuration file is /etc/apache2/sitesenabled/<somename>.

---

### Post by TheDarkMaster on 2009-01-21
Thanks for the reply, but that isnt the problem. He clearly loads my page but he doesnt parse it with the server when I dont give the exact filename.

here's my directory section in httpd.conf for that directory:

```

DirectoryIndex index.shtml index.html index.php

<Directory /var/www/*>
AllowOverride None
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
Options +Includes
</Directory>

```

---


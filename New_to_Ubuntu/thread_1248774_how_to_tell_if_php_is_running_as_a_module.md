---
title: "how to tell if php is running as a module"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by occams_beard on 2009-08-24
How can I tell if php running under apache compiled as a module?

phpinfo() shows "Server API 	Apache 2.0 Handler"

what does that mean?

---

### Post by loomsen on 2009-08-24
Hello.

grep -i php /proc/modules

or

lsmod | grep -i php

will show if php is up and running as a module :)

---

### Post by occams_beard on 2009-08-24
Don't those show kernel modules?  PHP would be an Apache module, would it not?

I need to know if php is running under apache as a module, or say as cgi.

---

### Post by occams_beard on 2009-08-24
httpd -l | grep php

returns nothing...  What would the php module be called? mod_php ?


(I know under ubuntu apache is "apache2", but i'm working with centos)

---

### Post by loomsen on 2009-08-24
I'm on F11.

[http://pastie.org/593500](http://pastie.org/593500)

Thats what a package manager query shows for php | grep apache

---

### Post by stoobers on 2009-08-24
> **occams_beard said:**
> How can I tell if php running under apache compiled as a module?

phpinfo() shows "Server API 	Apache 2.0 Handler"

what does that mean?

This is from the apache info page on handlers.

A "handler" is an internal Apache representation of the action to be performed when a file is called. Generally, files have implicit handlers, based on the file type. Normally, all files are simply served by the server, but certain file types are "handled" separately.

But if you can run the function "phpinfo()", mod php is installed and running.

---


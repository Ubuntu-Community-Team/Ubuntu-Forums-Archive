---
title: "PHP testing"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by ciborium on 2009-01-16
This may be in the wrong forum, move if necessary.

After having created web pages with HTML and Javascript, I was wanting to try to learn to use PHP.

The problem is that my usual method of creating and testing web pages doesn't work.  Generally I create an HTML document in Text Editor, save it and then right-click and run in Firefox.  Any of the PHP pages I create just give me a dialog asking where to save the file.

I installed PHP 5, Apache 2, and LAMP server.

Is it possible to set up my system to be able to test my pages as described?  And how?

If it is not possible, how can I best test my pages without uploading them to a server to test?

I tried to follow this tutorial:
[http://www.howtoforge.com/ubuntu_debian_lamp_server](http://www.howtoforge.com/ubuntu_debian_lamp_server)

I put a test file in the directory /var/www/ and it still does the same, even when running from root.

I even tried typing /var/www/test.php into Firefox address bar.

What am I doing wrong?

---

### Post by iaculallad on 2009-01-16
That should not be:

> /var/www/test.php

being placed on browser's address bar, it should be:

> [http://your_local_IP_address/test1.php](http://your_local_IP_address/test1.php)

or

> [http://localhost/test1.php](http://localhost/test1.php)

My sample test1.php contains the code below:

> <? phpinfo(); ?>

---

### Post by ciborium on 2009-01-16
Thank you, for some reason I skipped that part.

http://<my ip address>/test.php worked just fine.  I still wish I could use the right-click method but... At least it works.

---


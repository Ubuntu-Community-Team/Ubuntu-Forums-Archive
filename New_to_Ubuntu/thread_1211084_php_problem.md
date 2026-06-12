---
title: "php problem"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by chettiyar on 2009-07-12
My php codes in html file are not processed. All the items inside <html> and </html> except those within <php and ?> are processed. No error message also shown. Can anybody help???
I get the following error message when I try to restart apache.
apache2: Could not reliably determine the server's fully qualified domain name, using XXX.X.X.X for ServerName (in the place of X digits appear).  Is this the reason for php problem????

---

### Post by credobyte on 2009-07-12
No, that's not the case ( tough, you can fix it by adding [COLOR=Green]ServerName myserver[/COLOR] to [COLOR=Green]/etc/apache2/apache2.conf[/COLOR] ).

Try this :
```
sudo apt-get install php5 libapache2-mod-php5
```

---

### Post by s.fox on 2009-07-12
Hi,

PHP code should be contained within these tags like this:
```

<?php

echo "This works";

?>
```

If your HTML page contains ANY php it will need to be saved with php extension.  If you are getting an error is it possible for you to post the php script for us to look at?  

Thanks,

-Silver Fox

---

### Post by chettiyar on 2009-07-12
Dear Silver_fox_
nobody ever told me abt renaming the file as .php.  when i renamed and tried to open with firefox it says - you hav chosen to open a php file from ...... directory, what should firefox do with this file - open with/save file.  which appln should i select in open-with and from which directory???  thanx in advance.

---

### Post by credobyte on 2009-07-12
> **chettiyar said:**
> Dear Silver_fox_
nobody ever told me abt renaming the file as .php.  when i renamed and tried to open with firefox it says - you hav chosen to open a php file from ...... directory, what should firefox do with this file - open with/save file.  which appln should i select in open-with and from which directory???  thanx in advance.

You can't open .php file with Firefox directly ! You need to upload it to your server ( apache2 ). If you do not have one, follow this guide : [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Copernicus1234 on 2009-07-12
> **chettiyar said:**
> Dear Silver_fox_
nobody ever told me abt renaming the file as .php.  when i renamed and tried to open with firefox it says - you hav chosen to open a php file from ...... directory, what should firefox do with this file - open with/save file.  which appln should i select in open-with and from which directory???  thanx in advance.

Php is code that runs on a webserver and the results of the code execution gets delived to your web browser. Thats why you cant run it directly in the browser. Its a server side language. :)

if you want a client side language that runs in the web browser, try JavaScript. :)

---

### Post by Wim Sturkenboom on 2009-07-12
> **Silver_fox_ said:**
> If your HTML page contains ANY php it will need **to be saved with php extension**.  If you are getting an error is it possible for you to post the php script for us to look at?  
Must be an Ubuntu specific requirement. It might be advisable but it is not required.

As reference a quote from [http://osdir.com/ml/php.general/2002-05/msg01167.html:](http://osdir.com/ml/php.general/2002-05/msg01167.html:)
> 
Your apache on linux must be configured to parse .html files through php
while your apache on your noteb.. must not, in your apache's httpd.conf
look for the foll. line:
AddType application/x-httpd-php4 .php
AddType application/x-httpd-php4 .phtml
so if you want to parse html files thru php add:
AddType application/x-httpd-php4 .html


Note: you must just search for those addtypes because the may be in another file when using Ubuntu.

---

### Post by Celauran on 2009-07-12
> **Wim Sturkenboom said:**
> Must be an Ubuntu specific requirement. It might be advisable but it is not required.

As reference a quote from [http://osdir.com/ml/php.general/2002-05/msg01167.html:](http://osdir.com/ml/php.general/2002-05/msg01167.html:)


Note: you must just search for those addtypes because the may be in another file when using Ubuntu.

With PHP and Apache installed, they'll be in /etc/apache2/mods-enabled/php5.conf

---

### Post by chettiyar on 2009-07-12
dear credobyte,
seems ur suggestion solved the problem. thanq very much

---


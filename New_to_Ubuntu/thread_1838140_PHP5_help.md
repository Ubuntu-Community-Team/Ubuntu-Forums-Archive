---
title: "PHP5 help"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by gupta_sumesh63 on 2011-09-03
I installed apache2.2.20 using -prefix=/usr/local/apache2 from source i.e all files of apache2 are in /usr/local/apache2.

Then I installed php5 with sudo apt-get install php5. That has got installed in /etc I think. To test php5 installation I created a file phpinfo.php in the local host containing the following:


[PHP]<?php phpinfo() ?>[/PHP]

After saving I chmod it to a+rx.

Now when I run [http://localhost/phpinfo.php](http://localhost/phpinfo.php), the page shows 

[PHP]You are forbidden to access this site on this server.[/PHP]

Can any one help me to solve the issue? Maybe the config is wrong? Or installation of php is wrong. Thanks in advance.:confused:

---

### Post by cariboo on 2011-09-04
Is there a reason you didn't install apache2 from the repositories? If it was just because of security updates, apache2 is updated without incrementing the version number. Php5 probably isn't working because you installed apache2 to a non-default location, you may have to check the various php.ini files to see it it is pointing to the correct location.

---

### Post by gupta_sumesh63 on 2011-09-04
Thank you very much. I reinstalled apache2 from repos. Now everything is working fine.

---


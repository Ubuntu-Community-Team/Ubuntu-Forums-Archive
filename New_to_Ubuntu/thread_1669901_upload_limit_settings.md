---
title: "upload limit settings"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by duceduc on 2011-01-18
I have set my php.ini file to limit my uploads, but I still cannot upload files more than 40mb. Here is what I have set the following lines to.

> memory_limit = 128M
post_max_size = 1024M
upload_max_filesize = 1024M

I also checked my settings by creating a file with the these lines.
> <?php
phpinfo();
?>
The apache have been restarted and I also have rebooted the server as well.

---


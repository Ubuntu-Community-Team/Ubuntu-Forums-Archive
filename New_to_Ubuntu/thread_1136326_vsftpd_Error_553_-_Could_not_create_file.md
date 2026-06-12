---
title: "vsftpd Error 553 - Could not create file"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by ubuntuforums on 2009-04-24
Hi. I setup a virtual host so that I can access /var/www/ from /home/username/www/

When I login to my ftp it brings me to /home/username/

I can upload and delete files there. But I cannot rename or delete the /www/ folder.

In /home/username/www/ I cannot upload, create, or delete any files, if I try to I receive an error like '553 - Could not create file'.

I connect to my server solely through ssh, so I need to know how to fix my user permissions through the terminal.

Thanks for any help.

---

### Post by ubuntuforums on 2009-04-25
Fixed by giving my user ownership of the directory: chown -R usernamehere /dir/here/

---


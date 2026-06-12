---
title: "function move-uploaded-file"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by take4 on 2009-08-10
I hope that I am submmiting this to the correct forum.  I am new to using ubuntu.  During my installation, I installed lamp do work on learning php development.  However I have a problem with one portion of code from my books tutorial.

This is the error which I recieve:
**Warning**:  move_uploaded_file(images/phizsscore.gif) [[function.move-uploaded-file]("http://localhost/headfirst/ch05/function.move-uploaded-file")]: failed to open stream: Permission denied in **/var/www/headfirst/ch05/addscore.php** on line [B]30

I have changed the permissions on /var/www/headfirst/ch05 so that user, group and others have read, write and exicute permissions.  I am lost why I still have this permission denied issue if anyone can point in the direction to solve this issue.  

Thank you
[/B]

---

### Post by synapsys on 2009-08-10
Maybe the problem is with the file and not the folder. Did you use the -R switch to recursively change permissions for the folder and all files it contains?

---


---
title: "XAMPP/phpMyAdmin: 1045: Access denied for user '[root]'@'localhost' (using password.."
date: 2010-11-09
forum: New to Ubuntu
---

### Post by flameproof on 2010-11-09
I get sooo annoyed, every time I install XAMPP on Windows or Ubuntu (or now Xubuntu) I get when I type [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)  sooner or later

1045: Access denied for user '[root]'@'localhost' (using password....

Then I forget how to fix it and search, search search and finally reinstall XAMPP. But it's actually very easy to fix:

> 1. Open config.inc.php file in the phpmyadmin directory 

2. Find line 21: $cfg['Servers'][$i]['password'] = ''

3. Change it to: $cfg['Servers'][$i]['password'] = 'your_password';

4. Restart XAMPP

This should often work in Windows and Linux.

PS: I just post it here so I know where to look and find it next time.

---

### Post by J V on 2010-11-09
And you call yourself flameproof?

---


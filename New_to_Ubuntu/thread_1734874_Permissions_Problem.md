---
title: "Permissions Problem"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by ChuckLeJam on 2011-04-20
New to Linux.
I installed the XAMPP package
and used the Security program to  establish passwords for all the components.
I wanted to run the sample application cds and got an error because of the password.
I attempted to edit the ~/opt/lampp/htdocs/xampp/cds.php file to fix the password.
Although the file is owned by root and I am logged in as root I am not able to modify the file
nor can I change the permissions.
Help!

---

### Post by LOIREE on 2011-04-20
Stupid question, have you tried:
sudo ~/opt/lampp/htdocs/xampp/cds.php ?

On the other hand, path seems strange. ~ you mean opt lays under /home/root ? Shouldn't it be under /opt instead? Not sure if it is editable there.

---

### Post by ChuckLeJam on 2011-04-20
I am sorry.
You are absolutely right, the path is
/opt/lampp/htdocs/xampp

and I am able to open the cds.php file using gedit but it is read-only.

I did attempt
sudo cds.php
after entering my password
I get a message saying that roo is not in the sudoers file!??

---

### Post by ttshivers on 2011-04-20
This article might help you add the user to the sudoers file: [https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers")

---

### Post by deconstrained on 2011-04-20
No need to sudo as root, it's redundant. As long as your username (or one of the groups you belong to) is in the sudoers file (i.e. %admin ALL=(ALL) ALL for the group 'admin') you can just run sudo as yourself.

---

### Post by ttshivers on 2011-04-20
> **ChuckLeJam said:**
> 
I get a message saying that roo is not in the sudoers file!??

Wait is it roo or root?

---

### Post by ChuckLeJam on 2011-04-20
OK.
I was able to do
sudo gedit cds.php

which allowed me to modify the file, save it,
and now it runs correctly with the new password.

Regarding roo vs root: the username is root but roo seems to be used as a nickname!

Thank you all very much for your assistance.
One day I hope to know enough to help some other newbie.

Until next time,
ChuckLe...

---


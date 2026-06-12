---
title: "could not open a copied file"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by nora.erdm on 2009-06-11
hi all
I installed php5, mysql and apache2 on my ubuntu.
And I copied a folder file to var/www to set up by using php.
But I could not open that copied file. It says an error "The folder contents could not be displayed. You do not have the permissions necessary to view of contents of "filename". "
I don't know why.
Please help me.

nora.erdm

---

### Post by nora.erdm on 2009-06-11
bbb

---

### Post by abhiroopb on 2009-06-11
Anything that is placed in folders OTHER than in the /home folder requires sudo root access.

in a terminal type in:

sudo gedit /var/www/filename

---


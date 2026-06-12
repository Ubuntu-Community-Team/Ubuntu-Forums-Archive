---
title: "Help - I've lost my login!!"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by stevebond001 on 2009-05-21
Hi
I've got myself in a bit of a state and need some help to get me out of it.
I've just changed my login screen and now when I boot my PC I get the error message:
"The greeter application appears to be crashing. Attempting to use a different one" with an OK button.

When I click on OK it just stays in a loop and I can't login.
I've googled this and found a suggestion to amend the /etc/gdm/gdm.conf-custom file, but can't locate the required file to change.

Has anybody got any idea on how to fix this.  I really really don't want to have to reinstall Jaunty, as I've only just got it to how I want it.

Any suggestions would be greatly appreciated.

Many thanks in advance

---

### Post by finer recliner on 2009-05-21
where is the tutorial you're getting these instructions from? I'd like to verify you're following it correctly.

---

### Post by stevebond001 on 2009-05-21
This is the article that I found:
[http://liltux.wordpress.com/2007/09/05/how-to-fix-the-error-the-greeter-application-appears-to-be-crashing-in-ubuntu/](http://liltux.wordpress.com/2007/09/05/how-to-fix-the-error-the-greeter-application-appears-to-be-crashing-in-ubuntu/)

---

### Post by sim-value on 2009-05-21
Did you do Backups of the files you changed ?

---

### Post by stevebond001 on 2009-05-21
No I didn't do any backups, as all I was changing was the login screen.

---

### Post by finer recliner on 2009-05-21
does this file exist: /etc/gdm/gdm.conf ?

try editting that one

---

### Post by stevebond001 on 2009-05-21
Yes I've managed to open this file (in nano).  What do I need to edit?

---

### Post by finer recliner on 2009-05-21
comment out the line that your tuturial suggested by inserting a '#' at the beginning of the line (no quotes though)

---

### Post by stevebond001 on 2009-05-21
That line does not exist in this file.

I've found a line:
Greeter=/usr/lib/gdm/gdmgreeter

Could I replace "gdmgreeter" with "gdmlogin" ?

---

### Post by stevebond001 on 2009-05-21
Hi
An update.

I amended the line as I suggested and when I rebooted it gave ma a standard Debian gui logon screen.  I was then able to login and reset my logon screen back to the default one.

Thank you very very much for your help with this - it is much appreciated.:p:p:p

---


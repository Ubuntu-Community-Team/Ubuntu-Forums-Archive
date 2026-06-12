---
title: "Vendetta Install Trouble"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by myolbug on 2009-04-04
I cannot get this installed: vendetta-linux-amd64-installer.sh

I tried to follow the directions on the install page, i.e. sh ./vendetta-linux-x-installer.sh but when I do this all I get is this: sh: Can't open ./vendetta-linux-x-installer.sh

I have read their forum but I cannot get it to install.

What should I do?

I have an AMD 64 X2 4400+ dual core with Ubuntu 8.10 64 bit and I downloaded the 64 bit version.  I am stuck.

---

### Post by taurus on 2009-04-04
You're supposed to type in the exact name of the file, replacing the x with amd64.

```
sh ./vendetta-linux-amd64-installer.sh
-or-
sudo sh ./vendetta-linux-amd64-installer.sh 
(If you need root privilege.)
```
Of course, make sure you are in the directory where that file is.

---

### Post by myolbug on 2009-04-04
> **taurus said:**
> You're supposed to type in the exact name of the file, replacing the x with amd64.

```
sh ./vendetta-linux-amd64-installer.sh
-or-
sudo sh ./vendetta-linux-amd64-installer.sh 
(If you need root privilege.)
```
Of course, make sure you are in the directory where that file is.

I have tried this but nothing happens.  This is the reason for the post.

---

### Post by taurus on 2009-04-04
Nothing happens as it drops you back to a prompt?  

What was the exact command did you run since the one you posted was wrong, sh ./vendetta-linux-**[COLOR="Red"]x[/COLOR]**-installer.sh?

---

### Post by myolbug on 2009-04-07
> **taurus said:**
> Nothing happens as it drops you back to a prompt?  

What was the exact command did you run since the one you posted was wrong, sh ./vendetta-linux-**[COLOR="Red"]x[/COLOR]**-installer.sh?

randy@randy-desktop:~$ sudo '/home/randy/vendetta-linux-amd64-installer.sh' 
sudo: /home/randy/vendetta-linux-amd64-installer.sh: command not found


What now?

---

### Post by myolbug on 2009-04-07
Google is my friend.  I should have tried it first.  Oh Well.  This thread gave me the answer: [http://ubuntuforums.org/showthread.php?t=433036](http://ubuntuforums.org/showthread.php?t=433036)

---

### Post by myolbug on 2009-04-07
I thought that I had it, all I have is an icon that says it is an executable (application/x-executable)
located in home.randy/bin

So, what now?

---

### Post by myolbug on 2009-04-08
Anyone?  What is my next step?

Found the answer.  I needed to check Execute in the Properties>Permissions tab of the icon.  Then it is a simple matter of double clicking the icon.

---

### Post by JoshuaRL on 2009-04-08
> **myolbug said:**
> Anyone?  What is my next step?

Found the answer.  I needed to check Execute in the Properties>Permissions tab of the icon.  Then it is a simple matter of double clicking the icon.

And there you have the reason that, where possible, always use applications from the repos or .deb's from respectable places.  It isn't possible in this case, but you see how it can get confusing pretty fast.

---


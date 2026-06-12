---
title: "fwbuilder...and just for fun, a second life."
date: 2011-01-21
forum: New to Ubuntu
---

### Post by philodice on 2011-01-21
I'm feeling fairly comfortable with Ubuntu.  For me that's when I usually wade into something I'm not ready for.  Fwbuilder 4.0 looked fun and easy, but when I try to compile and install based on template one, it fails.  I'll get busy reading the 484 pg manual...but does anyone have any helpful hints?

I'm also planning to install "a second life' viewer.  Are the instructions here up to date?

[http://wiki.secondlife.com/wiki/Compiling_the_viewer_%28Linux%29](http://wiki.secondlife.com/wiki/Compiling_the_viewer_%28Linux%29)

---

### Post by 123456789123456789123456 on 2011-01-22
you says it fails, what errors are you getting, is it a supporting package error?

---

### Post by philodice on 2011-01-22
I make a folder, name it, select fwbuilder template 1, compile works, then when I click install it fails.  I am guessing the template settings are wrong somehow.

---

### Post by mikehorn on 2011-01-22
Firewall Builder uses SSH / SCP to install and run the firewall script on the target firewall, even if the firewall you are configuring is local.  You need to have a user account setup that has appropriate sudo permissions to run the firewall script since many commands require root privileges.  Here's a link to the guide that explains how to do this:

[http://www.fwbuilder.org/4.0/docs/users_guide/install_with_regular_user.html](http://www.fwbuilder.org/4.0/docs/users_guide/install_with_regular_user.html)

If you follow the instructions above, make sure to set the firewall script directory to /etc/fw in the firewall settings (Double-click on the firewall, Click on the Firewall Settings button, click the Installer tab and set the directory in the first field).  Note, this directory needs to exist on the server.

---

### Post by philodice on 2011-01-29
> **mikehorn said:**
> Firewall Builder uses SSH / SCP to install and run the firewall script on the target firewall, even if the firewall you are configuring is local. You need to have a user account setup that has appropriate sudo permissions to run the firewall script since many commands require root privileges. Here's a link to the guide that explains how to do this:
 
[http://www.fwbuilder.org/4.0/docs/users_guide/install_with_regular_user.html](http://www.fwbuilder.org/4.0/docs/users_guide/install_with_regular_user.html)
 
If you follow the instructions above, make sure to set the firewall script directory to /etc/fw in the firewall settings (Double-click on the firewall, Click on the Firewall Settings button, click the Installer tab and set the directory in the first field). Note, this directory needs to exist on the server.
 
I will try that tomorrow.  I won't be getting much computer time at home for a while.  Husband wants to make music on his new Ubuntu programs that he's never played with.

---


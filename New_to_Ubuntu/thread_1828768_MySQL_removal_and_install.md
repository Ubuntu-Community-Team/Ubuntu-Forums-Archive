---
title: "MySQL removal and install"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by hpng on 2011-08-19
10.04LTS, HP laptop

I installed and uninstalled mySQL using Synaptic Package manager.
I still see            /etc/mysql and            /etc/mysql/my.cnf in the folders.
I thought uninstall would uninstall everything.

I have to uninstall because I forgot my password.

So, if one forget the password, how do I recover it?

Now, when I reinstall it, it does not ask me for the passward during installation.
So I am wondering if I better delete all things associated with mysql install and start over.

Summary:
Issue#1:
I need to install MySQL, and also need to setup password and user name, but there exist remnants of previous MySQL install that makes the installer think I do not need new account setup for MySQL.  How do I make a new administrator and user accounts on mySQL server?

Issue#2:
Does any know of a good tutorial using C++ and MySQL?

Cheers and thanks

---

### Post by Wim Sturkenboom on 2011-08-19
Did you just mark for uninstallation or mark for complete removal? Might make a difference.

And [http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html) to 'reset' the root password. You probably could have searched bit on the web ;)

---


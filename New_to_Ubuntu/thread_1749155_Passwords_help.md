---
title: "Password/s help"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by sbmmm on 2011-05-04
Definitely a beginner here...I used to have a great sysadmin who set up my LAMP server with Ubuntu 10.04.  Now, he is unavailable and I really need to change passwords for 


[LIST]
[*] Root
[*]sudo account ( I also use this ssh)
[*]Mysql
[*]PhpMyAdmin
[/LIST]
 
1. For security reasons, my sysadmin set up my ssh access on a non-standard port.  Will changing the password/s for root or sudo affect access configuration or my ability to access? 

2.This may be partly a Mysql management question...Currently the Mysql and PhpMyAdmin have the same access passwords (both using root for username), is this by default?  Also, should individual db have different passwords?  BTW, I do see in PhpMyAdmin there is a privileges tab and under my primary db, full privileges are given to root. 

3. I also have the Webmin CP.  Could I use Webmin settings to change needed passwords vs. using Command Line in PuTTY?  I am getting more comfortable with PuTTY, but just asking.

Thank you for any help.

---

### Post by spikoley on 2011-05-06
The command to update a password is *passwd*.  With Ubuntu you do not set a [root password]("https://help.ubuntu.com/community/RootSudo"), but it can be done.  I would check with the guy who set it up before messing with the root password.

To change the sudo account password use this command.

```
sudo passwd <user name>
```

I am not sure about changing the other passwords.  Hopefully, somebody else can answer that for you.

---


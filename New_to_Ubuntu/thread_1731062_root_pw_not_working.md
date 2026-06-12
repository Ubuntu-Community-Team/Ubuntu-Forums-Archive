---
title: "root pw not working"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by zachery on 2011-04-16
ok guys so basically what i have is ubuntu server 10.10 and i installed the gui desktop so my family could use it well since i installed the gui my root pw doesnt meaning i cant go 

su and login

and i can not login to root to anything

im trying to install my printer lexmark pro 901 and i cant do it without that pw

did something reset when i installed the desktop? or is there anything i can do?

---

### Post by fabricator4 on 2011-04-16
> **zachery said:**
> ok guys so basically what i have is ubuntu server 10.10 and i installed the gui desktop so my family could use it well since i installed the gui my root pw doesnt meaning i cant go 

su and login

and i can not login to root to anything

im trying to install my printer lexmark pro 901 and i cant do it without that pw

did something reset when i installed the desktop? or is there anything i can do?

Did you have a root password previously, and do you have a user with admin rights?  The default for Ubuntu, even server (I think) is to have the root account disabled and the default user setup is an admin one.

More information [here]("https://help.ubuntu.com/community/RootSudo").

Chris

---

### Post by zachery on 2011-04-16
well i had to login to su or do sudo to run things before but the account i am on is in the admin group but none of my pws work for the authentication part my old or new pw

---

### Post by fabricator4 on 2011-04-16
> **zachery said:**
> well i had to login to su or do sudo to run things before but the account i am on is in the admin group but none of my pws work for the authentication part my old or new pw

You can can't login as root "su root" because there is no root login, only the admin one you are on at the moment.

The work arounds are listed in that tute that I linked to.  Most things can be done, but not "su root".

Unless you're saying that your admin login password is no longer working?

Chris

---

### Post by zachery on 2011-04-16
well the authentication pw is no longer working

---

### Post by fabricator4 on 2011-04-16
> **zachery said:**
> well the authentication pw is no longer working

The authentication password for sudo under the administrator login is the one you used to login with.

The root login is disabled by default.  Installing Gnome should not have changed anything.  If you really want a root login you can enable it simply by changing the password.  Make it a hard one and don't use the root login for anything except admin tasks and log out immediately.

sudo can be used for almost anything including changing the root password (passwd command) however, and it's the advised method for administering the system.

Chris

---

### Post by oldos2er on 2011-04-16
Try this to reset a password: [http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---


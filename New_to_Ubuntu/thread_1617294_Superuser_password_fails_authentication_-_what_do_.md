---
title: "Superuser password fails authentication - what do I do now?"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-11-09
Hello:

I upgraded from 10.04 to 10.10 using the update manager.

When I type 'su' in a terminal my password fails authentication.

I have only have one password and always use the same one.

I am certain that, while my system was 10.04, I could 'su' successfully.

I know that you rarely use 'su' but I don't like the fact that I can't.

Any ideas on how to fix this would be appreciated,

---

### Post by bioterror on 2010-11-09
> **Robert.Thompson said:**
> Hello:

I upgraded from 10.04 to 10.10 using the update manager.

When I type 'su' in a terminal my password fails authentication.

I have only have one password and always use the same one.

I am certain that, while my system was 10.04, I could 'su' successfully.

I know that you rarely use 'su' but I don't like the fact that I can't.

Any ideas on how to fix this would be appreciated,

when you say 'su' it means you're trying to login as a 'root', that's disabled in Ubuntu by default.

You can try to say 'sudo passwd root' and change the root password (enable).

'sudo su' should also work.

---

### Post by webtechquery on 2010-11-09
Check out the following post for ur solution:

[http://www.webtechquery.com/index.php/2010/06/ubuntu-root-password-ubuntu-root-login/](http://www.webtechquery.com/index.php/2010/06/ubuntu-root-password-ubuntu-root-login/)

---

### Post by CharlesA on 2010-11-09
I would suggest everyone read the sticky here: [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

In Ubuntu, the root account is disabled by default so you can't use su, you use sudo instead.

---

### Post by mcduck on 2010-11-09
> **Robert.Thompson said:**
> Hello:

I upgraded from 10.04 to 10.10 using the update manager.

When I type 'su' in a terminal my password fails authentication.

I have only have one password and always use the same one.

I am certain that, while my system was 10.04, I could 'su' successfully.

I know that you rarely use 'su' but I don't like the fact that I can't.

Any ideas on how to fix this would be appreciated,

Like said, "su" would ask for target user's password, while Ubuntu's security model has root user disabled and admin tasks are instead done using "sudo".

If you want to open a root session in shell, "sudo -i" is what you are looking for. ("sudo su" and "sudo -s" basically work as well, but don't load root user's environment correctly which can result is some troubles).

Enabling the root user is of course possible, but it's highly unrecommended and not really necessary for anything. (by the way, it's not encouraged to post instruction for doing that in the beginner section of the forums, especially without fully explaining what it does and the possible consequences).

Anyway, this page pretty much explains it all: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

edit: too slow. :D

---

### Post by Robert.Thompson on 2010-11-09
Thanks to all of you for your help and advice. :)

---


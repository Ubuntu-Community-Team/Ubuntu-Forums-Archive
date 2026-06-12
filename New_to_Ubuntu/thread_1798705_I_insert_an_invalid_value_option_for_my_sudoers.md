---
title: "I insert an invalid value option for my sudoers"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by -em- on 2011-07-06
I edit my sudoer in a consol by visudo.
I thought I could set my passwd_timeout to a value less then 1min... apparently no ! 
I did the same mistake for my timestamp_timeout[B].
[/B]
Here's my prompt when trying to be in root by sudo su:
[I]
[COLOR=DimGray]em@myPC:~$ sudo su
sudo: value `0.2' is invalid for option `passwd_timeout'
[sudo] password for root: [/COLOR][/I]


So I thought I could we wise and try to connect by su:
Here's my prompt when trying to be in root by su:

[COLOR=DimGray][I]em@myPC:~$ su
Mot de passe : 
su : Échec d'authentification
em@myPC:~$ [/I]
[/COLOR]
I don't know how to fix the problem, 
since I can no longer connect my self in root to edit the file...
:confused:

---

### Post by -em- on 2011-07-06
I forgot to say, my root password is no longer recognize...

---

### Post by werty2010 on 2011-07-06
the tread is kind of old but i think this is what your looking for: 
[http://ubuntuforums.org/showthread.php?t=229309](http://ubuntuforums.org/showthread.php?t=229309)

---

### Post by idoitprone on 2011-07-06
If I may add, boot to recovery mode. It is a way to cirumvent the file permission and allow you to edit files owned by root. werty2010 nice link

---

### Post by -em- on 2011-07-06
So, I think the next step is to change the file by booting on a liveCD or recovery mode... pfffff ! :(

---

### Post by werty2010 on 2011-07-06
> **idoitprone said:**
> If I may add, boot to recovery mode. It is a way to cirumvent the file permission and allow you to edit files owned by root. werty2010 nice link

thank you  :)

---


---
title: "MySQL root problems"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by synicalx on 2009-10-30
Hey all,

I installed 9.04 a week or so ago and I've decided to follow some simple tutorials on whatever I can find. So far it's all gone fine but the latest one I've tried is a "DIY twitter client in PHP" from a Linux User magazine. Everything needed (apache, PHP 5, MySQL) all installed fine through synaptic but once I tried to fire up MySQL using this command;

           mysql -u root -p

It starts asking for a root password. The magazine mentions it will do this and suggests referring to the distro documentation for the root password - which doesn't seem to exist. Of course I'm a total Linux noob so it's quite likely I've overlooked something really obvious here, but if anyone can lend me a hand or point me in the right direction I'd be really grateful :D

---

### Post by nakama85 on 2009-10-30
> **synicalx said:**
> Hey all,

I installed 9.04 a week or so ago and I've decided to follow some simple tutorials on whatever I can find. So far it's all gone fine but the latest one I've tried is a "DIY twitter client in PHP" from a Linux User magazine. Everything needed (apache, PHP 5, MySQL) all installed fine through synaptic but once I tried to fire up MySQL using this command;

           mysql -u root -p

It starts asking for a root password. The magazine mentions it will do this and suggests referring to the distro documentation for the root password - which doesn't seem to exist. Of course I'm a total Linux noob so it's quite likely I've overlooked something really obvious here, but if anyone can lend me a hand or point me in the right direction I'd be really grateful :D

By default no root password is set. You will need to set one in the users section. Or you could use sudo instead

go to --System-->Admin-->Users/Groups

select root and click the little key chain-- enter the password you set up ubuntu with 
----properties---
then add a password.

just don't forget it

---

### Post by synicalx on 2009-10-30
Thanks!

Worked well until I got an error due to MySQL not installing properly, but [this]("http://ubuntuforums.org/showthread.php?t=1008273&page=2") fixed it right up.

---


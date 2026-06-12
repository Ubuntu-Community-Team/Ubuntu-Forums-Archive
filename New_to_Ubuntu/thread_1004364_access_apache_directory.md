---
title: "access apache directory"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by eng.reem on 2008-12-07
hey all,i recently downloaded lamp server ,i installed apache
,php,mysql using terminal code
the problem is when i try to access the www directory i'm not allowed to
edit files delete them , or to write a php code and save it,
then when i tried to extract .php files in www directory i got
that message :
"You don't have the right permissions to extract archives in the folder "file:///var/www"
any help plz ..?

---

### Post by spikoley on 2008-12-07
You need to have root permissions to save to directories that you are not the owner of or in the group.  Use [sudo and gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") in front of your commands.  Hopefully somebody else can explain the proper permissions you should set up for the www folder.  My guess is to make it owned by the user who will be managing it, but you should find out for sure for security reasons.

---

### Post by gettinoriginal on 2008-12-07
Found this, hope it helps

[http://sudan.ubuntuforums.com/showthread.php?t=892510](http://sudan.ubuntuforums.com/showthread.php?t=892510)

---

### Post by dannytatom on 2008-12-07
Since it's usually best to keep permissions as their set, I just run 'sudo nautilus' and edit the files through that.  Not sure if it's the best idea, but it works.

---


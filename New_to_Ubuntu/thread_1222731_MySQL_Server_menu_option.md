---
title: "MySQL Server menu option"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by edster99 on 2009-07-25
Hi 
I have installed XAMPP 1.7.1 on my system (9.0.4) from [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html).  Everything works fine.  But - I have got a menu option appeared on the main menu (the one for Logoff/Restart etc) titled MySQL Server.  When I click on it, I get a GUI logon screen, which just asks for a password. At the moment, I only have 2 passwords that I use, but neither of those lets me log in.  After 3 attempts, I get asked for a username and password.  If I use root, I get a message 'The system administrator is not allowed to log on to this session'.  I have some options in the bottom left - Select Session, Select Language, Remote Login via XDMCP, plus Quit,Shutdown, Restart etc.
As far as I can work out, this is the 'Local' login window. 

Can anyone tell me what this is/ how it works?  I have looked on the mySQL site, the XAMPP site and here, and cant work it out.  It would be nice to think I could log straight into a MySQL session, but it doesnt seem to happen.

Thanks
Ed

---

### Post by yeats on 2009-07-25
I would suggest going to System -> Preferences -> Main Menu and posting back the command that that menu option is performing.  Post it here and someone can provide some feedback.

---

### Post by edster99 on 2009-07-25
Hi Chris

I dont have that menu on the 'menus' option, only the 'Applications' and 'System' menus.  The logout/restart menu isnt on there. Is it somewhere else that I can access?

I've realised that it is a description for a user called mysql, so not what I thought! The user doesnt have a home directory, so cant really log in, but at least I've worked it out. 

thanks

---


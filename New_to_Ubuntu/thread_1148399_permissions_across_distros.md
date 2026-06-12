---
title: "permissions across distros"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by tchoklat on 2009-05-04
I have transferred the contents of my /home directory to another distro for a trial - in this case a Ubuntu derivative, #!crunchbang. I am stuck with an issue over permissions with lot's of things owned by /root requiring sudo to use. Using the terminal, what command do I need to recursively change the ownership to me, tony?


tony!

---

### Post by LowSky on 2009-05-04
hope this helps
[http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

---

### Post by tchoklat on 2009-05-04
I've plundered through this and think I have got it with the command;

tony@tony-crunchbang:~$ sudo chown tony /home/tony -R

To change the ownership of my home directory to me, tony!

thanks

---


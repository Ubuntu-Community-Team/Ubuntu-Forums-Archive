---
title: "File System cant be access"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by anakramli on 2011-01-22
Hi there, im an absolute beginner for ubuntu os. Just installed for few weeks. n liking it :) 
Anyway my prob was. i was trying to install drupal 7.0 on ubuntu everything went fine until i discovered that IM NOT ALLOWED to edit my FILE SYSTEM. for example i have to put my drupal file in /var/www.. but i cant... 
ive tried to configure the permission of this file system. it says that im not the user so i cant. very weird.. i help all of u can help me to figure out this problem :) thanks!!

---

### Post by vanadium on 2011-01-22
Do not install a content management system if you have no proficiency about the system. Ask/pay someone who has some system knowledge, or give yourself the time to become acquainted with some basics of a linux system.

---

### Post by JKyleOKC on 2011-01-22
The problem is that you've run into one of the main reasons that Unbuntu and all other *nix systems are so much more secure than most of the other operating systems. An ordinary user is not allowed to make major system changes -- which means change of anything outside of that user's home directory. Only the "superuser" is allowed to do that.

Search the forums for "sudo" and "security" to get the details. There's a simple way to do what you want, but you need to know all of the implications of it first, to keep your system secure.

Drupal is a good system; I've used it. However I personally found "whizzywig" to be much easier to use. And there are many more from which you can choose -- but all will run into the security walls, so you need to study those details first.

---


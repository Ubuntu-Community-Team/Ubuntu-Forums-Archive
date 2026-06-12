---
title: "Allow user to access /var/www/"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by faviouz on 2011-06-22
Hi,

I am running Lubuntu 11.04 and since I installed Apache/MySQL/PHP5, I have to login as root everytime and either type in gksudo or use the terminal in order to create, move or delete files and folders inside the /var/www/. Having that said, I would like to grant my user account access to this folder, so I can just place a shortcut in my desktop and then be able to create, move or delete files and folders as I would usually do.

Thank you.

---

### Post by bodhi.zazen on 2011-06-22
For security purposes it is best to keep those files owned as root.

If you must, see man chmod

---

### Post by doas777 on 2011-06-22
ok, my take on it is, when you are deploying material to your website, that is clearly an administrative action, so the person posting the code, shoudl be required to take root, perform their tasks, and then release root again prior to testing. 

but it seems like many web devs disagree, so my recommendation is to add yourself to teh www-data group, and use setgid/setuid on /var/www/. that way you can create fils in the directory, but they will automatically change ownership to www-data:www-data. setuid can be a vulnerability, but since the files will already be executed by www-data anyway, its basically the same.

---

### Post by faviouz on 2011-06-22
Thanks both of you for your help!

I am aware of the security risks, but I am not running a web server here. It's just a local environment where I deploy PHP applications or test existing ones. Regardless, I managed to get it working.

---

### Post by Wim Sturkenboom on 2011-06-22
Why not let apache serve from /home/yourname/www or something similar instead of from /var/www ? A lot easier than risking things by modifying permissions, at least in a Slackware setup (don't know about Ubuntu).

As long as Apache only has to read, there are no issues as long as it has permission to read the directory (which is usually the case). Apache can not write in your home directory and I use ACL to solve that.

@doas777
Maintaining websites is not a root activity in my opinion.

---

### Post by doas777 on 2011-06-22
> **Wim Sturkenboom said:**
> 
@doas777
Maintaining websites is not a root activity in my opinion.
we'll have to agree to disagree on that one. 

@op, I'm glad you got it running to your taste. in the end, that is all that matters.

---


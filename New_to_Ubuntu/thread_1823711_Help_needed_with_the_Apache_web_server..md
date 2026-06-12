---
title: "Help needed with the Apache web server."
date: 2011-08-12
forum: New to Ubuntu
---

### Post by thankyoutoomuch on 2011-08-12
[FONT=Times New Roman][SIZE=3]I installed the apache web server but I can’t change the index file in www because it belongs to root. How can I change it so it belongs to me? Or is there some other way that I can put my own content up without changing the permission I can’t figure out how to log in as root except in the terminal, but I can’t find my way around in the terminal yet. Is there a graphical program that will let me do this? I tried KompoZer but it wont let me make the changes either.[/SIZE][/FONT]

---

### Post by ~!geek!~ on 2011-08-12
If your web projects are for local machine and one or two users including you, you may own the www directory safely. 
To do this: 
> sudo chown <yourusername> /var/www -R
Now the directories and files within www belong to you.

---

### Post by thankyoutoomuch on 2011-08-12
> **~!geek!~ said:**
> If your web projects are for local machine and one or two users including you, you may own the www directory safely. 
To do this: 
 
Now the directories and files within www belong to you.
 
Yes it is just for me to develop websites that I will put on a server on the web later once I get them working the way I want.  Thanks. :)

---


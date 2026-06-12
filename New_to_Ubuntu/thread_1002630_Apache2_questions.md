---
title: "Apache2 questions"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by TripitakaUK on 2008-12-05
I have searched...and searched..and searched before I posted.

I have Hardy desktop and I have managed to get apache2 installed and running on it. I thought that there may have been a "How-to" on this but I can't find one - if anyone knows the location, could you let me know?

Anyhow, it's running. I want to post a test page up and it would seem that the place where the files are stored is /var/www but I do not have permissions to sve files to that directory. Is that normal? Surely I dont have to sudo nautilus or sudo cp to get the files in there? Am I doing something wrong?

---

### Post by stefangr1 on 2008-12-05
> **TripitakaUK said:**
> I have searched...and searched..and searched before I posted.

I have Hardy desktop and I have managed to get apache2 installed and running on it. I thought that there may have been a "How-to" on this but I can't find one - if anyone knows the location, could you let me know?

Anyhow, it's running. I want to post a test page up and it would seem that the place where the files are stored is /var/www but I do not have permissions to sve files to that directory. Is that normal? Surely I dont have to sudo nautilus or sudo cp to get the files in there? Am I doing something wrong?

Yes, it is. you have to run "sudo chown <yourusername> /var/www" to get the right permissions.

---

### Post by ibutho on 2008-12-05
The behaviour you mentioned is normal. You can change the user and group permissions of the directory and give yourself read and write permissions. If this is a development server, you can enable the apache2 userdir feature. You will then be able to save webpages to somewhere like /home/user/public_html and access the pages by doing something like [http://localhost/~user/somepage.html](http://localhost/~user/somepage.html).

It may help if you look at the apache documentation and the [apache section]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html") in the Ubuntu Server Guide.

---

### Post by TripitakaUK on 2008-12-05
Thanks for the replies. I wasn't sure if I would break apache doing chown - Lord knows, I've broken Ubuntu so many times over the last three weeks but always managed to fix it due largely to the help on these forums.

Still amazed that there isn't a noob "How to" for apache though.

---


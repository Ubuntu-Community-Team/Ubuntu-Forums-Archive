---
title: "[SOLVED] please help - how to add a forum to my site"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by gnulogic on 2008-04-08
I was trying to put a forum on my site that i host from home using apache and hardy heron.  what is the best free forum software?  And what exactly do you do to set it up?  Thank you  in advance.

---

### Post by gnulogic on 2008-04-08
I installed phpbb2 from the repositories and it dissapeared (cant find where it is in the gnome desktop and I cant figure out how to pull it up in a terminal).

---

### Post by ibutho on 2008-04-08
You actually have to access phpbb2 using your web broswer. There is a detailed guide at the [Ubuntu Community docs]("https://help.ubuntu.com/community/PhpBB2") that may help you.

---

### Post by gnulogic on 2008-04-08
thanks i now have it all installed and running.  but I dont know how to add the forum to my site.  how would i do that?

---

### Post by superprash2003 on 2008-04-08
you could try going to [www.phpbb.com](www.phpbb.com) and download their latest release(phpbb3 i think).. the downloaded file will be a zip file.. extract the contents to the website folder .. like for example /var/www/forum .. then go to [http://localhost/forum/install.php](http://localhost/forum/install.php) to launch the install.php file, then just follow the instructions.. and you should get a forum up and running

---

### Post by ibutho on 2008-04-08
> **gnulogic said:**
> thanks i now have it all installed and running.  but I dont know how to add the forum to my site.  how would i do that?
What happens when you run [http://localhost/phpbb](http://localhost/phpbb) ? Thats the url you use to access the forum from your local machine. If trying to access it from elsewhere you would use the web address e.g. [http://www.somesite.com/phpbb](http://www.somesite.com/phpbb) .

---

### Post by gnulogic on 2008-04-08
thank you everyone, I got it running due to your posts.  Ibutho and superprash2003 your tips really helped.

---

### Post by ibutho on 2008-04-08
> **gnulogic said:**
> thank you everyone, I got it running due to your posts.  Ibutho and superprash2003 your tips really helped.
I'm glad to have helped. :)

---


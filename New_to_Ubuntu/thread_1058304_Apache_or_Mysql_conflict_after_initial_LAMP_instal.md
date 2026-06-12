---
title: "Apache or Mysql conflict after initial LAMP install"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by szofiel on 2009-02-02
Hi! This trouble is very embarrassing but I really don't know how to solve it:  Trying to set up a local account of wordpress I messed the configuration, which now behaves very weird.  According to the official LAMP guide, if all steps to get Apache went well, &quot;It works!&quot; appears after following a link.  Now, I have a Wordpress.com account which whenever I try to preview or logout, redirects me to a page that states &quot;It works!&quot;.  By the sound of it, seems to be pure and real dorkness, but don't know for sure how to fix it.  Any help?   Thanks.

---

### Post by yeats on 2009-02-02
The "It works!" page is the default apache2 page, which is located in /var/www.  Have you moved your Wordpress files into the /var/www directory (must be done with sudo)?  

Also, there are instructions on the Wordpress site you might want to take a look at here:

[http://codex.wordpress.org/Installing_WordPress]("http://codex.wordpress.org/Installing_WordPress")

---

### Post by szofiel on 2009-02-02
> **chrissharp123 said:**
> The &quot;It works!&quot; page is the default apache2 page, which is located in /var/www.  Have you moved your Wordpress files into the /var/www directory (must be done with sudo)?  

Also, there are instructions on the Wordpress site you might want to take a look at here:

[http://codex.wordpress.org/Installing_WordPress](http://codex.wordpress.org/Installing_WordPress)

 Actually, I didn't move one single file.  But after my initial post I've tried to logout again with the following response:    Not Found  The requested URL /remote-login.php was not found on this server. Apache/2.2.9 (Ubuntu) Server at relojmakech.com Port 80   In fact, I'm willing to dump any LAMP conf files in order to flush everything, so I can begin from scratch.   At some point, doesn't seem to me a bad idea, but how can I reset without leaving any trace of earlier steps of the original install?  This is because I have nothing started yet, there's no information stored and I wouldn't mind to begin anew.  Thanks!

---


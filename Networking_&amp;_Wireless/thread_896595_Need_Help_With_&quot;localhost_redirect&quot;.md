---
title: "Need Help With &quot;localhost redirect&quot;"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Stervyatnik on 2008-08-21
I am trying to rescue data from an older version of Wordpress. I installed the appropriate version of Wordpress (2.0.11) in /var/www/wordpress, and I set up the MySQL database so it's now displaying the old data in the Wordpress interface when I go to "localhost/wordpress." So far, so good.

Now, I want to log in to the LOCALHOST wp-admin, so I can (hopefully) create files which will load into the Wordpress 2.6 interface on my Web host/server. I try to go to:

[INDENT]localhost/wordpress/wp-admin[/INDENT]

BUT, the dang thing tries to redirect to:

[INDENT]http://www.mysite.com/wp-login.php?redirect_to=%2Fwordpress%2Fwp-admin%2F[/INDENT]

This is ABSOLUTELY frustrating me. I also have tried:

[INDENT]127.0.0.1/wordpress/wp-admin[/INDENT]

And get the SAME redirect. My /etc/hosts file shows:

[INDENT]127.0.0.1     localhost[/INDENT]

So I have no idea what is going on. I know there's probably a simple explanation and solution, and if anyone out there would like to help a struggling, past-newbie-but-still-stumped guy, thanks in advance!

---

### Post by tolmeda on 2008-08-28
If the page is redirecting, it would be something in the WordPress code for that page, not a networking problem. My guess is there is hardcoded full path configured in WordPress and used to redirect you from the wp-admin page to the wp-login page.

---

### Post by tkm, on 2009-06-30
Hi,

I'm experiencing the same issue. Did you manage to find a resolution?

Thanks,
tkm

---

### Post by chopsueysensei on 2010-02-21
Similar issue here, only that for me it's the other way around. I have a local copy of my site I used to install the whole thing. Now when I login at [http://mysite.com](http://mysite.com) it redirects me to [http://localhost/wp-login.php](http://localhost/wp-login.php)!
In fact that's the hardcoded URL embedded in the page (I can see it in my status bar if I just hover over the login link)... what the hell is going on? There must be something I'm doing wrong but, what?
Any new ideas on this?

Thanks.

---

### Post by thilina on 2011-02-10
you need to edit your mySql database. For more info see the link below.

[http://blog.ishans.info/2011/01/17/weird-wordpress-problem-wp-admin-redirects-to-localhost/](http://blog.ishans.info/2011/01/17/weird-wordpress-problem-wp-admin-redirects-to-localhost/)

---


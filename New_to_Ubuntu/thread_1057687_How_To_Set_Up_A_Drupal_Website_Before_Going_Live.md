---
title: "How To Set Up A Drupal Website Before Going Live?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by wubbzy on 2009-02-02
I currently have a website with DocumentRoot set to /var/www (running Apache2.24 on Ubuntu 6). I just downloaded and set up Drupal on /var/www/mynewsite. I'd like to get that configured, old content migrated, and tested, before going live.

Could someone outline for me how I should go about doing that? I saw I could/should use a2ensite to create a new virtual site, but how do I do that so that I can easily make the new site go live when it's ready? Should I have Apache use another port? One possible problem is that (this is more of a Drupal question but...) when you first set up Drupal, you access an installation page. I think whatever URL you use at the time gets hardcoded into the site. So, if I just use mydomain.com/mynewsite, Drupal will always remember that as my site's URL.

Thanks.

---

### Post by indytim on 2009-02-02
Why don't you just create a sub domain and put Drupal on your public site?  When you're good to go, move the site to you primary domain.

IndyTim

---

### Post by wubbzy on 2009-02-05
> **indytim said:**
> Why don't you just create a sub domain and put Drupal on your public site?  When you're good to go, move the site to you primary domain.

IndyTim

I would use a2ensite to do that, right? (Rather than editing httpd.conf and manually restarting Apache).

Thx.

---

### Post by leg on 2009-02-05
Just have your site set up and get it into the state you want it to be in. When you are finished and you want it to go live ftp the contents to the root of its final position. Then create a database for your site on the server and import your local database to it. Change the settings in <root>sites/default/settings.php to reflect the new database and you should be good to go.

[edit]before you dump your database drop the contents of the watchdog table to save a bit of bandwith.

---


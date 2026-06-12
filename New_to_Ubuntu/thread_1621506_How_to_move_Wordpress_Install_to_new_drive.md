---
title: "How to move Wordpress Install to new drive?"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by kendoori on 2010-11-14
Have just set up a development box for a WP blog that I want to play with. I don't have that much room on my install/root drive, but have plenty on another mounted drive.

I've installed Wordpress and MySQL using the defaults. Wordpress is in:

/var/www/wordpress

Not sure where MySQL data is stored, but I'm less concerned about that growing too large.

I would like to have http:/localhost/wordpress/ such that it grabs data from 
/media/NAS/Wordpress rather than /var/www/wordpress

---

### Post by cariboo on 2010-11-15
Probably the easiest way to do what you need is to create a sym-link:

```
sudo ln -s /media/NAS/Wordpress  /var/www/wordpress
```

I would suggest you move the wordpress directory to /media/NAS, before trying to create the sym-link.

---


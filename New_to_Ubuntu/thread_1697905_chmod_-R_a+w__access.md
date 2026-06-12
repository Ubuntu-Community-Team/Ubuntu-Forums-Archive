---
title: "chmod -R a+w  access"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by joe101 on 2011-03-01
Hello and thank you for looking at this thread, I'm a bit confused as to why a PHP programmer has requested the following access :

[FONT=&quot]chmod -R a+w /var/www/vhosts/domain.com/add/var[/FONT]
[FONT=&quot] chmod -R a+w /var/www/vhosts/domain.com/add/var/cache
chmod -R a+w /var/www/vhosts/domain.com/add/var/plugins
chmod -R a+w /var/www/vhosts/domain.com/add/plugins[/FONT]

[FONT=&quot]I've done several seaches on the net with no clear answer. I'm trying to figure out whether this gives root access to all the above folders from a normal user login and if so how to change the permissions back, any help would be much appreciated.
[/FONT]

---

### Post by jeremy1138 on 2011-03-01
> **joe101 said:**
> Hello and thank you for looking at this thread, I'm a bit confused as to why a PHP programmer has requested the following access :

[FONT=&quot]chmod -R a+w /var/www/vhosts/domain.com/add/var[/FONT]
[FONT=&quot] chmod -R a+w /var/www/vhosts/domain.com/add/var/cache
chmod -R a+w /var/www/vhosts/domain.com/add/var/plugins
chmod -R a+w /var/www/vhosts/domain.com/add/plugins[/FONT]

[FONT=&quot]I've done several seaches on the net with no clear answer. I'm trying to figure out whether this gives root access to all the above folders from a normal user login and if so how to change the permissions back, any help would be much appreciated.
[/FONT]

That will add write access to the specified locations along with all the files rooted in those locations for all users.

To change them back, you need to remove write access for the group and others.

```

chmod -R go-w /var/www/vhosts/domain.com/add/var
chmod -R go-w /var/www/vhosts/domain.com/add/var/cache
chmod -R go-w /var/www/vhosts/domain.com/add/var/plugins
chmod -R go-w /var/www/vhosts/domain.com/add/plugins

```

I think that'll do it for you but I'm no expert so let's see if we can get someone to confirm it first.

Edit - 
Just note that you may want to keep those files as they are with the changes you've shown.  Those permissions changes may be necessary to make things work for you.

---

### Post by SeijiSensei on 2011-03-01
The Apache webserver runs as the "www-data" user.  Ordinary users cannot write to /var/www since it's owned by www-data.

I would suggest a much stricter approach than what the developer proposes.  Make the PHP user's primary group be www-data.  You can also put the user in her own group as a secondary group.  Then grant the www-data group write access to /var/www:

```

sudo usermod -g www-data phpuser
sudo usermod -G phpuser phpuser
sudo chgrp -R www-data /var/www
sudo chmod -R ug+w,o-w /var/www

```

Replace "phpuser" with the actual username.

This won't work so well if you're trying to support multiple developers who all want private access to their code.  One solution is to reverse the above process and put the www-data user in each developer's group.  You could then have each developer maintain her website in her home directory and grant read privileges on that directory to the www-data group.  You'd need to configure the <VirtualHost> definitions in Apache accordingly to point the DocumentRoot to the appropriate location in the developer's home directory.

Managing permissions in situations like this is tricky, and you were right to question the developer's wish to grant world-writable privileges to /var/www.

---

### Post by joe101 on 2011-03-01
Thank you very much for your input jeremy & SeijiSensei, I think your right jeremy in saying that the changes may be necessary to make things work.
Fortunately there is only one programmer SeijiSensei and I will need to think carefully before making any sudo changes as I'm still fairly new to linux.
Though it makes me wonder if the programmer has write access to the /var logs doesn't that mean if he/she has backdoor access that they are able to cover their tracks by removing login entries/attempts  as root or as a user ?

---

### Post by SeijiSensei on 2011-03-01
Logs are in /var/log and owned by root.  Even if you made /var/www world-writable that wouldn't change the ownership of the log files nor grant any additional permissions in /var/log.

---

### Post by joe101 on 2011-03-02
[FONT=Verdana]Thank you SeijiSensei for letting know....at least I will be able to view the logs as they are.[/FONT]

---


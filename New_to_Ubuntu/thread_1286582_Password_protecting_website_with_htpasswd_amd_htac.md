---
title: "Password protecting website with htpasswd amd htaccess"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by anandamide on 2009-10-09
Hi chaps
I'm setting up a private webserver and want to make it password protected. However, the page is still displaying with no requirement for a password.

I've used htpasswd to create a password, created a .htaccess file and edited the apache config file.

.htpasswd is in /home/philip/

.htaccess is in /var/www

htaccess reads:

```
AuthType BasicAuthName "Password Required"AuthUserFile /home/philip/.htpasswdRequire User Philip
```

Here's the diff from /etc/apache2/apache2.conf and /etc/apache2/apache2.cong-original:

```
136c136< AccessFileName /var/www/.htaccess---> AccessFileName .htaccess167c167< HostnameLookups On---> HostnameLookups Off282,290d281<< #Password protect site< <Directory /var/www/*>< AllowOverride FileInfo AuthConfig Limit< </Directory>
```

Any ideas?

It's probably something blindingly obvious. It usually is when I ask questions on this forum... :-p

---

### Post by anandamide on 2009-10-09
Argh! Please excuse crappy formatting!

I meant:

```
AuthType Basic
AuthName "PasswordRequired"
AuthUserFile /home/philip/.htpasswd
Require User Philip
```

```
136c136
< AccessFileName /var/www/.htaccess---> AccessFileName .htaccess
167c167
< HostnameLookups On---> HostnameLookups Off
282,290d281<
< #Password protect site
< <Directory /var/www/*>
< AllowOverride FileInfo AuthConfig Limit
< </Directory>
```

---

### Post by anandamide on 2009-10-09
Just noted an obvious mistake in the above apache.config file, now reads:

```
<Directory /var/www/*>
AllowOverride All
</Directory>
```

---

### Post by anandamide on 2009-10-09
Bump :-)

---

### Post by BugBuster on 2009-10-09
Well first of all this page has useful information that you need to understand apache authentication.

[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)

As far as your query is concerned, I myself, have done a similar setup using the following method.

You need to add the following lines to the apache2.conf file,

> <Directory "/var/www">
AuthType Basic
AuthName "PasswordRequired"
AuthUserFile /home/philip/.htpasswd
Require valid-user
</Directory>

Then create a password file,

```
htpasswd -c /home/philip/.htpasswd Philip
```

This will prompt you for the password for the user "Philip" twice.

Then restart apache service..and try again.

Note: If you get "Internal Server Error" ...then most probably your home folder is not accessible to the apache service.Make appropriate changes to your users/groups settings or move the .htpasswd file to another location. Also in that case make sure you make changes to "AuthUserFile" in apache2.conf


Using this method there is no need for .htaccess file in each protected directory.Simply add <Directory> sections for all the folders that are to be protected.

Also you can add more users to the same password file using

```
htpasswd /home/philip/.htpasswd user2
```

---

### Post by anandamide on 2009-10-09
Thanks a lot for the reply.

That all makes a lot of sense, and reading through the link I think I understand it all with a fair degree of clarity.

I've followed the above steps but am still not getting any prompt when I visit the website. The server just seems to be ignoring my direction to ask for a password.

I do have a feeling that this is probably something very simple that I've just overlooked.

---

### Post by anandamide on 2009-10-09
Ahah - I mised the quote marks from the <Directory ...>.

Now getting an Internal Server Error, as you (kind of) predicted. This is great progress!

Will fiddle with permissions and hopefully it should all be a-OK once that's done.

---

### Post by BugBuster on 2009-10-09
Well here's to make it even simpler...

Under /home in nautilus, right-click on your folder with your username (basically your home),click properties and then select the permissions tab.

There against "Group" select www-data from the drop-down and against "Folder Access" select Access Files.

Log out and login again...

---

### Post by anandamide on 2009-10-09
Haha - I was sneakily ssh'ing from work so no chance of Nautilus.

Interestingly, after fiddling around with permissions and still getting nowhere I checked the error log and found

```
configuration error:  couldn't perform authentication. AuthType not set!: /

```

...I'd forgotten to set the AuthType - d'oh!

Anyway, it's all gloriously straightforward now and working like a dream - thanks so much :-).

---

### Post by St66666 on 2009-10-20
thanks, this was enough help for me to set up mine :)

---


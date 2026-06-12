---
title: "Basic authentication problem"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by apache2noob on 2008-08-26
I'm trying to get basic authentication up and running. But it just won't work :(

This is what I've done so far:
- I made a new VirtualHost with DocumentRoot:/var/www/basic
- I created this folder at /var/www
- In this folder I created an index.html file with some text.
- I added this to my DocumentRoot Directory directive:
  <Directory /var/www/basic>
     AuthType basic
     AuthType Prive
     AuthUserFile /etc/apache2/apache.htpasswd
     Require valid-user
     ...
   </Directory>

- I created a user/password file by using the follwing command: "htpasswd -c /etc/apache2/apache.htpasswd test"
- I activated the site and restarted apache2.

However basic authentication woon't work because if I go to "http://localhost/basic" in mozilla firefox webbrowser,I don't get a login screen that normally should be displayed.

Does somebody know what I'm doing wrong here? Perhaps my Directory where I put "AuthType..." is wrong?

I'm using ubuntu 7.04 and apache2.

Please help

---

### Post by jigsaws on 2008-08-26
AuthType Prive
should it be "AuthName" ? 

:-)

---

### Post by apache2noob on 2008-08-26
I changed it but it doesn't change anything. Do you need to put it in the documentRoot instead of the /var/www/ directory?

---

### Post by jigsaws on 2008-08-26
To be sure add "
AuthName "Prive"

Be sure that authfile exists:
ls -l /etc/apache2/apache.htpasswd
has read permissions for apache user and there are any users.

I used to do auth other way:

<Directory />
...
    AllowOverride AuthConfig
</Directory>

and then I put .htacces file in directory which I want protect:

AuthUserFile /etc/httpd/conf/.htpasswd
AuthGroupFile /dev/null
AuthName "admin"
AuthType Basic

<Limit GET>
require user lukasz
</Limit>

/etc/httpd/conf/.htpasswd is file created with htpasswd command

But your way should also works.

---


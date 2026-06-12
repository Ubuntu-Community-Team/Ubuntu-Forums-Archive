---
title: "Enable FastCGI with VirtualHosts"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by heavymark on 2010-11-16
Good Day,

I'm a newbie to servers and ubuntu. I'm running the official 10.10 Ubuntu 64 bit AMI for Amazon EC2. So far so good.

I've been following some of the recommendations/instructions from MediaTemple's site as they have by far been the most thorough compared to the ones I've found elsewhere.

So I have LAMP installed, VirtualHosts setup, Apache using SuExec to run as the domain user and all that goodness. It was recommend if using SuExec to also use FastCGI. I followed the instructions here to install FastCGI:

[http://wiki.mediatemple.net/w/Configuring_PHP_with_FastCGI_on_Ubuntu_9.10]("http://wiki.mediatemple.net/w/Configuring_PHP_with_FastCGI_on_Ubuntu_9.10")

Now the problem with those instructions are they are for NGINX and not Apache2.

Luckily all the steps but the last seem to work for Apache2 as well. But the last step:

[HTML]nano /etc/nginx/sites-available/ve-server1.com[/HTML]

instead I did:

[HTML]nano /etc/apache2/sites-available/mydomain.com[/HTML]

That file has my virtualhost entry I previously created:

[HTML]<VirtualHost *:80>
ServerAdmin webmaster@mydomain.com
ServerName mydomain.com
ServerAlias www.mydomain.com
DocumentRoot /var/www/mydomain.com/html/
ErrorLog /var/www/mydomain.com/logs/error.log
CustomLog /var/www/mydomain.com/logs/access.log combined
SuExecUserGroup mydomain.com mydomain.com
</VirtualHost>
[/HTML]

So I somehow need to merge my current virtual host file with this data:

[HTML]server {

listen   80;
server_name  www.mydomain.com;
rewrite ^/(.*) http://mydomain.com/$1 permanent;

}


server {

listen   80;
server_name mydomain.com;

access_log /var/www/mydomain.com/logs/access.log;
error_log /var/www/mydomain.com/logs/error.log;

location / {

root   /var/www/mydomain.com/html/;
index  index.html;

}
# pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
#
location ~ \.php$ {
fastcgi_pass   127.0.0.1:9000;
fastcgi_index  index.php;
fastcgi_param  SCRIPT_FILENAME  /var/www/mydomain.com/public$fastcgi_script_name;
include        fastcgi_params;
}


}
[/HTML]

Now alot of that info I already have in my current file but written in apache2 style rather than nginx. I'm just not sure which info I need to include and what format to write it in. Or does someone know of a good link with an example file for Ubuntu 10.10 using VirtualHosts and FastCGI?

This link seems to be the closet to what I'm looking for: [http://linux-101.org/Apache_Virtual_Hosts_with_FastCGI_and_suEXEC.html]("http://linux-101.org/Apache_Virtual_Hosts_with_FastCGI_and_suEXEC.html")

But since I followed the previous article to a t and in this example it has a Directory entry which mine doesn't so not sure if that procedure would work with mine.

---


---
title: "apache"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by Rakeshvijayan on 2011-02-03
Hi  friends I wish to know about apache i read some document on internet about apache configuration

my question is, is  dns is need  for load site in apache ?

thanks

---

### Post by Nerflander on 2011-02-03
To run the site local ? or you want to host for the world wide webbz?

---

### Post by Rakeshvijayan on 2011-02-04
> **nerflander said:**
> to run the site local ? Or you want to host for the world wide webbz?


i just want to learn apache configuration .i want it on localy

---

### Post by DiSTORT3D on 2011-02-04
no you dont need dns to run appache,

very easy

apt-get install apache2

then go to [http://localhost/](http://localhost/) and there is your apache.

---

### Post by lisati on 2011-02-04
To add to this: the default location for storing your web pages so that you can display them once you've installed apache is in folder /var/www

---

### Post by Rakeshvijayan on 2011-02-07
do any body have the clear documentation for Apache and DNS configuration .if you have this please post it through our forum because a person can simplify the complication of configuration .And am the bigner in linux .I got the reply for any technical instance by reffering any site a computer savy can follow those ):P

---

### Post by mcduck on 2011-02-07
Apache2:
[https://help.ubuntu.com/10.10/serverguide/C/httpd.html]("https://help.ubuntu.com/10.10/serverguide/C/httpd.html")

DNS:
[https://help.ubuntu.com/10.10/serverguide/C/dns.html]("https://help.ubuntu.com/10.10/serverguide/C/dns.html")

..but like already mentioned, you don't need DNS to test Apache or use it on local network.

---

### Post by Rakeshvijayan on 2011-02-07
> **mcduck said:**
> Apache2:
[https://help.ubuntu.com/10.10/serverguide/C/httpd.html](https://help.ubuntu.com/10.10/serverguide/C/httpd.html)

DNS:
[https://help.ubuntu.com/10.10/serverguide/C/dns.html](https://help.ubuntu.com/10.10/serverguide/C/dns.html)

..but like already mentioned, you don't need DNS to test Apache or use it on local network.

DEAR SIR I HAD TOLD YOU THAT AM NOT COMPUTER SAVY .

WHAT SHOULD I DO IN THIS FILES 

[LIST]
[*]                                    *apache2.conf:* the main Apache2 configuration file.  Contains settings that              are *global* to Apache2.
[*]                                    *conf.d:* contains configuration files which apply *globally* to Apache2.              Other packages that use Apache2 to serve content may add files, or symlinks, to this directory.
[*]                                    *envvars:* file where Apache2 *environment* variables are set.
[*]                                    *httpd.conf:* historically the main Apache2 configuration file, named after the              **httpd** daemon.  The file can be used for *user specific*              configuration options that globally effect Apache2.
[/LIST]
WHAT SHOULD EIDIT AND INCLUDE THERE

---

### Post by mcduck on 2011-02-07
> **Rakeshvijayan said:**
> DEAR SIR I HAD TOLD YOU THAT AM NOR COMPUTER SAVY .

WHAT SHOULD I DO IN THIS FILES 

[LIST]
[*]                                    *apache2.conf:* the main Apache2 configuration file.  Contains settings that              are *global* to Apache2.             
[*]                                    *conf.d:* contains configuration files which apply *globally* to Apache2.              Other packages that use Apache2 to serve content may add files, or symlinks, to this directory.             
[*]                                    *envvars:* file where Apache2 *environment* variables are set.             
[*]                                    *httpd.conf:* historically the main Apache2 configuration file, named after the              **httpd** daemon.  The file can be used for *user specific*              configuration options that globally effect Apache2.             
[/LIST]
WHAT SHOULD EIDIT AND INCLUDE THERE
That's what the rest of the page explains.

I can't possibly tell you what you might want to do with your web server. :D

But if you really just want to test Apache, you don't need to touch any config files. Just install it and drop some webpages into /var/www, just like DiSTORT3D suggested above.

---

### Post by ikt on 2011-02-07
> **Rakeshvijayan said:**
> DEAR SIR I HAD TOLD YOU THAT AM NOR COMPUTER SAVY .

You shouldn't use all capital letters on the internet, it comes across as shouting.

Why do you want to know about apache?

---

### Post by Tyggna on 2011-02-07
> **Rakeshvijayan said:**
> DEAR SIR I HAD TOLD YOU THAT AM NOT COMPUTER SAVY .


Then you probably shouldn't be bothering with apache at all.  Find a virtual hosting company to handle all this for you.  Apache is big, complicated, and can take years to learn how to administer it effectively.

To run a webserver on a local network without using any name lookups, you're done.  Install it on Ubuntu and it works.  Change what it serves up by editing files in /var/www/html/

If you want answers to all your questions still--they're below, otherwise don't bother reading it.  It's more likely to be confusing than helpful--unless you're putting forth a serious effort to learn apache.

> 

WHAT SHOULD I DO IN THIS FILES 

*apache2.conf:* the main Apache2 configuration file.  Contains settings that are *global* to Apache2.             


Nothing--default setup in Ubuntu serves nearly every need, from static web content hosting to dynamic server side applications.  

This file is used primarily for performance tuning and file logging.   If you change things here, it's just gonna make your life harder--especially if you don't know exactly what you're doing and why you're doing it.

> 
*conf.d:* contains configuration files which apply *globally* to Apache2.  Other packages that use Apache2 to serve content may add files, or symlinks, to this directory.


This is generally a directory.  Since you're only using this locally at the moment, you don't need to do anything with it.  If you ever want to make this server publically available, then you'll want to open the security file here and change the "ServerTokens Full" to "ServerTokens Minimal"


> 
*envvars:* file where Apache2 *environment* variables are set.

Don't touch this--there's no need to for a single-use webserver.

> 
*httpd.conf:* historically the main Apache2 configuration file, named after the **httpd** daemon.  The file can be used for *user specific* configuration options that globally effect Apache2.             
With Ubuntu's setup, this is just here so some old-timers and those who use different versions of Linux can remain comfortable.  You don't have to use it if you don't want to--it's optional.

> 
WHAT SHOULD EIDIT AND INCLUDE THERE
What you really should edit is found in 
```
/etc/apache2/sites-enabled/
```
These files are what will let you use apache with DNS--as I think you've been asking for.  There should be one in there already (mine is named 000-default)

Look through that file and study it closely.  Everything you need to get your webserver working exactly the way you want it is there.
<VirtualHost *:80> specifies what address and port you want this information to be served on.  Some examples of this would be:

<VirtualHost mysite.dyndns.org:80> - serves up webpages to anyone who accesses your website on port 80 via the internet address mysite.dyndns.org

<VirtualHost *:443>  - serves up webpages on the encrypted web-page port

DocumentRoot -- which directory on the server that you want information to be served from.
<Directory /var/www/>  -- setup permissions for that directory, you'll need to read up on this to learn more if it is applicable to you.

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/ -- where you serve up webprograms from.  The syntax for this is that anything accessed via the web (say from [http://198.162.1.101/cgi-bin/](http://198.162.1.101/cgi-bin/)) actually accesses scripts from /usr/lib/cgi-bin/ instead of from /var/www/html
You'll notice that there's a <Directory> tag for this as well--the main reason is it needs to set the Option +ExecCGI, which says that it's okay for the webserver to execute files found in that directory.


That should be enough information for just about any beginner to get started(whether one looking to write web-apps, or looking to do a webpage a. la 90s)

---

### Post by Rakeshvijayan on 2011-02-09
> **tyggna said:**
> then you probably shouldn't be bothering with apache at all.  Find a virtual hosting company to handle all this for you.  Apache is big, complicated, and can take years to learn how to administer it effectively.

To run a webserver on a local network without using any name lookups, you're done.  Install it on ubuntu and it works.  Change what it serves up by editing files in /var/www/html/

if you want answers to all your questions still--they're below, otherwise don't bother reading it.  It's more likely to be confusing than helpful--unless you're putting forth a serious effort to learn apache.



Nothing--default setup in ubuntu serves nearly every need, from static web content hosting to dynamic server side applications.  

This file is used primarily for performance tuning and file logging.   If you change things here, it's just gonna make your life harder--especially if you don't know exactly what you're doing and why you're doing it.



This is generally a directory.  Since you're only using this locally at the moment, you don't need to do anything with it.  If you ever want to make this server publically available, then you'll want to open the security file here and change the "servertokens full" to "servertokens minimal"




don't touch this--there's no need to for a single-use webserver.

            
With ubuntu's setup, this is just here so some old-timers and those who use different versions of linux can remain comfortable.  You don't have to use it if you don't want to--it's optional.


What you really should edit is found in 
```
/etc/apache2/sites-enabled/
```these files are what will let you use apache with dns--as i think you've been asking for.  There should be one in there already (mine is named 000-default)

look through that file and study it closely.  Everything you need to get your webserver working exactly the way you want it is there.
<virtualhost *:80> specifies what address and port you want this information to be served on.  Some examples of this would be:

<virtualhost mysite.dyndns.org:80> - serves up webpages to anyone who accesses your website on port 80 via the internet address mysite.dyndns.org

<virtualhost *:443>  - serves up webpages on the encrypted web-page port

documentroot -- which directory on the server that you want information to be served from.
<directory /var/www/>  -- setup permissions for that directory, you'll need to read up on this to learn more if it is applicable to you.

Scriptalias /cgi-bin/ /usr/lib/cgi-bin/ -- where you serve up webprograms from.  The syntax for this is that anything accessed via the web (say from [http://198.162.1.101/cgi-bin/](http://198.162.1.101/cgi-bin/)) actually accesses scripts from /usr/lib/cgi-bin/ instead of from /var/www/html
you'll notice that there's a <directory> tag for this as well--the main reason is it needs to set the option +execcgi, which says that it's okay for the webserver to execute files found in that directory.


That should be enough information for just about any beginner to get started(whether one looking to write web-apps, or looking to do a webpage a. La 90s)

thanks friend ,
will you guide me to configure apache ? I installed lampserver^ on my 
ubuntu what sould i do next.....

---

### Post by Tyggna on 2011-02-10
You really need to poke around /etc/apache2
The files in there are all used to control and setup your webserver.  If you just want to do PHP on your webserver, than you're good to go and don't need to do anything.  If you want to do more--then read the above post for a brief description of a lot of the files.

For the mysql part of it--you should search around, there's plenty of documentation for setting up a root mysql password and users.  I'd wager a google search of "php with mysql setup" would probably be sufficient.

---

### Post by Rakeshvijayan on 2011-02-11
what this command indecate

---

### Post by Rakeshvijayan on 2011-02-11
am going to follow the informations from u all 

first thing i wish to ask u ,is 

  don'tlive me when am stuck any where I need all members support 

if am gain those new one can learn by our configuration :)

---

### Post by Rakeshvijayan on 2012-01-16
what to do if I have more than one website .my dns name mctlib.com I need to call another web page with name  example.com


[http://www.youtube.com/watch?v=2vA2Yzv-NoI](http://www.youtube.com/watch?v=2vA2Yzv-NoI)

i watched this video I am going to test it on vmware thanks

---

### Post by zipperback on 2012-01-16
> **Rakeshvijayan said:**
> what to do if I have more than one website .my dns name mctlib.com I need to call another web page with name  example.com


To serve multiple domains via apache, then you will need to configure apache to properly handle each of those domains. 

Documentation for apache is available on the apache website
[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

If you want to run multiple virtual hosts, then you need to read over the information found on this page: [http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)


If you are going to be providing web services via domain names then you will need to have those domain names properly configured in DNS as well.

I would however suggest that you simply get a hosting account from a reliable web hosting company and let them handle the technical stuff for you, as this will allow you to concentrate on building your website and such.

- zipperback
:popcorn:

---

### Post by zipperback on 2012-01-16
I should probably point out that if you plan on providing email and ftp services for your domains, you will need to configure those services as well.

My advice it to get a hosting account with a reliable company, and just concentrate on your websites. Leave the technical aspects to those who really know what they are doing.

- zipperback
:popcorn:

---

### Post by Rakeshvijayan on 2012-01-16
> **zipperback said:**
> I should probably point out that if you plan on providing email and ftp services for your domains, you will need to configure those services as well.

My advice it to get a hosting account with a reliable company, and just concentrate on your websites. Leave the technical aspects to those who really know what they are doing.

Thanks for the advice  ,dear friend I am studying that technical part of apache
I am not a web developer

---

### Post by mastablasta on 2012-01-17
These are Ubuntu forums. You should ask for help in Apache forums and read their documentation. There might also be free-ebooks available if you just want to learn.
 
This place is ment for Absolute beginners to Ubuntu linux OS. It is not Absolute beginners to Apache server forums.

---

### Post by Rakeshvijayan on 2012-01-17
> **mastablasta said:**
> 
 
This place is ment for Absolute beginners to Ubuntu linux OS. It is not Absolute beginners to Apache server forums.
  
Dear friend is it possible to install apache on ubuntu .That is the reason for asking question ,I am  a usual user of ubuntu that why I stick on here OK ,If you cant help me just read and leave the page

---

### Post by lisati on 2012-01-17
> **Rakeshvijayan said:**
> Dear friend is it possible to install apache on ubuntu .That is the reason for asking question ,I am  a usual user of ubuntu that why I stick on here OK ,If you cant help me just read and leave the page

Have a look here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---


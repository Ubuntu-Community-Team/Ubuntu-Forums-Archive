---
title: "LAMP on 6.10 i386"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by keiffee30 on 2007-04-17
Anybody:- 

Is it poss to install LAMP (linux webserver, php, mysql) in to ubuntu 6.10 . I have seen it on the server edition but not on the desktop. The reason for doing this is that i would like to run a app called "joomla". This can make websites and i will be using this for some kids to use the website for training.

If this is poss where do i go to get the install app. Can any help out a bit of a newbee on this. 
:-)

---

### Post by dmizer on 2007-04-18
it's not so difficult to just install the requisite parts individually after you've installed your desktop.

for example, all you need to do to install apache is:
```
sudo aptitude install apache2
```
that's it ... nothing more is required.  after the above single command, you will now have a working http server.

more information here: [http://easylinux.info/wiki/Ubuntu:Edgy#Apache_HTTP_Server](http://easylinux.info/wiki/Ubuntu:Edgy#Apache_HTTP_Server)


for php5: [http://easylinux.info/wiki/Ubuntu:Edgy#How_to_install_PHP5](http://easylinux.info/wiki/Ubuntu:Edgy#How_to_install_PHP5)
for mysql: [http://easylinux.info/wiki/Ubuntu:Edgy#How_to_install_MYSQL_for_Apache_HTTP_Server](http://easylinux.info/wiki/Ubuntu:Edgy#How_to_install_MYSQL_for_Apache_HTTP_Server)

btw, joomla is not an "app" it is a CMS (content management system)

---

### Post by jonallport on 2007-04-18
All of the LAMP pkgs are available in one hit via aptitude.  Look at the tasks/unrecognised tasks, you'll see 'lamp-server' if you hit '+' over 'lamp-server' aptitude will mark all of the packages you need for install, then just 'g'.

Hope that helps

---

### Post by dmizer on 2007-04-18
this is true, but mysql requires more than just installing the package.  i thought php was the same (requires a small conf file edit), but apparently i was wrong.

either way though ... it's not difficult to set up a server after a gui installation.

---

### Post by jonallport on 2007-04-18
Me again.

Have just run a server install on a spare box to see what Ubuntu runs during install.  For the LAMP task:

'sudo tasksel'
pick 'lamp server'

sorted!

As for config, as far as i can remember the only thing I "configured" for my webserver was the admin e-mail address in httpd.conf.  mySQL, PHP etc all ran without trouble.

---

### Post by keiffee30 on 2007-06-19
ok many thanks for all your time with this problem. i now have a working server with all the stuff i need and its lovly. 

Many thanks to all the Dev people that are working behind the scenes ... please please keep up the out standing work. 

thanks Ubuntu

---


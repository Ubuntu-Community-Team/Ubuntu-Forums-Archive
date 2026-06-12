---
title: "Apache server configuration"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by technowizard12 on 2010-02-17
Hello,

I'm setting up a web server with Ubuntu Server Edition. If it makes a difference, I'm using the Kubuntu GUI. This is my first Linux distribution ever, so I'm a bit lost. I want to know how to configure the apache server. I've installed it, I just don't know how to edit the configuration. I tried sticking ```
ServerAlias *.website.com
```in the configuration file, but it wouldn't let me save it. How do I edit? More importantly, where do I put my website? I plan to use the Joomla CMS, if that matters.

---

### Post by superprash2003 on 2010-02-17
are you trying to setup virtual server? cause by default after a LAMP ( apache ) install , you really dont need to configure much as anything you put in /var/www will go online

---

### Post by halitech on 2010-02-17
the config files are owned by root so you can't edited them without giving yourself the rights to do so. The easiest way to do this is use sudo. Say you want to edit /etc/apache2/apache2.conf , you would run gksudo kate /etc/apache2/apache2.conf and then you can edit the file and save it. If you want to do it in the terminal, it would be sudo nano /etc/apache2/apace2.conf

---

### Post by technowizard12 on 2010-02-17
Thanks. I still have one more question. I'm trying to unzip Joomla (which is basically my site) to var/www/ . I don't have permission to write to the directory, apparently. Is there a way to extract the file without the error?

---

### Post by pirateghost on 2010-02-17
learn how to use sudo  it will become your best friend for situations like that

sudo tar xvf blahblahblah

---

### Post by halitech on 2010-02-17
The other option is to extract it to a folder in your home folder and then move it to /var/www

example
```
sudo cp ~/folder/joomla/* /var/www/joomla/*
```

or, you can *CAREFULLY* use 
```
gksudo nautilus
```
and move it graphically. Be *VERY* careful using this as you can break your system if you do things you shouldn't do.

---


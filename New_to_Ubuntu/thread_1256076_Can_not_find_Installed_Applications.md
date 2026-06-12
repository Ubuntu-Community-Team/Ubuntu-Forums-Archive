---
title: "Can not find Installed Applications"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by styris88 on 2009-09-02
Hi, 

recently i have installed apache2, php5, mysql and dyndns updater but could not not find any application on my system and all binary files are in usr/share but dont know where are the application launchers

---

### Post by howefield on 2009-09-02
> **styris88 said:**
> Hi, 

recently i have installed apache2, php5, mysql and dyndns updater but could not not find any application on my system...

Sounds like command line stuff, time to break out the terminal...

---

### Post by aeiah on 2009-09-02
they'll be launched from the terminal. some, like php and apache are really services that you dont particularly interact with directly. if you want to set up a web server i suggest reading through a tutorial. you're most of the way there but i suspect you'd like to at least install phpmyadmin (also available in synaptic) as this allows you to control php/mysql via a web control panel.

but like i said, you'd find it clearer if you followed a tutorial

---

### Post by wojox on 2009-09-02
Open you browser:

```
http://localhost
```

It should say It works!

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by jrothwell97 on 2009-09-02
Welcome.

Apache, MySQL and the DynDNS updater are what we call *daemons* - these are programs that run automatically in the background. In effect, they're already running.

As wojox said, if you visit [http://localhost](http://localhost) you should now see an "It works!" page - this means Apache is working.

---

### Post by Gaweph on 2009-09-02
Hello,

You might want to read up on enabling apache modules also, if you are going to want to get php files from yoru home directory to work. e.g.

[http://localhost/~username/SOMEWEBFOLDER/](http://localhost/~username/SOMEWEBFOLDER/)

This means that you can then create and put files in your home folder that can be viewed in the browser and hte PHP will get rendered as if you are looking at it over the internet.

Read this:


[http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file]("http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file")

Read the part about:

cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/userdir.conf userdir.conf
sudo ln -s ../mods-available/userdir.load userdir.load
sudo /etc/init.d/apache2 restart

---

### Post by cranecreek on 2009-09-02
For a step by step on setting up a server go [here]("http://howtoforge.com")

---


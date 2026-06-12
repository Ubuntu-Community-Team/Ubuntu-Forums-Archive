---
title: "few questions"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by zachery on 2011-03-14
so i am pretty much brand new to ubuntu i have messed around with it a little and have gotten my apache2 server up and running what i have some questions on is 


1. How can i give my server a actual address and not my ip address?

2. Is there any way i can put like forum software on part of it? if so how?

3. What is the best way to write web pages i know some html so thats how i was able to write what i have now just wondering what best way is :)


thanks for your help in advance! :D

---

### Post by yeats on 2011-03-14
> **zachery said:**
> 
1. How can i give my server a actual address and not my ip address?

You'll need to register with an ISP/domain name provider.

> 2. Is there any way i can put like forum software on part of it? if so how?

Two popular and easy to use options:

phpBB - [http://www.phpbb.com/](http://www.phpbb.com/)
SMF - [http://www.simplemachines.org/](http://www.simplemachines.org/)


> 3. What is the best way to write web pages i know some html so thats how i was able to write what i have now just wondering what best way is :)

You can use HTML authoring software like Komposer, or you can use a WYSIWIG content management system like Drupal, Plone, or Joomla.

---

### Post by zachery on 2011-03-14
> **yeats said:**
> You'll need to register with an ISP/domain name provider.



Two popular and easy to use options:

phpBB - [http://www.phpbb.com/](http://www.phpbb.com/)
SMF - [http://www.simplemachines.org/](http://www.simplemachines.org/)




You can use HTML authoring software like Komposer, or you can use a WYSIWIG content management system like Drupal, Plone, or Joomla.


thanks for the answers mate i figured i would have to register a domain but was hoping i didnt have i rly wanted to make my own but o well :P

---

### Post by ~Plue on 2011-03-14
1. you could use a free service like dyndns
[http://www.dyndns.com/](http://www.dyndns.com/)
[http://www.no-ip.com/](http://www.no-ip.com/)

2. download and extract the installation archive to your server root (or a sub folder) and follow the instructions through the web browser
(if you haven't already, you must first install php, mysql, and to make things easier, phpmyadmin)

3. you mean a recomendation for an editor? then komposer or bluefish would be fine i guess

---

### Post by 5149.5 on 2011-03-14
> **zachery said:**
> 1. How can i give my server a actual address and not my ip address?
 

If your ISP sets you up with a static IP addres, you could set up your router to forward all requests to your public address on port 8080 to your web servers address on port 80. Your web server would have to be accessed by ip address:8080 and would not be accessible by name.

---

### Post by zachery on 2011-03-14
> **~Plue said:**
> 1. you could use a free service like dyndns
[http://www.dyndns.com/](http://www.dyndns.com/)
[http://www.no-ip.com/](http://www.no-ip.com/)

2. download and extract the installation archive to your server root (or a sub folder) and follow the instructions through the web browser
(if you haven't already, you must first install php, mysql, and to make things easier, phpmyadmin)

3. you mean a recomendation for an editor? then komposer or bluefish would be fine i guess


well i actually installed mysql and php5 and apache2 of but you are suppose to be able to go to your ip address/phpmyadmin/: but i cant get it to come up i have restarted the server and everything but that page wont show up

---

### Post by 5149.5 on 2011-03-14
> **zachery said:**
> well i actually installed mysql and php5 and apache2 of but you are suppose to be able to go to your ip address/phpmyadmin/: but i cant get it to come up i have restarted the server and everything but that page wont show up

How is your client connected to your server? Are they both connected to the same switch/router?

---

### Post by zachery on 2011-03-14
> **5149.5 said:**
> How is your client connected to your server? Are they both connected to the same switch/router?


well i tryed on my server it self using the gui and firefox web browser and tryed on my reg desktop didnt show up on either 

but yes they are both connect to my router my desktop is wireless and my server is plugged in to Ethernet from my router router ofc is plugged into my modem

---

### Post by ~Plue on 2011-03-14
> **zachery said:**
> well i actually installed mysql and php5 and  apache2 of but you are suppose to be able to go to your ip  address/phpmyadmin/: but i cant get it to come up i have restarted the  server and everything but that page wont show up
try;
```
sudo dpkg-reconfigure phpmyadmin

```or if that doesnt to it, purge and reinstall
```
sudo apt-get purge phpmyadmin && sudo apt-get install phpmyadmin

```(run *sudo /etc/init.d/apache2 restart *after you do either of that[I])
[/I]

---

### Post by zachery on 2011-03-14
> **~Plue said:**
> try;
```
sudo dpkg-reconfigure phpmyadmin

```or if that doesnt to it, purge and reinstall
```
sudo apt-get purge phpmyadmin && sudo apt-get install phpmyadmin

```(run *sudo /etc/init.d/apache2 restart *after you do either of that[I])
[/I]


woot i purged it and it work now thanks mate :)

---

### Post by zachery on 2011-03-14
/e figured out the cmd will see where i can get thanks for help guys appreciate it

---

### Post by zachery on 2011-03-14
ok so im trying to restart the server and im getting

/etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting ...........................................................httpd (pid 761) already running



when i try to go to my phpmyadmin i get

**phpMyAdmin - **

 Cannot start session without errors, please check errors given in  your PHP and/or webserver log file and configure your PHP installation  properly.

---

### Post by zachery on 2011-03-15
still getting it guys :(

---


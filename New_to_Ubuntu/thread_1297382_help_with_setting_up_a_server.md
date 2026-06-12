---
title: "help with setting up a server"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by itsbrad212 on 2009-10-21
Hey guys, i got another question.

i have a laptop i would like to use as a server for a ***small*** website. but i didnt know if i could considering i have a wireless connection coming into my laptop. so, would that change anything? and next, what would i need to access it over the internet. (i have apache, mysql, php, phpmyadmin)

thanks in advance!!!

---

### Post by eilios on 2009-10-21
Laptop? *Server?* Wha..?
Jokes aside, it would need to be plugged in via broadband(wireless can disconnect occasionally) and plugged into an energy source for it to be viable. That advice aside...
First, you need to port forward. That's the easy part, go to [www.portforward.com](www.portforward.com), forward it to the port you run your server off of(usually port 80). After that, go to a friend's house, and go to your computer's IP, and see it if works. If you can get that far, you are ready for a domain.

---

### Post by martrn on 2009-10-21
> **itsbrad212 said:**
> would i need to access it over the internet. (i have apache, mysql, php, phpmyadmin)

Goto [URL="http://www.whatismyip.com/"]
http://www.whatismyip.com/[/URL]

and post back the [http://88.88.88.88](http://88.88.88.88)   url that you get from there to anyone who you think can test your website for you and see what they say about it.

If it becomes popular you might need another computer to put it on and also a fixed ip number if your isp keeps changeing your number.

---

### Post by itsbrad212 on 2009-10-21
thanks for the quick reply. ill try what you said. lol sorry the laptop thing sounds like a joke, its just temporary :D

---

### Post by itsbrad212 on 2009-10-21
ok i did the port forwarding, and what exactly is the browser looking for (is it /var/www ???) i'm confused :confused:

---

### Post by SkyNet2029 on 2009-10-21
all of your web content needs to be in /var/www
or you could specify a non-standard diretory in your apache httpd.con

---

### Post by martrn on 2009-10-21
Apache will server all the .php .html files from a the 'rules' place at :

[file:///etc/apache2/sites-available/default]("file:///etc/apache2/sites-available/default")

You need to post your ip no in the form :

[http://81.200.64.50](http://81.200.64.50)

which you can get from

[http://www.whatismyip.com/](http://www.whatismyip.com/)

!!  : - /

---

### Post by itsbrad212 on 2009-10-21
[B]71.155.239.132 and wat do i do about apache
[/B]

---

### Post by martrn on 2009-10-21
Type sudo /etc/init.d/apache2 restart

from a terminal and that should restart apache.

http: //   71.155.239.132[/url] to view your website, as long as your isp allows it.

You will have a file at /etc/apache2/sites-available/default

that will list directories such as /var/www/ where you can serve web-pages from.

---

### Post by itsbrad212 on 2009-10-21
thanks for all of your help. unfortunatly, my isp doesn't allow it, i've found...:(:(:(:(:( BOO AT&T!!!!

---


---
title: "The best VPS solution for you?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Blagomir on 2009-04-24
Hello :)

What you use for creating VPSs ? What should i use - OpenVZ, Xen or Linux VServer ?

---

### Post by MontelEdwards on 2009-05-07
Whattt?
I just use Apache,
the easiest way is to install it via XAMPP.
But DONT use it for a public website, public webserver. Basically nothing out of your local network.
You can get XAMPP by running these commands
```
wget http://www.apachefriends.org/download.php?xampp-linux-1.7.1.tar.gz
sudo tar xvfz xampp-linux-1.7.1.tar.gz -C /opt

```

Then to start the server you need to do
```
sudo /opt/lampp/lampp start
```

Then if you want to save file to the server, the folder I believe is /opt/lampp/htdocs.




Or you can install Ubuntu's Apache from the respos by running
```
sudo apt-get install apache2
```
then the folder is /var/www
You will need to set the permission to the file owner as www-data
I guess that is the easiset way because it is auto started.
Just go to [http://localhost]("http://localhost") once you have it loaded, and you will see it.:guitar:

---


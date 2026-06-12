---
title: "How to make a website"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by wildgene789 on 2007-09-25
hey guys i installed Ubuntu Server and all i want to do is run a website on it. can you point me to a tutorials or make one for me on how to set up a web server with like php mysql  phpmyadmin and all that **** . now lets remember im really knew at all this linux stuff lol my friend just told me there like no viruses so i want to give a chance :)

---

### Post by gsiliceo on 2007-09-26
Try getting XAMPP, it has all you need for a webserver
[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

---

### Post by _Phil on 2007-09-26
What should this website be for?
Testing purposes or commercial?

For testing purposes I would suggest LAMPP (Linux+Apache+MySQL+PHP+phpmyAdmin)
```
http://www.apachefriends.org/en/xampp-linux.html
```

But attention! If you want to go online with your website LAMPP is very dangerous. There are no passwords set for root Users and many restrictions (like PHP register_globals etc.) are enabled. So its very unsecure, because the goal behind LAMPP is to test Web Applications on a open system.

cheers
phil

---

### Post by wildgene789 on 2007-09-26
well i just want a website lol but i want it to be secure too.

---

### Post by itzabo on 2007-09-26
I use [http://clarkconnect.com]("http://clarkconnect.com") for my servers.
The home version works as a
Router,Firewall,DHCP Server,Web Server, Mail Server,FTP Server, File Server

All of these can be up and running in about 20 min with either a DSL or Cable Modem.
Put 2 NIC's in your server PC and install.

Works great with the following stuff I use
2 XP Pro, 1 Vista, 1 Ubuntu, 1 iBook, DLINK Wireless router (DHCP Disabled)

The server has no mon or keyboard hooked up to it. Use any web browser to work on things.
Or SSH for terminal stuff.

Good Luck.

Bo

---

### Post by _Phil on 2007-09-27
Or you could try 

```
sudo tasksel
```

Where you can install LAMP Server, which is apache, MySQL and PHP as aptitude packages. They are standard installed, so you have to configure them by yourself.

I haven't tried this by myself yet.

cheers
phil

---


---
title: "OwnCloud Public Access"
date: 2014-04-10
forum: Networking &amp; Wireless
---

### Post by thault on 2014-04-10
I have Xubuntu 12.04 installed, with OwnCloud installed and running in the LAN. I'm interested in accessing this from school. I have a domain that points towards my network. What do I need to do within my network and apache to connect with owncloud outside the network.

---

### Post by Ubi_one_2014 on 2014-04-10
open port 80 and you should get access by:
[http://real_ip/owncloud](http://real_ip/owncloud)

---

### Post by thault on 2014-04-10
Will I need to change any of my settings with my domain forwarding with that port?

---

### Post by Ubi_one_2014 on 2014-04-10
as fas as i know, no

---

### Post by paulisdead on 2014-04-11
You really should be running SSL on the site for this.  By default https runs on 443.  You can set it up so if you connect on port 80 it'll forward to https.  I think the installation instructions for owncloud even outline how to set the web server up that way.  If you don't want to pay a certificate authority for one, you can make a self signed one, but by default most browsers will give a warning when you first connect.  Your router/dsl/cable modem or whatever will need to be setup to forward the ports to the internal IP of your server.

Also make sure you install any updates for openssl on the server before you put it on the internet.  I'm sure you've already heard about the heartbleed bug.

---

### Post by thault on 2014-04-13
Do you have a good guide on setting up SSL on owncloud?


```
sudo a2enmod ssl
sudo a2ensite default-ssl
sudo service apache2 reload
```

Here's the code to create a self signed SSL certificate and make it the default. Thanks for your help guys :)

---


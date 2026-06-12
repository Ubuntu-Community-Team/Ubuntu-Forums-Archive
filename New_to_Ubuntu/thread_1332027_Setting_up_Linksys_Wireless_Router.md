---
title: "Setting up Linksys Wireless Router"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by mvdoso on 2009-11-19
I recently bought a Linksys Wireless Router.  It came with a CD, that was Mac and Windows only.  I no longer have the CD or box, and the router is all hooked up and working, but I want to create a password for it so that people who live around me can't steal my internet.  I have an Ubuntu Laptop with a CD drive, and a netbook with no CD drive. 

How can I do this?

The Router is one of the new Linksys N ones.

---

### Post by teward on 2009-11-19
you need to go into the Router's configuration settings and add a password.  Then you need to activate the password using WEP or WPA2 encryption.  Go to Linksys' website and look for the manuals for your particular router's manual.

---

### Post by twisted_steel on 2009-11-19
You will need to modify the configuration using the web interface.  I believe the default network with Linksys routers is 192.168.1.0/24.  If this is the case, open up a web browser and point to [http://192.168.1.1](http://192.168.1.1).  You should get a password prompt.

When enabling wireless security, only use WPA or WPA2.  Do not use WEP.  Use AES for encryption.  I personally just do a pre-shared key with random letters and numbers that I save in a text file.  If you search for "linksys router manual" on Google, the one for WRT600N should be close enough.  I don't think Linksys differs that much in their web interfaces.

---

### Post by cariboo on 2009-11-19
You don't need the CD even on Windows. Open your favourite web browser, in the url bar type:

```
http://192.168.1.1
```

If you haven't changed the administration user name and password, enter:

```
admin
```

for both the username and password, once you're in you can change all the settings you want.

---


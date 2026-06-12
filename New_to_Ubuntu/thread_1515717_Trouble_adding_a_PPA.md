---
title: "Trouble adding a PPA"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Vendettaseve on 2010-06-22
Hey

Having some trouble adding a PPA for Gyachi on Ubuntu 10.04, Here is why Im putting in and what its kicking back to me.

> vendettaseve@vendettaseve-laptop:~$ sudo add-apt-repository ppa:baudm/ppa
[sudo] password for vendettaseve: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv F8DAF736A0F5EEE030AE0B9CB00E04A9D58062FB
gpg: requesting key D58062FB from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host


And the site im getting the instructions from.  [https://launchpad.net/~baudm/+archive/ppa?field.series_filter=lucid]("https://launchpad.net/~baudm/+archive/ppa?field.series_filter=lucid")

Your help is much appriciated, 

Thanks

---

### Post by howefield on 2010-06-22
keyserver.ubuntu.com has been a bit flaky recently and looks to having issues again.

Try a different keyserver.

---

### Post by Vendettaseve on 2010-06-22
> **howefield said:**
> keyserver.ubuntu.com has been a bit flaky recently and looks to having issues again.

Try a different keyserver.

Care to elaborate?

---

### Post by howefield on 2010-06-22
Try running this in terminal.

It will try to fetch the signing key from a mirror server.

```
sudo apt-key adv --keyserver wwwkeys.eu.pgp.net --recv-keys D58062FB
```

The other option is to import the key via a text file into your software sources, let me know if you want a copy of the one you need.

System > Administration > Software Sources > Authentication tab > Import Key File and navigate to where you have placed the file.

---

### Post by Vendettaseve on 2010-06-22
> **howefield said:**
> Try running this in terminal.

It will try to fetch the signing key from a mirror server.

```
sudo apt-key adv --keyserver wwwkeys.eu.pgp.net --recv-keys D58062FB
```

The other option is to import the key via a text file into your software sources, let me know if you want a copy of the one you need.

System > Administration > Software Sources > Authentication tab > Import Key File and navigate to where you have placed the file.

Excelent thanks :D Worked perfectly

---

### Post by howefield on 2010-06-23
> **Vendettaseve said:**
> Worked perfectly

Thanks for the update, it is useful to have a few backup keyservers handy.

wwwkeys.eu.pgp.net is one of many. (I think you can change "eu" to any two letter country code, I have never had to, it seems reliable enough)

---


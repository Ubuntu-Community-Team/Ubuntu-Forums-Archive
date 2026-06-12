---
title: "Apache install can't locate server name"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by Ron Roy on 2010-12-25
Hi, Just tried to install apache and the terminal message says can't locate server name. How can I uninstall apache?
Thanks

---

### Post by cariboo on 2010-12-26
That's just a standard error message, apache should still work. IF you want to uninstall apache2, you can use the software Center, Synaptic Package Manager or the command line using the following command:

```
sudo apt-get purge apache2
```

Make sure you have stopped apahace before removing it, using the following command:

```
sudo service apache2 stop
```

or

```
sudo /etc/init.d/apache2 stop
```

---

### Post by wojox on 2010-12-26
And if it's FQDN this will fix it [FQDN]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache")

---


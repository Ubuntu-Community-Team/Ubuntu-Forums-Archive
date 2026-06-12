---
title: "PHP help"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by Old-un on 2011-03-04
I would like to start learning PHP but i'm not sure what software to install. Have just been told that XAMPP is pretty good but can't find it in synaptic? Would appreciate any help and/or advice.

---

### Post by LetUsDesign.it on 2011-03-04
> **Old-un said:**
> I would like to start learning PHP but i'm not sure what software to install. Have just been told that XAMPP is pretty good but can't find it in synaptic? Would appreciate any help and/or advice.
 
A good option for you is to install the LAMP server directly from the CLi
 
```
sudo tasksel install lamp-server
```
 
You can look towards [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) for more information

---

### Post by dionysius on 2011-03-04
For a quick and easy install of a LAMPP stack you could have a look at [LAMPP at Apache Friends]("http://www.apachefriends.org/en/xampp.html")

And I'm sure you'll find [Tuxradar's Practical PHP]("http://www.tuxradar.com/practicalphp") useful too. 

If you're installing LAMPP on your production machine, remember to set passwords and enable ufw - and stop services like Apache when you're done.

---


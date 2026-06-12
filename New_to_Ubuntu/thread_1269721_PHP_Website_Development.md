---
title: "PHP Website Development"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by shaolin77 on 2009-09-18
Hello Everyone, 
  While I'm not  new Linux or website development, I am new to Ubuntu and need some help figuring out both Ubuntu and Website development using PHP.  I've been mainly developed websites using a certain .netframework from MS...however I would like to start using PHP and through Linux.   

I just installed Ubuntu (Desktop v.9.04) and I understand that I will need to do a LAMP configuration...my question is that after this gets installed I will be taking the PC off my network and using it offline for website development (If possible)...I know this may sound a little silly however without going into anymore detail..is this possible?  Can I  develop a php website with on Ubuntu without having it connected to a network for that matter the Internet?  I'm not sure if with the LAMP configuration it will create virtual server environment in which I can see the outcome of my code?  

Not bad for my very first Ubuntu posting huh? :lolflag:

---

### Post by apmcd47 on 2009-09-18
Why not install Apache and PHP from source? That way you will have a web environment you are comfortable with and not have to worry about unknowns such as LAMP. You can also put in the options YOU want, not those the package maintainers think you want.

Just a thought.

Andrew

---

### Post by shaolin77 on 2009-09-18
Andrew, 
  Thank you for the information, well since I'm new to the PHP scene, I thought that LAMP was more of a complete package..since I will need to design a database with any PHP website I will start working with..I figured I would need Apache2, PHP, and MySql...however again I'm still new to this..so I'm not if this is the correct mindset I should have. 

Thanks,

Shaolin77

---

### Post by sunchiqua on 2009-09-18
Yes, you can work offline ( don't forget about Firefox "Work offline" option .. sometimes it makes people go crazy ).

---

### Post by shaolin77 on 2009-09-18
Sweet!!

Thanks, do you know of good IDE that I can use to build PHP sites with...I know I can use any basic text editor, however I need a good IDE to work off of.  


Thanks again.

---

### Post by indytim on 2009-09-18
```

$ sudo tasksel

```

Select LAMP and do the install the easy way.  When finished don't forget to change your permissions in /var/www to your user id.

IndyTim

---

### Post by sunchiqua on 2009-09-18
> **shaolin77 said:**
> Sweet!!

Thanks, do you know of good IDE that I can use to build PHP sites with...I know I can use any basic text editor, however I need a good IDE to work off of.  


Thanks again.

Eclipse PDT, NetBeans, Geany, etc. - Google for screenshots/description.

---

### Post by bunizz on 2009-09-18
NetBeans is my favorite! :)

---

### Post by gordintoronto on 2009-09-18
I'm about two weeks ahead of you, so I can answer some questions.

You can indeed install Apache, PHP and mySQL on your Ubuntu, and do development and testing offline.  You can also do testing from another computer on your network, by pointing its browser at your IP address.  For example, you might want to check that your site looks OK in Explorer.

If you're new to Mysql, I suggest you search the forums for "mysql_real_escape_string" and plan on spending a couple of hours reading the results.

---

### Post by jzacsh on 2009-09-18
_you can also just open up synaptic._
**search for **(*and then click mark for installation*)...
* **php** (*the generic name - i believe the generic names are usually pointers to the latest stable versions of things* - someone correct me if I'm wrong?)
* **apache2**
* **mysql-server**

* **click apply/install** (*and **okay**, for whatever else it asks you about dependencies*)

_when synaptic is done installing all that_
* **phpmyadmin**

*that's it!* :)

**visit your development site here:**
_[http://localhost/](http://localhost/)_
you should see "**it works!**"

**now take control** of development by putting something like **this in the terminal**:
```
sudo chown -R *uname:uname* /var/www
```
that ^ will make your development folder (which is, _/var/www_) yours and writable for you.
...then, even:
```
mv /var/www/index.html /var/www/orig_index.html
```
that will move the ^ "**it works!**" test out of your way.

---


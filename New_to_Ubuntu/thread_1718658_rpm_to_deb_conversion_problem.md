---
title: "rpm to deb conversion problem"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by Omar.Fayyad on 2011-03-31
[COLOR=Red]error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package ncui: preinst
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `ncui-1.2': File exists
unable to mkdir ncui-1.2:  at /usr/share/perl5/Alien/Package.pm line 257.[/COLOR]


[SIZE=4]I found the above error when tried to convert and install rpm package to deb.

Please help .... how can i solve it...!!!?[/SIZE]

---

### Post by Omar.Fayyad on 2011-03-31
.....

---

### Post by davidmohammed on 2011-03-31
can you supply a link to the rpm?

---

### Post by sanguinoso on 2011-03-31
What procedure did you use to attempt to convert the rpm?

---

### Post by bodhi.zazen on 2011-03-31
> **Omar.Fayyad said:**
> [COLOR=Red]error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package ncui: preinst
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `ncui-1.2': File exists
unable to mkdir ncui-1.2:  at /usr/share/perl5/Alien/Package.pm line 257.[/COLOR]


[SIZE=4]I found the above error when tried to convert and install rpm package to deb.

Please help .... how can i solve it...!!!?[/SIZE]

That error message tells you what to do 

> Use the --scripts parameter to include the scripts.

alien --scrpits ...

What are you trying to install ?

In my experience, converting a rpm is often suboptimal and you are (IMHO) far better off compiling from source.

That scripts error is ominous as often the "scripts" you would run on a rpm systems (ie RHEL / Fedora) are incompatible with Ubuntu.

---

### Post by Omar.Fayyad on 2011-04-02
[COLOR=Red]That was the command for installing flash-plugin rpm package [/COLOR]

alien -d -i --scripts /flash-plugin-10.2.153.1-release.i386.rpm 


[COLOR=Red]That was the error recieved.[/COLOR]

error: incorrect format: unknown tag
mkdir: cannot create directory `flash-plugin-10.2.153.1': File exists
unable to mkdir flash-plugin-10.2.153.1:  at /usr/share/perl5/Alien/Package.pm line 257.


[COLOR=Red]ANY HELP..?[/COLOR]

---

### Post by Omar.Fayyad on 2011-04-02
> **davidmohammed said:**
> can you supply a link to the rpm?



[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by Omar.Fayyad on 2011-04-02
> **sanguinoso said:**
> What procedure did you use to attempt to convert the rpm?


alien -d -i --scripts /flash-plugin-10.2.153.1-release.i386.rpm

---

### Post by davidmohammed on 2011-04-02
you dont need to install flash using that method.

Simply install all the ubuntu restricted codecs will do this for you


sudo apt-get install ubuntu-restricted-extras

or just search in software centre for the above.

As a recommendation - stick to the applications in the software centre.

---

### Post by bodhi.zazen on 2011-04-02
> **davidmohammed said:**
> you dont need to install flash using that method.

Simply install all the ubuntu restricted codecs will do this for you


sudo apt-get install ubuntu-restricted-extras

or just search in software centre for the above.

As a recommendation - stick to the applications in the software centre.

If all you want is flash, use :

```
sudo apt-get install flashplugin-nonfree
```

The ubuntu-restriced-extras will install a lot more then flash.

If you want to install flash from adobe, use the tar ball and not the rpm.

---

### Post by st33med on 2011-04-03
Agreed with Bodhi. Don't bother with RPM packages unless it is absolutely necessary.

---


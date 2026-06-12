---
title: "can't install netbeans on Ubuntu 10.04"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by nurwakhidin on 2010-05-02
guys, I really need help..
I just upgraded my ubuntu 9.10 to 10.04, It works well but my Netbeans is lost, I try to install it again from Synaptic Package Manager but it says "... no available version but exist in database"..
can someone give me a solution.. TIA

---

### Post by Elfy on 2010-05-02
it's here in mine - Universe repository

If you open a terminal and run 

```
sudo apt-get update &&sudo apt-get install netbeans
```

can you paste the error message you get.

---

### Post by nurwakhidin on 2010-05-02
well.. I just tried this..

"sudo aptitude install netbeans"

it works.. I got netbeans 6.8
but.. thanx anyway..

---

### Post by throwspinecones on 2010-05-12
In case anyone has my problem, upgrade to 10.04 and netbeans PHP stopped working.  

1) I had to change the xdebug path /etc/php5/apache2/conf.d/xdebug.ini to zend_extension=/usr/lib/php5/20090626/xdebug.s  

2) I uninstalled netbeans, purged, reinstalled, and delete ~user/.netbeans/6.8    

3) when netbeans came up, answer yes to migrate over old settings.

4) PROBLEM: the PHP plug in was not there, and there is a very tiny icon in the botton right side you have to click, and it will fetch all the modules in the previous install. 

Maybe I made this harder than it had to be, but this process did get netbeans, xdebug, PHP working so I can debug drupal and such

---

### Post by Summitt Dweller on 2010-06-29
I just upgraded Ubuntu 9.10 to 10.04 and my Netbeans 6.8 didn't make the journey.  I'm reinstalling it now but wondering how I might get back all my old 6.8 configuration and projects.  My entire 9.10 image is backed up in a tar but I'd rather not piece through it if there's an easier way.

---

### Post by Summitt Dweller on 2010-06-29
> **throwspinecones said:**
> 
2) I uninstalled netbeans, purged, reinstalled, and delete ~user/.netbeans/6.8    

3) when netbeans came up, answer yes to migrate over old settings.


I'm curious about 2 and 3 above.  When you say "purged"...what exactly did you do?  And once ~user/.netbeans/6.8 is gone how does Netbeans know what the old settings are?

I'm not questioning if this will work or not (haven't gotten that far yet) but am just wondering how it does this.

FYI... After I installed NB6.8 on my Ubuntu 10.04 box it came up showing all my old projects FOR AN INSTANT.  A moment later they were gone and I haven't found a way to get them back, yet.

Thanks again.

---

### Post by Summitt Dweller on 2010-06-29
Just completed the process in step 2, but when I launched NetBeans it never prompted me to restore/recover my old configuration.  So, I have the old config all backed up...just need to know how/where to recover my lost projects and settings now.

---


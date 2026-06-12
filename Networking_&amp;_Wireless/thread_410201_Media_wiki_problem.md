---
title: "Media wiki problem"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by NiRaDo on 2007-04-15
Hi.
I try to install media wiki whereas apache is ever present. So, I began to enter in terminal :

   >  sudo apt-get install mediawiki1.5 mediawiki1.5-math 

After that, I configured apache :

>     sudo ln -s /etc/mediawiki/apache.conf /etc/apache2/sites-available/mediawiki.conf
    sudo ln -s /etc/apache2/sites-available/mediawiki.conf /etc/apache2/sites-enabled/001-mediawiki

Unlucky, when I try to launch apache, I get an error message :
> 
    dorian@dorian-desktop:~$ sudo invoke-rc.d apache2 restart
    Password:
     * Forcing reload of apache 2.0 web server...                                   grep: /etc/apache2/sites-enabled/001-mediawiki: No such file or directory
                                                                             [fail]
    invoke-rc.d: initscript apache2, action "restart" failed.

It is very tricky. How can I resolve this problem ?

Thank you in anticipation.

---

### Post by Boodah on 2007-04-21
Hi 
I just had the same problem. I think there is a problem with the symbolic links. Follow each link in turn and you will find the break. For me it was on /etc/apache2/sites-available/mediawiki.conf. 

I resolved the problem by removing the broken link and replacing it with this...

```

sudo ln -s /etc/mediawiki1.5/apache.conf /etc/apache2/sites-available/mediawiki.conf

```

hope this helps

---

### Post by benunderscore on 2007-05-07
thanks for this, worked a treat

the url once you've done the symbolic links is [http://localhost/mediawiki](http://localhost/mediawiki) 

the actual mediawiki files are in /var/lib/mediawiki1.7/ (for feisty)

---


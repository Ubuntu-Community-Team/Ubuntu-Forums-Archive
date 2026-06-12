---
title: "Restoring a system back?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by unknown user on 2009-01-19
[FONT="Tahoma"]I have now got my 8.10 system worked close to how I want it and I was wondering if there is any imaging software that I could use to make an image to restore to in case my laptop went down, like ghost on windows?

Or would just taking a copy of my user folder be enough to restore back to if the worst happened?[/FONT]

---

### Post by hyper_ch on 2009-01-19
depends...

you could boot a live cd and then just "dd" the whole drive to another drive... that's probably the simplest way

or you could just save your home folder, the etc folder, the var/www the /var/lib/mysql and other folders you need incl. a list of installed packages. You can't then mirror back but you can pretty quickly re-setup your system.

---

### Post by taurus on 2009-01-19
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by donkyhotay on 2009-01-19
I'd just backup your home folder and other files. Reinstallation is pretty fast and it's probably easier to update your files then making images all the time.

---

### Post by Temposs on 2009-01-19
donkyhotay is right. There is no need to image your entire drive. You can use a backup program like Simple Backup: [http://sourceforge.net/projects/sbackup/](http://sourceforge.net/projects/sbackup/)

You can get it from the repositories:

```
sudo apt-get install sbackup
```

---

### Post by MrKlean on 2009-01-19
You could also use remastersys..it will make an iso file which you can burn to dvd.  This will make an installable copy of the system you have setup.  There is a problem, with the printing afterwards which has a simple fix, if you're running Intrepid ; )

---

### Post by unknown user on 2009-01-22
Thanks for the reply guys, will install sbackup tonight.

---


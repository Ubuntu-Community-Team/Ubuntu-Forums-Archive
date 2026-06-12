---
title: "getting started with Apache2 (issue when opening php file)"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by rhythmiccycle on 2009-06-17
i have experience using php on windows xp, but i used "xampp" to set everything up.

i'm trying to get apache2 working in ubuntu. 

i got the localhost set up, and it is running html files fine.

but when i try to open a php file, firefox opens "opening file" window. It seems to be trying to download the file, but i just want it to work like a normal webpage

is the problem in the apache2 settings or is it in the firefox settings?

either way, how do i fix it?.

---

### Post by Iowan on 2009-06-17
See if [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205") helps - in particular thi part:> Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php.

---

### Post by TheBuzzSaw on 2009-06-17
In synaptic, just install the "php5" package, and it will get you all setup for PHP testing. :)

---

### Post by rhythmiccycle on 2009-06-18
i entered 

sudo apt-get install libapache2-mod-php5

and updated

The same thing is still happening

---

### Post by v3xtra on 2009-06-18
[http://ubuntuforums.org/showthread.php?t=1187873&highlight=php+FF](http://ubuntuforums.org/showthread.php?t=1187873&highlight=php+FF)

Post #6 should be what you need.  Hope that helps!

---

### Post by rhythmiccycle on 2009-06-19
post #6 from that link did the trick, thanks alot

---


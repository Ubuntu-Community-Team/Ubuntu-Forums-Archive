---
title: "Permissions Help!"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by Datamac on 2010-03-30
Need help maintaining permissions across multiple directories.  Have Ubuntu 8.04 Hardy Heron.  O/S installed, updated and running with no problems.  Why is it that my administrator user id doesn't seem to have root permissions to create directories?  I am trying to setup hosting 3 separate websites and therefore create 3 separate directories to manage all associated files for the 3 websites.  Also, I am attempting to read through the tutorials located at: [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

### Post by Calash on 2010-03-30
The guide you are reading is assuming you are using a root account.  Ubuntu has the root account locked and uses a command called sudo to grant temporary root privileges


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Looking quickly at the guide you should be able to do what you need by adding sodo before each command line.  You will have to type your password the first time but it will cache it for a period of time.

---

### Post by Datamac on 2010-03-30
How do I get temporary root privileges in the GUI of unbuntu?

---

### Post by HarrisonNapper on 2010-03-30
You can run a command (Alt+F2) using gksudo (Gnome) or kdesudo (KDE). So if I want to open synaptic, Alt+F2, then "gksudo synaptic", enter my root password, success! :)

---

### Post by halitech on 2010-03-30
to create a directory - sudo mkdir /var/www/directory1

to create a file - sudo touch /var/www/directory1/indoex.html

to edit a file - sudo nano /var/www/directory1/index.html
or
gksudo gedit /var/www/directory1/index.html

---

### Post by J V on 2010-03-30
What he wants is "gksudo nautilus" which, by the way is a bad idea. Try to use the commandline to do it, much safer, and if you can't figure out what you want beforehand so you leave it open as short as possible (Copy a file to your ~ and then find out you can't remove it for example)

---


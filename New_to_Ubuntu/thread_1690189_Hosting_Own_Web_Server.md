---
title: "Hosting Own Web Server"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by asbloodrunsblack on 2011-02-18
Just wondering if anyone had any literature i could read up on or any helpful tips. 
its been awhile since i've used linux but i am pretty computer savvy and will catch on quite quick

---

### Post by Keiran230 on 2011-02-18
I don't know of any particular sites with good documentation on it, but with hosting a web server using Ubuntu, these are a few pointers to get you started.

[LIST=1]
[*]The most popular web server (on Earth) is Apache, which works on Ubuntu.
[*]While Ubuntu will create a capable server, it is vastly preferred to install Ubuntu Server edition. Ubuntu Server does NOT have a graphical interface, however, and you should only do this if you can survive with seeing only a bash terminal. Without a GUI, Ubuntu Server spends more processing power on the Apache and less on X (the graphical environment).
[*]httpd is the name of the Apache daemon. Its configuration files will be in /etc/httpd (if I remember correctly) and the default directory for web files will be in /var/www
[*]Apache is an ancient program which is still actively developed, so you should be able to find documentation on it easily
[*]Important note: the /var and /etc directories are owned by root, which means the average user cannot copy or edit files in these directories. Use the sudo command to elevate yourself to root's privileges.
Ex: *sudo gedit <file>* or *sudo nano <file>* to edit files
Ex: *sudo cp ~/Desktop/file.htm   /var/www* to copy a file named file.htm on your desktop into the web doc directory
[*]To get more information on any of the commands I used above, use the man command. Ex: *man cp*
[*]If you're the graphical type, you can open a GUI with root privledges to the web doc directory by typing *sudo nautilus /var/www*
[/LIST]
-hope this helps

---

### Post by lisati on 2011-02-18
I notice this is posted in "Absolute beginners" instead of "Server platforms" - one of the staff can move it if you want.

There are some resources available at [http://www.ubuntu.com/server/technical-resources](http://www.ubuntu.com/server/technical-resources) that you might be interested in.

---

### Post by CharlesA on 2011-02-18
Just a note: most servers are run headless, so you don't need a GUI to run a web server.

You can configure a site by using a web interface such as webmin, or the others that are out there. You can also do it all CLI if you like.

My web development server is just a box running Ubuntu Desktop with LAMP installed on it.

---

### Post by asbloodrunsblack on 2011-02-18
whichever is the most appropriate location

---

### Post by asbloodrunsblack on 2011-02-18
Thanks keiran. idk if i'm fully comfortable operating linux without a GUI yet. i still had several issues in terminal before and always had to hit the forums to figure out what i needed. but i guess since i have multiple towers and laptops i could use server and just use another to figure out whatever i messed up lol

---

### Post by asbloodrunsblack on 2011-02-18
and charles do you have more info on LAMP?

---

### Post by CharlesA on 2011-02-18
> **asbloodrunsblack said:**
> and charles do you have more info on LAMP?
I know there is a ton of documentation out there, but the LAMP stack is fairly easy to install.

I'm not sure if this still works on 10.10, but it works on 10.04:

```
sudo tasksel
```

Select LAMP and hit ok.

See here: [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---


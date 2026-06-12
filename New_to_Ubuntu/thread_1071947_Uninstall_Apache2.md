---
title: "Uninstall Apache2"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by Al Fischer on 2009-02-16
I want my server to serve webs that I am building. My host uses Apache so I Googled and found Apache2. It installed with no problems. I now understand that it may not work in Ubuntu. Synaptics shows several packages for Apache and also lists Tomcat 5  5.5 and 6.

Do I remove everything that says Apache?  I didn't install anyting called Tomcat did itcome with the original install?
Do I need to do any config?

---

### Post by sandyd on 2009-02-16
whats wrong with apache?

works fine for me

to remove it

```

sudo apt-get remove paache2
sudo apt-get autoremove

```

but lets not be hasty! maybe your problem with apache can be fixed

---

### Post by punx45 on 2009-02-17
yeah, apache2 definitely works in ubuntu. if it didnt work you wouldnt be able to get it from the repos.   it does require some configuring, first though.

---

### Post by Al Fischer on 2009-02-17
Well, if both Apache2 and Tomcat are installed which is actually being used? When I access the server from my laptop it does say IT WORKS so which one is replying? In Windows I would look msconfig or startup but don't know if Linux has anything similar.

---

### Post by linux_tech on 2009-02-17
> **Al Fischer said:**
> Well, if both Apache2 and Tomcat are installed which is actually being used? When I access the server from my laptop it does say IT WORKS so which one is replying? In Windows I would look msconfig or startup but don't know if Linux has anything similar.

Open your browswer and go to
[http://localhost/](http://localhost/)
In terminal-
```

ps -ax |grep http

```

---

### Post by sandyd on 2009-02-17
> **Al Fischer said:**
> Well, if both Apache2 and Tomcat are installed which is actually being used? When I access the server from my laptop it does say IT WORKS so which one is replying? In Windows I would look msconfig or startup but don't know if Linux has anything similar.
apache 2 is replying.
tomcat defaultly operates on port 8080
while apache defaultly operates on port 80
by typing "localhost" you are accessing localhost:80

if your confused with managing all these different servers, try webmin
[http://webmin.org](http://webmin.org)

might help

---

### Post by Al Fischer on 2009-02-18
Thanks Carlee. So Apache seems to be working. Good!

I THINK the folder www is where a drive should be mounted for normal website files. What would I use for accessing from another desktop on my lan? [http://servername.www.drivename](http://servername.www.drivename)  ? assuming I had an index.html for the webste in the drive root.

---

### Post by spiderbatdad on 2009-02-18
on your lan, type the lan ipaddress into your browser.
the file /etc/apache2/sites-available-default is where server name is declared among other settings. Have a look at my basic guide:
[http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)

Also see community docs:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Al Fischer on 2009-02-18
SPIDERBATDAD, 

THATS exactly what I was looking for. Most of the details of specifics are not hard to Google but your view gives a better look at the overall. I'm sure you can tell I am just getting started at this Linux thing and it brings me back to my CPM and DOS 1.1 days. Enjoying it!

---

### Post by spiderbatdad on 2009-02-19
Welcome to the community!

---

### Post by Nausser on 2009-03-31
I finally uncovered how to completely re-install apache2 in intrepid Ibex

First to fully remove it: (If you currently have it removed improperly, reinstall it by "sudo apt-get install apache2".

Now type:
"sudo apt-get remove --purge apache2 apache2-utils"
This command will completely remove all apache2 configuration files and directories. (Apt was going to remove "/var/www/" however it saw that I had files in it so it left them behind.)

Now do your typical installation:
"sudo apt-get install apache2"

Now your config files and directories in /etc/should all be back and at their defaults as well as the "apache2-utils previously removed.

Hope this helps someone!

-Nausser

---

### Post by Al Fischer on 2009-03-31
The 'Completely remove' also does it as I found. Now back to setting it up. Somewhat confusing at MY level of understanding Linux.But the "Boss" says to fix the totally corrupted XP on our grandson's system firts. Oh. well...   (at least I am more knowledgeable there)

---

### Post by tin tin on 2012-05-22
> **Nausser said:**
> I finally uncovered how to completely re-install apache2 in intrepid Ibex

First to fully remove it: (If you currently have it removed improperly, reinstall it by "sudo apt-get install apache2".

Now type:
"sudo apt-get remove --purge apache2 apache2-utils"
This command will completely remove all apache2 configuration files and directories. (Apt was going to remove "/var/www/" however it saw that I had files in it so it left them behind.)

Now do your typical installation:
"sudo apt-get install apache2"

Now your config files and directories in /etc/should all be back and at their defaults as well as the "apache2-utils previously removed.

Hope this helps someone!

-Nausser
hi, 
thankyou this was very helpful for me!

---

### Post by oldos2er on 2012-05-22
Old thread closed; please don't bump old threads.

---


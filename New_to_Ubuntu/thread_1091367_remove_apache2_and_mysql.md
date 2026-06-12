---
title: "remove apache2 and mysql"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by funkyali on 2009-03-09
Hi 

How do I completely remove apache2 and mysql from my ubuntu 8.10 installation?

---

### Post by kanikilu on 2009-03-09
I think it should be ```
sudo apt-get purge mysql-server && sudo apt-get purge apache2
``` Or just search for them in Synaptic and mark for (complete) removal.

---

### Post by funkyali on 2009-03-09
Just seems to hang my the terminal window and the synaptic windows as well when I click apply

---

### Post by konqueror7 on 2009-03-09
try,
```

sudo apt-get autoremove --purge mysql-server
sudo apt-get autoremove --purge apache2
```

this will remove the app, its settings, and related packages installed...this is what i usually do with my apps, but you can replace 'autoremove' with 'remove' only...

---

### Post by kanikilu on 2009-03-09
So no errors, it just hangs?

Have you tried stopping the related services before removing?

```
sudo /etc/init.d/mysql stop
sudo /etc/init.d/apache2 stop
```

How did you install the packages? If you used the "LAMP Server" [task selection](https://help.ubuntu.com/community/Tasksel), you might want to try doing ```
sudo tasksel
``` and remove the asterisk next to the LAMP Server item.

---

### Post by funkyali on 2009-03-09
i installed it using task selection.

I tried the following you will see I managed to stop mysql but I could not remove it and I could not stop apache2

```
user-laptop:~$ sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                                 [ OK ] 
user-laptop:~$ sudo /etc/init.d/apache2 stop
 * Stopping web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting .                                                           [ OK ]
user-laptop:~$ sudo apt-get autoremove --purge mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic mysql-server-5.0
The following packages will be REMOVED
  linux-headers-2.6.27-7* linux-headers-2.6.27-7-generic* mysql-server*
  mysql-server-5.0*
0 upgraded, 0 newly installed, 4 to remove and 14 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory 

```

Forgot to mention that I did the sudo tasksel and just left me with a blinking cursor

---

### Post by kanikilu on 2009-03-09
> E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Sounds like something is running elsewhere or hung up. You might want to try ```
sudo pkill apt
``` before trying that again. You may want to pkill apache2 as well if it won't shutdown gracefully...

---

### Post by funkyali on 2009-03-09
> **kanikilu said:**
> Sounds like something is running elsewhere or hung up. You might want to try ```
sudo pkill apt
``` before trying that again. You may want to pkill apache2 as well if it won't shutdown gracefully...
I did as you suggestted but it still leaves me with a blinking cursor on a new line after the confirmation

```

user-laptop:~$ sudo pkill apt
[sudo] password for user: 
user-laptop:~$ sudo pkill apache2
user-laptop:~$ sudo apt-get autoremove --purge mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic mysql-server-5.0
The following packages will be REMOVED
  linux-headers-2.6.27-7* linux-headers-2.6.27-7-generic* mysql-server*
  mysql-server-5.0*
0 upgraded, 0 newly installed, 4 to remove and 14 not upgraded.
After this operation, 140MB disk space will be freed.
Do you want to continue [Y/n]? Y
[COLOR="Red"]<BLINKING CURSOR>[/COLOR]

```

Where I placed the wording BLINKING Cursor is where it just leaves me I have to close the terminal window and start again.

---

### Post by funkyali on 2009-03-09
bump....

---

### Post by kanikilu on 2009-03-09
Sorry, I'm out of ideas. I think the only other thing I would try is maybe booting into recovery mode and trying it from there :confused:

---

### Post by Nxion on 2009-03-09
Try it this way:

```
sudo apt-get remove apache2 && sudo dpkg --purge apache2
``````
sudo apt-get remove mysql-server && sudo dpkg --purge mysql-server
```

Any luck?

---

### Post by konqueror7 on 2009-03-09
try doing it in the virtual terminal, press, ctrl + alt + f1,,,see if that helps, i don't know really why your systems seems to hang but, what is the specs of your computer?

---

### Post by Nxion on 2009-03-10
The specs of the machine shouldn't really matter. Ubuntu is meant to run on anything really. When you get to the point you have a blinking courser Can you see any activity on the machine? Meaning is the status light flashing on your machine? can you here the computer chugging away? or is it silence?

---

### Post by konqueror7 on 2009-03-10
yes, ubuntu is meant to run on most machines, but then it has also limitations, that's why you have other distros and derivatives for this cases...but anyway, just check what he says if your PC is really processing or not...

---


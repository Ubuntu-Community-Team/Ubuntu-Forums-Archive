---
title: "Installing server files on the Desktop version??"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by macmike on 2010-05-06
Hi I am new at Linux. I am A+ certified as well as Net+ certified. I am trying to set up a Web Server to host 2 Websites and a Mailing list want th use mail man for that. I at first installed the Server version of Ubuntu 10.04 LTS 32 bit version. Didn't get a GUI interface. So installed the Desktop version hoping I can install the server files to get this program going. Is there any way to install what I need into the desktop version?

Mike Hughes
mail<at>mikealrhughes<dot>com

---

### Post by nathan726 on 2010-05-07
You'll want to open the terminal (Applications > Accessories > Terminal) and type the following:
```
sudo apt-get install lamp-server^
```Note: the caret '^' symbol is essential.

There is a nice tutorial here:
[http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/)

---

### Post by 3rdalbum on 2010-05-07
Yes, just look in Synaptic Package Manager for whatever services you want to install.

There is a single command that installs Apache (web server), PHP and MySQL; it's:

```
sudo tasksel lamp-server
```

---

### Post by Abera on 2010-05-21
> **3rdalbum said:**
> Yes, just look in Synaptic Package Manager for whatever services you want to install.

There is a single command that installs Apache (web server), PHP and MySQL; it's:

```
sudo tasksel lamp-server
```

I keep seeing this, but can't find a good answer. I want to know if I can have both Desktop and the LAMP server with one box? I just set a box up with 10.4 Desktop. If I use the tasksel, will this kill my Desktop? I need both. Thanks

---

### Post by louieb on 2010-05-21
> **Abera said:**
> I want to know if I can have both Desktop and the LAMP server with one box? 

Yes, I've done just that. :)  

Really does not matter - install the Desktop 1st - then add the Lamp and whatever else servers you want.  

As long as your hardware is good enough - should run just fine.

---

### Post by Abera on 2010-05-21
> **louieb said:**
> Yes, I've done just that. :)  

Really does not matter - install the Desktop 1st - then add the Lamp and whatever else servers you want.  

As long as your hardware is good enough - should run just fine.
Thank you... Which of these do I use?

sudo tasksel lamp-server

Or

sudo apt-get install lamp-server^

Thanks again

---

### Post by louieb on 2010-05-22
Don't know that it matters. For what its worth I use - note the install option was missing from the previous post.

```
sudo tasksel install lamp-server
```

Once installed - heres a good start to get it configured. [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Abera on 2010-05-22
> **louieb said:**
> Don't know that it matters. For what its worth I use - note the install option was missing from the previous post.

```
sudo tasksel install lamp-server
```Once installed - heres a good start to get it configured. [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")
While looking around, I also found this. It takes the config out and does it itself and worked good. > 
By Phillw
As of 9.10 the correct way to put on a LAMP server is as follows

  Code:
    sudo tasksel



Arrow down to LAMP, press the space bar to put an * in the box, press the tab bar to get to <OK> and press enter. Then do as it says & make a note of your MySQL root password

Then, go into System --> Administration --> Synaptic Package Manager
Type in phpmyadmin in the search window, right click on the little box to the left of phpmyadmin in the results area, select install, then click on 'Apply'. Do as it says. (Obviously, when asked, tell it you are using Apache).

Then reboot. You now have a full LAMP installation with PhpMyAdmin on it - all configured up.My only problem is permissions. I can't move anything too the WWW dir. Says I'n not the owner?:confused:
Thanks

---

### Post by bodhi.zazen on 2010-05-22
You really do no tneed Gnome desktop on a server.

Most of the management of a Linux server is either editing config files or starting / stopng services all of which can be done from the command line or over ssh.

If you want a graphical fron end, I suggest you look at webmin. Here is a guide, written for Debian, but applies to Ubuntu as well.

[http://woodel.com/](http://woodel.com/)

If you are new to Linux you have some reading to do re- sys admin, permissions, etc.

For a server guide I suggest you start with :

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions")

---


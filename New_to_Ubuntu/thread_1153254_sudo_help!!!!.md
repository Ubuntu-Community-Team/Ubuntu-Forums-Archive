---
title: "sudo help!!!!"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by pendulum101 on 2009-05-08
im having trouble editing files in my /var directory , i know i need administrative priviliges to edit it but i need a little help using sudo. basically what command do i need to be able to edit secured files (i need to edit var/www for php college)

please feel free to add any other useful tips onto any replies, im eager to learn ubuntu 8.10's full potential (any handy )terminal commands

---

### Post by Niniel on 2009-05-08
Open a terminal window and enter "gksudo application name", that will start the program with root privileges. 
E.g. "gksudo nautilus" opens a root-enabled file manager window. That's easiest but maybe a little dangerous. 
You can also just open a root enabled text editor (gedit).
There is a way to add "Open as root" to your context menu or open a root terminal in the folder you are in, but you will have to search the forums for that because I can't remember the name of the software right now that manages this.

---

### Post by wizard10000 on 2009-05-08
> **pendulum101 said:**
> im having trouble editing files in my /var directory , i know i need administrative priviliges to edit it but i need a little help using sudo. basically what command do i need to be able to edit secured files (i need to edit var/www for php college)

please feel free to add any other useful tips onto any replies, im eager to learn ubuntu 8.10's full potential (any handy )terminal commands

Easiest way to do this?  Or at least what I think is the easiest way?

Create a launcher using this command line -

gksudo nautilus /

That'll give you a nautilus window with root privileges - then all you have to do is navigate to /var/www and edit away  ;-)

Another way to do it is to just run

gksudo gedit

and you can drag stuff from any nautilus window into the editor and you'll be editing as root.

---

### Post by jflaker on 2009-05-08
> **wizard10000 said:**
> Easiest way to do this?  Or at least what I think is the easiest way?

Create a launcher using this command line -

gksudo nautilus /

That'll give you a nautilus window with root privileges - then all you have to do is navigate to /var/www and edit away  ;-)

Another way to do it is to just run

gksudo gedit

and you can drag stuff from any nautilus window into the editor and you'll be editing as root.

One thing to note:
You are in nautilus as root..you have access to change and/or delete anything you want...**USE EXTREME CAUTION**

---

### Post by halitech on 2009-05-08
if you just want to edit files in /var/www then you can do 1 of 2 things

```
gksudo gedit /name/of/file/to/edit
```or ```
sudo nano /name/of/file/to/edit
```

the first will open gedit, the second will do it in a terminal

---

### Post by wizard10000 on 2009-05-08
> **jflaker said:**
> One thing to note:
You are in nautilus as root..you have access to change and/or delete anything you want...**USE EXTREME CAUTION**

Yup.  This can't be overstated.

---

### Post by pendulum101 on 2009-05-08
yes of course i would bear in mind that using gksudo would give me probably far too much power but i just need a solution for the moment thanks for the help

---

### Post by pendulum101 on 2009-05-08
hey one more question what is the difference between gksudo and sudo if there is any

---

### Post by Niniel on 2009-05-08
gksudo opens the graphical password prompt, with sudo you'll have to enter your password in the terminal window

---

### Post by Elfy on 2009-05-08
> **pendulum101 said:**
> hey one more question what is the difference between gksudo and sudo if there is any

Use sudo for terminal and gksudo (or kdesu in kubuntu) for graphical apps - [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by pendulum101 on 2009-05-08
thank you v.much

---

### Post by neu2buntu on 2009-05-08
to edit/change any files other than in your ~/ home dir you will need root priviledges,so get used to doing this.the main thing to remember is to exit as soon as you have done your editing.
  the difference between "gksu" and "sudo" commands is gksu (the root environment) quits instantly whereas sudo keeps the root environment alive for longer(giving a gateway to potential hackers)   to be honest i have used the gksu nautilus command on occasion but would not reccomend it for new users,as you can easily damage your system.    

use man [name of command or package] to find out more options examples:--- ```
man bash 
``````
man sudo
``` ```
man gksu
``` obviously you know to do these commands in the terminal (applications>accessories>terminal):guitar:

---


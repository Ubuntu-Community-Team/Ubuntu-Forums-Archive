---
title: "Starter Query"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by carparknz on 2009-12-31
Hi All
I have been trawling through pages and pages about Linux and tried a few versions, which did not encourage me greatly. Looking at Ubuntu gives me some hope.
I'm about to give Ubuntu Server Edition a trial and if I may ask some simple questions to get me started.  I'd like to drop all my MS Windows server software and run Linux.
While all my network PC's still run Windows XP, what horrors am I likely to encounter.
   a. What Linux software is available for email servers, currently running Mercury 
   b. Software for PC data and backup servers
   c. Remote log on and maintenance to servers
   d. Local network intranet and test web server  
   e. Seamless operation between current PC'c and linux

As you can see I'm a newbie at this, even after a month of trials and tribulations. 
Any help or suggestions are sincerely and greatfully appreciated.

Best to all

Colin   :redface:

---

### Post by tenach on 2009-12-31
I'll answer as best I can:

Mail server: [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

Backing up your server can go a few ways:
  [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)
  [http://dirvish.org/](http://dirvish.org/) (I use dirvish, it is pretty good)

Remote logon is easy; make sure you install OpenSSH and then you can just ssh into your server. LAMPP takes care of a local web server, and samba works great for having your server share files with Windows, Mac, and Linux boxes.

What do you mean by 'seamless operation' ?

---

### Post by durand on 2009-12-31
Just know that with an ubuntu server install, you don't get a graphical install automatically since a server isn't meant to be accessed directly. (Apparently windows servers do come with a GUI) If you do want to install a gui, that is very straightforward. Just ask here.

Apart from that, ubuntu is great as a server, provided that you read up on what you are doing. The links above and this one should help: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Oh and that poll wouldn't really be very useful to you. This is an ubuntu forum, there will be bias ;)

---

### Post by k64 on 2009-12-31
> **carparknz said:**
> Hi All
I have been trawling through pages and pages about Linux and tried a few versions, which did not encourage me greatly. Looking at Ubuntu gives me some hope.
I'm about to give Ubuntu Server Edition a trial and if I may ask some simple questions to get me started.  I'd like to drop all my MS Windows server software and run Linux.
While all my network PC's still run Windows XP, what horrors am I likely to encounter.
   a. What Linux software is available for email servers, currently running Mercury 
   b. Software for PC data and backup servers
   c. Remote log on and maintenance to servers
   d. Local network intranet and test web server  
   e. Seamless operation between current PC'c and linux

As you can see I'm a newbie at this, even after a month of trials and tribulations. 
Any help or suggestions are sincerely and greatfully appreciated.

Best to all

Colin   :redface:

There is absolutely nothing in Windows or Mac OS X that can't be done in Ubuntu (or any Linux). Just think: GNOME Shell's Alt+Tab has the same features as Windows 7's Taskbar and OS X Snow Leopard's customized Expose-integrated Dock. GNOME Shell's Activities overview is like Windows 7's Jump Lists feature: When you right-click on an application icon, you get a window menu appearing in a quote box. The Calendar and Calculator are in there, and have been for years before Windows 7. And Ubuntu Linux is the only OS that comes with a productivity suite and image editor right out of the box.

---

### Post by carparknz on 2009-12-31
Thanks all for your responses.
I'll certainly take note do some more reading on systems available.
I'm still not up with all the direct command inputs so I'll have to go with a GUI option.
By seamless, I was meaning building a server and transfering files, etc without the network PC's knowing changes had been made.
And as for the poll, yes, a bit of a tongue in check knowing the question asked.
Hey, thanks all, I'm moving forward already.
Season best  :cool:

---

### Post by tenach on 2010-01-01
I hope that you find what suits you! :)  I started out going GUI all the way too, but eventually I had to learn a bit of the command line.  It is really the most powerful tool at your disposal, if you take the time to learn it.

Samba should take care of your file transferring needs, and is easy to get going.

Best wishes on your hunt!

---

### Post by carparknz on 2010-01-01
Thanks Tenach
I have been putting off setting Linux because of the many variations. Looking back and allowing myself a month to setup at least one server from zero was in hindsight a bit naive in the Linux world. However I'm determined to carry on. Thanks for your input.

---

### Post by tenach on 2010-01-01
You are very welcome!

I remember going through something similar when I was building myself my first Linux computer.  Hope to see you around!

---

### Post by carparknz on 2010-01-01
Hi Tenach
I've been around computers since the day Sinclar (UK), Apple and others went public, but teco is increasing faster than I'm growing old. Learning new systems when the only hair on the head is grey takes a bit longer. There may be many questions to come. Thanks for your support.
best regards

---

### Post by tenach on 2010-01-01
Well, ask away when you have questions, and I'm sure that if I don't answer, one of the many people on this forum will be more than willing to help you out :D  The biggest thing that has kept me with Ubuntu is the fact that the community treats everyone like people.  There's less of the "holier-than-thou" here than other places, though it does still exist.

---

### Post by halitech on 2010-01-01
If you want to put the server away somewhere and mostly forget about it with just a little tweaking here and there, go with just the server install and then install EBox ( [http://www.ebox-platform.com/](http://www.ebox-platform.com/) ) and administer the server with a web browser.

---

### Post by tenach on 2010-01-01
Thanks for the link halitech!  I haven't heard of that and have been looking for something of that sort.

---


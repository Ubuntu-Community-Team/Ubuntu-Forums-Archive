---
title: "[SOLVED] Network Scanner"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by lmlypfan on 2007-08-10
I posted this at the beginner section, but couldn't find an application to fit my needs.

In windows I used a LAN scanner that gave me the IP addresses of all computers on my network, as well as the operating system.   Look@LAN was the application.  

Is there one for ubuntu?  

I found nbtscan, but its info is limited.

Thanks

---

### Post by mike102282 on 2007-08-10
> **lmlypfan said:**
> I posted this at the beginner section, but couldn't find an application to fit my needs.

In windows I used a LAN scanner that gave me the IP addresses of all computers on my network, as well as the operating system.   Look@LAN was the application.  

Is there one for ubuntu?  

I found nbtscan, but its info is limited.

Thanks
Did you try sudo ifconfig?

---

### Post by lmlypfan on 2007-08-10
Doesn't that give me info on just my machine, and not others on the network?

I ssh'ed in from work, and ran sudo ifconfig, and only got info for that machine. 

I can't remember if the other machines are booted, but I think at lease one is.

---

### Post by lmlypfan on 2007-08-11
I found a great application.  AutoScan

[http://www.gnomefiles.org/app.php/AutoScan](http://www.gnomefiles.org/app.php/AutoScan)

---

### Post by afzalnaj on 2007-08-12
another one here [http://www.ntop.org/download.html](http://www.ntop.org/download.html)

---

### Post by Apex-jb on 2007-08-14
Could someone tell me how to install AutoScan? Its not in the package manager.

---

### Post by lmlypfan on 2007-08-14
Download the Linux binary here:  [http://www.gnomefiles.org/app.php/AutoScan](http://www.gnomefiles.org/app.php/AutoScan)

You should be able to just double click and install

---

### Post by Apex-jb on 2007-08-15
Thanks. I got it installed but now whenever I try to create a network I get this

> Connecting 127.0.0.1... FAILED

---

### Post by lmlypfan on 2007-08-16
I didn't change any of the default settings, and it worked fine. 
I think there is a "connect to local machine" or "local area network" drop down menu you can use.  

Thats about the best I got.  I have only played around with it a couple of times, but once its up, its a pretty sweet app.

---

### Post by Apex-jb on 2007-08-16
Cant find a drop down menu. I run the network wizard and when it comes up with the "Where is located the network", I click "local host" and then I get that error.

---


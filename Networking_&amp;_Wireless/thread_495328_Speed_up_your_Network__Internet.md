---
title: "Speed up your Network / Internet"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by taylorsnow on 2007-07-07
Ok so this is a two step process. Step one being to rebuild your TCP/IP Stack, and step two we will use the new Open DNS servers.

**[SIZE="3"]Step One:[/SIZE]**

Open Terminal and run
*sudo gedit /etc/sysctl.conf*

Replace the text in the"sysctl.conf" with the text from this website
[http://www.rubyringtechnologies.com/files/sysctl.conf.txt](http://www.rubyringtechnologies.com/files/sysctl.conf.txt)
Save and Exit

Make the new changes effective immediately by typing
*sudo /sbin/sysctl -p*

Now flush the routing table to make some of these changes happen instantly
*sudo /sbin/sysctl -w net.ipv4.route.flush=1*


Step Two

Replace your DNS servers that your ISP gives you with the ones provided from OpenDNS.org
Follow the easy instructions on their website here
[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)

Play around and look around, you should see a large difference from both... i noticed a huge change from [www.myspace.com](www.myspace.com).... good luck

---

### Post by steveneddy on 2007-07-07
Isn't this basically for servers to serve the date or content more efficiently?

---

### Post by AnthonyT on 2007-07-07
Yes this is usually a server tweak, but it can be used on the desktop level, and you should see a performance increase.

The OpenDNS is for the desktop, and yes it does make a difference.

Thanks,

Anthony

---

### Post by kevdog on 2007-07-07
I used OpenDNS for awhile, I didnt see any difference in speed.  In fact it screwed up my Samba settings when coupled with winbind.  I couldnt query any longer by machine name -- in fact smbtree command would work any longer.  I wrote the people at OpenDNS and in order to solve the problem they recommended I sign up for an account.  I thought the whole point about OpenDNS was that it was free, but it really was not if I wanted smb functionality.

Oh well, back to what I had before without any loss in performance.

---

### Post by sabitha on 2007-07-08
> **taylorsnow said:**
> Ok so this is a two step process. Step one being to rebuild your TCP/IP Stack, and step two we will use the new Open DNS servers.

**[SIZE="3"]Step One:[/SIZE]**

Open Terminal and run
*sudo gedit /etc/sysctl.conf*

Replace the text in the"sysctl.conf" with the text from this website
[http://www.rubyringtechnologies.com/files/sysctl.conf.txt](http://www.rubyringtechnologies.com/files/sysctl.conf.txt)
Save and Exit

Make the new changes effective immediately by typing
*sudo /sbin/sysctl -p*

Now flush the routing table to make some of these changes happen instantly
*sudo /sbin/sysctl -w net.ipv4.route.flush=1*


Step Two

Replace your DNS servers that your ISP gives you with the ones provided from OpenDNS.org
Follow the easy instructions on their website here
[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)

Play around and look around, you should see a large difference from both... i noticed a huge change from [www.myspace.com](www.myspace.com).... good luck

i need restart to take the changes or what ...:confused:

---

### Post by sabitha on 2007-07-08
> Make the new changes effective immediately by typing
sudo /sbin/sysctl -p
forgot that i dont see this :)

---

### Post by AnthonyT on 2007-07-08
> Make the new changes effective immediately by typing
sudo /sbin/sysctl -p

Now flush the routing table to make some of these changes happen instantly
sudo /sbin/sysctl -w net.ipv4.route.flush=1

Nope, you can if you want to.

Anthony

---

### Post by sabitha on 2007-07-08
can i use this for my squid server so it become more reponsive

---

### Post by leksdraven on 2007-07-08
I only saw a marginal increase in speed: 1.36 MB/S to 1.39 MB/S. Average.

---


---
title: "I've made the switch.  Now I need help!"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by stuboo on 2006-08-01
My wife and I spent the better part of 2 months remodeling a house we bought last year and one of my requirements was that everything be networked.  Every room has cat5e cable ports.  A few months ago I got around to building installing an Ubuntu server (breezy) and got it set up as a file server that uses Samba to connect to my windows machines.

Two weeks ago, my Windows XP decided it would go into a continuous reboot.  I got pissed, loaded up Damn Small Linux to get my files, bought a new HDD and installed Kubuntu (Dapper).  So far, I love it.  I've learned a great deal.

Here's what I need to do now . . .

I want to set up my fileserver to be an intranet/testing server as well - so I can do web development on any computer in the house.  I'd like to use Apache, PHP, MySQL with SVN (for starters).

I've not had any luck at all following the how to's on howtoforge.  If someone could point me in the right direction, I'd really appreciate it.

I think my biggest problem is that my machines aren't talking to each other correctly (or that it's been so long since I followed the recipe to set up samba, that I've forgotten many of the details).

Thanks in advance for your help.

Ryan

---

### Post by tkjacobsen on 2006-08-02
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) is a good wikipage to get startet with apache mysql and php

Havent tried svn myself, but here's the wiki:
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

---

### Post by shingalated on 2006-08-03
Apache and PHP can be easily installed with synaptic package manager or apt-get

---

### Post by stuboo on 2006-08-03
> **shingalated said:**
> Apache and PHP can be easily installed with synaptic package manager or apt-get
I'm confident in my ability to install apache/php/mysql on the server.  What I'm not sure how to do is configure it so that I can access that server from the other machines on my network.

I have 3 machines
1. Server (ubuntu breezy, headless)
2. Laptop (WinXP)
3. Desktop (kubuntu dapper, KDE)

I want to be able log open firefox on either my desktop or laptop and goto [http://myhomeintranet/](http://myhomeintranet/)  (or something similar) so that i can test php projects on it.

Thanks for the help thus far.  I'll tackle SVN after I get the other things up and running.

---


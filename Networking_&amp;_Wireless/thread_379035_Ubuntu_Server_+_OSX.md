---
title: "Ubuntu Server + OSX"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by lenwood on 2007-03-08
Hi All,
I set up a headless LAMP server using Ubuntu server a couple of weeks ago, and have had great success using it with my WinXP laptop. I installed Webmin and a couple of other web pages for controlling the system, I pull them up with a static index.htm file that I created on the system. I open [http://ubuntu/](http://ubuntu/) in my browser, and get busy. I works great.

I bought a Mac over the weekend, and I can only access the Ubuntu system with its IP address. If I put in the name of the system into my browser, some Chinese Linux page comes up (??). The Mac can resolve every other system name on my network, but not the Ubuntu system.

Can anyone help? Do I need to somehow tell my Mac that 'Ubuntu' is a trusted computer on my network?

Thanks,
Len

---

### Post by netztier on 2007-03-08
> **lenwood said:**
> 
I bought a Mac over the weekend, and I can only access the Ubuntu system with its IP address. If I put in the name of the system into my browser, some Chinese Linux page comes up (??). The Mac can resolve every other system name on my network, but not the Ubuntu system.

Well - what answer does the Mac get when you ask it to resolve the unqalified hostname "ubuntu"? Where does it get that answer from? What domain suffix does the Mac append to the hostname when trying to reolve "ubuntu"?

How do you provide name resolution for your local subnet? 

best regards

Marc

---

### Post by lenwood on 2007-03-10
After giving this some thought, I don't have any name resolution on my little network. I guess the WinXP machine was doing it through WINS. Does anyone have a recommendation for the best way of doing this? My primary system is now the Mac, and I need access to the Ubuntu system by its name. Routing is handled by a Linksys WRT54G. Is there a way for me to set the WRT54G to do this?

Thanks,
Len

---


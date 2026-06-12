---
title: "I want to make a linux router, need advice"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by tuproxy on 2007-12-14
I'm interested in making a wireless, gigabit router from a Dell P3 1Ghz, 376mg ram.

I would like to make this router with Ubuntu and am looking for suggestions. 

What other options can I have with a linux router?  Can I set it up to allow VPN connections?  What about VoIP?

I would possibly like to make this computer a small web server and ftp server.  

Could someone point me to a good guide that will walk me through this process?  Is it worth using this PC as a router over something that is a consumer router ($40-70 linksys or Belkin)

I just want to have something that is very reliable, solid and secure.

Please opinions!  Thank you!

---

### Post by mellowd on 2007-12-14
You can set it up as a router but to be honest if all you want is basic routing it's a lot easier to just install a consumer router

---

### Post by tuproxy on 2007-12-14
I have used Linksys WRT54g's and they all have crapped out over time. I was hoping for something a little more robust and learn about Linux at the same time.  

Is the Linux router much better than a consumer router?

---

### Post by mellowd on 2007-12-14
It depends on how much you want to do with it. Running a computer with linux is sucking an awful lot of power if its just routing. It's a lot more flexible and you can do all kinds of things with it so it realyl depends on how much you want it to do

---

### Post by tuproxy on 2007-12-14
I'm thinking of making it a web server and maybe a music server as well.  

Do you know of any good tutorials to set up my box as a router?

---

### Post by mellowd on 2007-12-14
I haven't actually done it yet, but I've come accross this tutorial. Can't say if it actually works though: [http://www.lab4games.net/zz85/blog/2006/09/18/turning-my-linux-server-into-a-router/](http://www.lab4games.net/zz85/blog/2006/09/18/turning-my-linux-server-into-a-router/)

---

### Post by Peter76 on 2007-12-15
Do a forum serach on 'sharing internet connection' in the how to section; I remeber there's a good guide there... ( connection sharing involves routing ). Setting up your own router and server is a great learning project, although I have to agree with mellowd on the bigger power consumption:-)
Also post a bit more about exactly what you want to do; somebody ( likely not me :-) ) might help

---

### Post by emil.s on 2007-12-15
I'm using shorewall:
[http://www.shorewall.net/](http://www.shorewall.net/)

This howto helped me to setup the perfect router/firewall:
[http://www.shorewall.net/GettingStarted.html](http://www.shorewall.net/GettingStarted.html)

And the manual is really good. :) Can't bee easier, enjoy! :)

---

### Post by tuproxy on 2007-12-15
thanks for the updates. I'll check them out.

---

### Post by dragon_788 on 2007-12-29
You could also look into the WRT54GL (the L is the important part) its a Linksys router that runs Linux itself, it can be modified to run a custom version of Linux with extra features too. Otherwise I've found them to be pretty solid hardware wise, and the firmware updates are pretty stable too.

---

### Post by Furat on 2007-12-29
If you want to use your P3 Box as a dedicated router you can use [IPCOP]("http://www.ipcop.org"), which I used for along time and it is very good router specially  if you install its plugins .
I you want to use it as web server, music server and router I think you can install "Zero Touch Linux"  which never try before. 
one last think , it is strongly not recommended to install  web server or File server on the routers

---

### Post by cdtech on 2007-12-29
This is the procedure I used to set up my server (which sounds like what you want to do). I now have a router, web server, and storage stored away in a closet using shorewall as my firewall.

[[COLOR="DarkRed"].:: the perfect setup ::.[/COLOR]]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")

Hope this helps.

---


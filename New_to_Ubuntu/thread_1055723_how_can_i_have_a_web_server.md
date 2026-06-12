---
title: "how can i have a web server?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by ja660k on 2009-01-31
hey guys, im wondering how i can have a web server so that people from somewhere else can open browser and put in my ip and BAM my site...

i have apache and php and stuff, but how do i put it on the net?

---

### Post by lykwydchykyn on 2009-01-31
You need to access the configuration on your router and forward a port to your server.  If you have a standard home ISP account, they probably block port 80 (web port), so you may need to forward some higher port to your box.

You might want to be aware that some ISPs specifically prohibit running a web server, so it'd be worth checking on that to know what risks you are taking.

---

### Post by fortyqueue on 2009-01-31
start apache

```
sudo /etc/init.d/apache start
```

if you are on a router, open port 80 to your box.

I'd recommend getting a readable url from [http://www.dyndns.com/]("http://www.dyndns.com/").

That should be it.  I think ubuntu's folder to hold your page and materials is in /var/www

---

### Post by Sorivenul on 2009-01-31
A lot depends on your setup... 

Are you behind a firewall, is a proxy involved, do you use a router or not, etc.?

An excellent guide is available from HowToForge, in versions for Hardy or Intrepid:
[The Perfect Server (Hardy Heron 8.04)]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")
[The Perfect Server (Intrepid Ibex 8.10)]("http://www.howtoforge.com/perfect-server-ubuntu-8.10")

If you have specific server related questions, better answers will probably come from the [Server Platforms subforum]("http://ubuntuforums.org/forumdisplay.php?f=339").

Hope this helps! Good luck!

---

### Post by ja660k on 2009-01-31
thanks... i dno what ports are open nor do i know how to open them

---

### Post by Sorivenul on 2009-01-31
> **ja660k said:**
> thanks... i dno what ports are open nor do i know how to open them
The links I provided should have how to do so somewhere in the tutorials. However, [PortForward.com]("http://portforward.com/") has detailed instructions for many routers.

---

### Post by ja660k on 2009-01-31
allright, well if i run into problems ill be back :) thanks guys

---

### Post by IEKnight on 2009-01-31
Hope this helps:
[LIST=1]
[*]Navigate to your router's configuration panel
[*]If computer has a static IP address then go to next step. If not, use the reserved IP list function to ensure that your computer is always assigned the same IP.
[*]In the port forwarding section of the router's configuration, set TCP port 80 to be forwarded to you computer's IP at port 80
[/LIST]

Hopefully you're all set.

btw, a great tool for configuring apache is _[Webmin]("http://www.webmin.com")_.

good luck

---

### Post by 3rdalbum on 2009-01-31
And put your HTML files into /var/www :-)

---

### Post by Sorivenul on 2009-01-31
> **3rdalbum said:**
> And put your HTML files into /var/www :-)
This is probably pretty important. :) Otherwise all people would see is "It works!".

---

### Post by ja660k on 2009-02-02
> **IEKnight said:**
> 
[LIST=1]
[*]Navigate to your router's configuration panel
[*]If computer has a static IP address then go to next step. If not, use the reserved IP list function to ensure that your computer is always assigned the same IP.
[*]In the port forwarding section of the router's configuration, set TCP port 80 to be forwarded to you computer's IP at port 80
[/LIST]


having a bit of a problem, as far as i know i forwarded the port to my "server"

as seen in the attatchment, 
but i think i have a dynamic ip...
but when i set it to static i dont get internet

so i dont know what to do..?

---


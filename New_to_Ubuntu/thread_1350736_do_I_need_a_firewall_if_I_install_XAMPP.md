---
title: "do I need a firewall if I install XAMPP?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by bob12564 on 2009-12-09
I'm trying to wean myself from Windows gradually and the next project is to install a development server on my Jaunty/9.04 desktop.  I'm a programmer and I need a test environment but I'm not interested in becoming a network administrator.  I'm using WAMP on my Windows box and XAMPP seems to be a good Linux replacement.  

Do I need a firewall if I install XAMPP?  I don't want any outside access to the XAMPP environment and most of the time it will be shut off unless I'm testing program code.  My Ubuntu box is also be connected to a DSL router/modem that contains a firewall.  I have used websites like ShieldsUp to test security and they show all ports as closed but visible.  Would that change if I install XAMPP?

I appreciate any newbie plain English advice.

---

### Post by lovinglinux on 2009-12-09
> **bob12564 said:**
> Do I need a firewall if I install XAMPP?  I don't want any outside access to the XAMPP environment and most of the time it will be shut off unless I'm testing program code.

XAMPP has an option to limit the connections to the loopback. I guess that should be enough, although I also block it with firewall rules (Windows reminiscent paranoia).

> **bob12564 said:**
> My Ubuntu box is also be connected to a DSL router/modem that contains a firewall.

If you don't open the port in the router, then you don't need a firewall on your machine.

> **bob12564 said:**
> I have used websites like ShieldsUp to test security and they show all ports as closed but visible.  Would that change if I install XAMPP?

It will show as open only if you forward port 80 from the router to your machine. 

What result do you get from [http://canyouseeme.org](http://canyouseeme.org) ?

---

### Post by bob12564 on 2009-12-10
Thanks for the reply.  I tried canyouseeme.org as you suggested with the ports listed on that page.  All came back as unseen/connection denied.

I tried shieldsup at grc.com and tested common ports which came back as "Your computer has responded that this port exists but is currently closed to connections."

I think you're saying that the DSL modem/router firewall is sufficient and that if I install XAMPP I'll still be safe.  Is that correct?

I'm still not clear if XAMPP will be opening a port.  I know that some people try to use it to host websites that are open to the public but I only want it running locally and closed to the outside world.  I hope you can clarify this further.

BTW, I know what you mean about Windows paranoia.  I've been using Ubuntu casually for about 2 years but I am now seriously attempting to use it full time.  I am comfortable that Linux is much safer than Windows but I know that running a server is sometimes dangerous.

---

### Post by lovinglinux on 2009-12-10
> **bob12564 said:**
> I think you're saying that the DSL modem/router firewall is sufficient and that if I install XAMPP I'll still be safe.  Is that correct?

Yes. As long as you don't forward port 80 from the router to your machine, all connection attempts will be refused. 

If using a local firewall will give you some peace of mind, go ahead and close the port on the firewall. Nevertheless, this is not necessary if you don't forward the port from the router. Nobody outside your local network will be able to reach your web server. 

> **bob12564 said:**
> I'm still not clear if XAMPP will be opening a port.  I know that some people try to use it to host websites that are open to the public but I only want it running locally and closed to the outside world.  I hope you can clarify this further.

XAMPP will be listening on port 80 so you can connect to your web site locally and thus the port will be "opened". But since you are not forwarding the port from the router, the outside world will see it as closed. The connections wil stop at the router. 

Just to make sure you have the correct settings on your router, start XAMPP and test if you can connect using [http://localhost](http://localhost). Then visit one of those firewall testing sites and scan your port 80 or any other port you used in XAMPP configuration. If the results says the port is closed, unseen or unreachable, then you are fine. 

> **bob12564 said:**
> BTW, I know what you mean about Windows paranoia.  I've been using Ubuntu casually for about 2 years but I am now seriously attempting to use it full time.  I am comfortable that Linux is much safer than Windows but I know that running a server is sometimes dangerous.

The danger of of running a server depends on the type of server and the security of the application. For example running a VNC server (Remote Desktop) opened to the outside world is definitely dangerous, while running a BitTorrent client not so much. They are both servers, because they listen to certain ports and accept unrequested remote connections. But the VNC server is dangerous by itself, because it allows anyone with authentication rights to fully control your machine, while the BitTorrent application only allows to download files specified in your torrents. To be a real threat, the BitTorrent application would need to have a security flaw, that could allow an attacker to gain control of other functions on your machine, not specified by the BitTorrent protocol.

In the case of XAMPP, which is not recommended for live web sites (opened to the outside world), the risks would depend on the security of the server application and also the applications running over it. If you design a poor web site with php and MySQL for example, there are several things an attacker could do to gain unauthorized access to your machine, through the code on your pages.

---

### Post by bob12564 on 2009-12-12
I just installed XAMPP using a You-Tube tutorial to walk me through it. Everything is password protected.  However, when I go to canyouseeme.org it now reports that port 80 is open and accessible.  You said:

"As long as you don't forward port 80 from the router to your machine, all connection attempts will be refused. "

I don't know what that means and I don't know what to do with the DSL gateway/router.  I presume that Firefox needs port 80 and I also have Skype installed which I understand also needs port 80 so the router must allow some sort of access.  I also have a wireless internet radio which needs some access that I still have to research.

I shut down XAMPP and it'll stay down until I can make it invisible.  I still need some help and I appreciate the help in getting this far.

---

### Post by lovinglinux on 2009-12-12
> **bob12564 said:**
> I just installed XAMPP using a You-Tube tutorial to walk me through it. Everything is password protected.  However, when I go to canyouseeme.org it now reports that port 80 is open and accessible.  You said:

"As long as you don't forward port 80 from the router to your machine, all connection attempts will be refused. "

I don't know what that means and I don't know what to do with the DSL gateway/router.

If you don't manually forward the port, then there is nothing to do, unless other application is using port 80 and UPnP at the same time, which would open the port automatically.

> **bob12564 said:**
> I presume that Firefox needs port 80 and I also have Skype installed which I understand also needs port 80 so the router must allow some sort of access.

You are confusing outgoing connections with incoming. Firefox is not a server, so it doesn't listen to any ports, so it doesn't open any port. It connects to external web sites on port 80, but that is their port, not yours.

Skype could be using port 80 indeed. I've got the image below from [portforward.com](http://portforward.com/english/routers/port_forwarding/Westell/Versalink327W/Skype.htm). It's a Windows version, but I guess the Linux  version should be the same (I don't use it):

[IMG]http://portforward.com/english/applications/port_forwarding/Skype/Skype-Connection.jpg[/IMG]

Uncheck the option "Use port 80 and 443 as alternatives for incoming connections".  Then setup the incoming port (use a number different than 80) in the "Use port XXXXX for incoming connections" and forward that port on the router. Then check if you don't have port 80 forwarded in the router and test with canyouseeme again. 

You can get instructions on port-forwarding for your router at [http://portforward.com](http://portforward.com)

If that doesn't help, you could configure XAMMP to use a different port.

---

### Post by bob12564 on 2009-12-13
I checked the Skype settings and it appears that it's not using port 80 after all.  I saw a lot of complaints about Skype conflicting with Apache and maybe the Skype folks changed the defaults.  It seems to work.

Playing with the router firewall knocked out my internet radio.  I got some help from someone at a forum for internet radios and there seems to be an issue with the Verizon DSL gateway/modem. It's a customized version for Verizon and a lot of configuration settings are missing.  I finally solved the issue by enabling the ufw firewall and leaving the default setting of blocking all incoming ports. That seems to have stealthed my computer altogether and XAMPP still seems to work except...

Do you have any idea why I can't get the XAMPP welcome page that's supposed to come up at localhost?  It was there when I installed XAMPP but a day later I just get a white screen with an XAMPP logo and asking me for a language.  I click 'English" but nothing else happens.  The welcome page has the links to phpmyadmin and the other tools.

Thanks again for the help.

---

### Post by lovinglinux on 2009-12-13
> **bob12564 said:**
> Do you have any idea why I can't get the XAMPP welcome page that's supposed to come up at localhost?  It was there when I installed XAMPP but a day later I just get a white screen with an XAMPP logo and asking me for a language.  I click 'English" but nothing else happens.  The welcome page has the links to phpmyadmin and the other tools.

Nope. I would install it again.

---


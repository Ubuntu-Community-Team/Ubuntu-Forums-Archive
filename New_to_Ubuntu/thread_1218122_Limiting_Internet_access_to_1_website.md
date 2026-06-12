---
title: "Limiting Internet access to 1 website"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by ltgrunt on 2009-07-20
I work in the IT department for a nonprofit that runs ~20 retail stores.  One of the key parts of our mission is helping people find employment, and to do this we have computer stations at each store where applicants are supposed to be able to browse our website and apply for jobs or job training with our company.  We've been using Windows XP systems for this, but several people misused the computer stations for personal use, including browsing to adult content.  To counter this, we used various Windows XP tricks to lock down permissions in WinXP and Internet Explorer, but this ended up locking us out of even our own website half the time, and prevents our customers from being able to open and use the application forms.

Since Windows XP wasn't cutting it, we decided to look into Linux.  Getting Ubuntu installed and operational isn't a problem, and we've gotten it to run Firefox on startup, but what we want to do is lock web browsing down to the point that users will only be able to go to the one website we specify - our website - and nothing else.  No Google, Hotmail, eBay, etc.

At this point, though, we're at the limits of our IT department's Linux knowledge, which basically consists of installing it, goofing around with it, trying to get Wine to work, and goofing around some more.

If anyone knows of any ways to restrict web access to one site and can explain to a complete beginner it would be much appreciated.

---

### Post by wizard10000 on 2009-07-20
> **ltgrunt said:**
> I work in the IT department for a nonprofit that runs ~20 retail stores.  One of the key parts of our mission is helping people find employment, and to do this we have computer stations at each store where applicants are supposed to be able to browse our website and apply for jobs or job training with our company.  We've been using Windows XP systems for this, but several people misused the computer stations for personal use, including browsing to adult content.  To counter this, we used various Windows XP tricks to lock down permissions in WinXP and Internet Explorer, but this ended up locking us out of even our own website half the time, and prevents our customers from being able to open and use the application forms.

Since Windows XP wasn't cutting it, we decided to look into Linux.  Getting Ubuntu installed and operational isn't a problem, and we've gotten it to run Firefox on startup, but what we want to do is lock web browsing down to the point that users will only be able to go to the one website we specify - our website - and nothing else.  No Google, Hotmail, eBay, etc.

At this point, though, we're at the limits of our IT department's Linux knowledge, which basically consists of installing it, goofing around with it, trying to get Wine to work, and goofing around some more.

If anyone knows of any ways to restrict web access to one site and can explain to a complete beginner it would be much appreciated.

I'm gonna answer a question with a question  :)

Do your IT guys know enough to set up a firewall correctly?  They could just block all http traffic to that machine's IP address except for that one site.

---

### Post by perito on 2009-07-20
u can configure your modem's firewall (for example) to block access to all sites except 1 site. afaik, no need to touch the OS.

---

### Post by ltgrunt on 2009-07-20
Software firewalls that we've tried on XP have been less than effective at the intended task.  Hardware firewalls would work, but have tended to goof up the Internet connection on the registers and the manager's workstation PC, all of which we need to keep online for communicating with the stores and for things like credit card and check transactions.

---

### Post by wizard10000 on 2009-07-20
> **ltgrunt said:**
> Software firewalls that we've tried on XP have been less than effective at the intended task.  Hardware firewalls would work, but have tended to goof up the Internet connection on the registers and the manager's workstation PC, all of which we need to keep online for communicating with the stores and for things like credit card and check transactions.

Forgive me, but if your IT department can't configure a hardware firewall then you're trying to use technology to solve a training issue  :)

I know that doesn't help you much - and I don't run a software firewall on my own Ubuntu machines.  Perhaps someone a little smarter on software firewalls can assist?

thanks - and good luck.

---

### Post by moody_mark on 2009-07-20
The firewalls are the best way. "ufw" Ubuntu firewall comes installed as standard and as with any command in Linux typing "man <command" will give you a help text file of the command, so for example

```
man ufw
```

If you dont want to use a firewall then you could try firefox plugins such as one I use at home called "procon" . It works great for keeping my kids from accidentally cross linking to those dodgy sites, it is a bit restrictive and you can restrict access to all sites apart from whats in a "whitelist".

[https://addons.mozilla.org/en-US/firefox/addon/1803]("https://addons.mozilla.org/en-US/firefox/addon/1803")

As for wine, not sure why your using that but if you dont need any windows apps, then id uninstall wine if I were you. Nothing wrong with it, but your just bloating your machine out if you dont need it.

Sounds like you might need some more help getting ubuntu up and running across your stores. You'll find lots of help on here, also take a look at the IRC channels if you get yourself setup with IRC and join the one of the ubuntu help channels, you can get real time help there.

[URL="https://help.ubuntu.com/community/InternetRelayChat"]
https://help.ubuntu.com/community/InternetRelayChat[/URL]

Scroll down to the bottom for details on registering for IRC

---

### Post by ltgrunt on 2009-07-20
> **wizard10000 said:**
> Forgive me, but if your IT department can't configure a hardware firewall then you're trying to use technology to solve a training issue  :)

I know that doesn't help you much - and I don't run a software firewall on my own Ubuntu machines.  Perhaps someone a little smarter on software firewalls can assist?

thanks - and good luck.


It's not that we can't configure a hardware firewall, it's that we don't want to configure the hardware firewall to restrict access on all of the machines in the building and in doing so break our retail register systems.  The hardware firewalls on-site are of the all-or-nothing, ham-fisted type that come built into basic routers, while the firewall or ISP provides is of the type that we aren't granted access to to play around with access restrictions per IP address at each location.

We also want to keep the possibility of being able to quickly move these machines from one location to another in the event of job fairs, etc., and relying on the restrictions to be built into the machines rather than the Internet access at each site would be more helpful in this regard as well.  Sorry for not providing more specific information before.

We're aware that there would be other ways to achieve the same result, but what we're specifically looking for is the ability to put the access restrictions on the computer itself.

---

### Post by wizard10000 on 2009-07-20
> **ltgrunt said:**
> ...The hardware firewalls on-site are of the all-or-nothing, ham-fisted type that come built into basic routers, while the firewall or ISP provides is of the type that we aren't granted access to to play around with access restrictions per IP address at each location.

Ah.  I get it now.

My apologies for smacking around your IT department  ;)

---

### Post by wojox on 2009-07-20
Here is good documentation for ufw:

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by hetx on 2009-07-20
sudo apt-get install firestarter

Nice graphical interface to set up the "firewall" so you only have access to one IP out. Then you run it with a non-sudo user and no one can touch it. Should do it for you, no?

---

### Post by ltgrunt on 2009-07-20
Thanks, Mark, I'll look into Procon.

Also, we haven't been using Wine on these jobsearch workstations.  We just put Wine on one of the test machines we've been playing around with because, well, we just wanted to play around with it.  We never really got it to do what we wanted - run Office 2007 - and that doesn't really bother me all that much since I'm a big fan of OpenOffice anyway.  Basically, we were just goofing around with Wine.

No problem, Wizard.  I could have gone into more detail ruling out the routes we didn't want to or couldn't address.

Thanks Wojox and Hetx, too.  I'll check those out as well.

---

### Post by Cheesemill on 2009-07-20
[http://www.lmgtfy.com/?q=firefox+whitelist+add-on](http://www.lmgtfy.com/?q=firefox+whitelist+add-on)

---

### Post by desperado665 on 2009-07-20
You might try running Opera in kiosk mode. 

See here: [http://www.opera.com/support/mastering/kiosk/](http://www.opera.com/support/mastering/kiosk/)

---


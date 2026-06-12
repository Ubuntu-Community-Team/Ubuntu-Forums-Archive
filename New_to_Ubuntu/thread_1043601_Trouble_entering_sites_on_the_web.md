---
title: "Trouble entering sites on the web"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by anigodin on 2009-01-18
Hello all,

I have a strange problem: I'm using Linux 8.10 with firefox 3. I have an Edimax router connected to the ADSL modem and for some reason I'm unable to enter certain websites.. 
I can go into my homepage and few other sites but other then that, nothing. I got an error message.

I thought maybe something is wrong with firefox (it's giving me some hard time lately, I don't know what's wrong with it), so I installed Opera (which I was able to connect to its website and download. Opera also cant enter most websites. 

The pidgin and other web services work, by the way.

I tried to unplug the router and the modem but nothing. I also tried to enter the configuration of the router but firefox and also opera just unable to do so..

On windows XP (which I have installed in dual boot on this machine), everything works fine.

What is the problem? does anybody know or had this kind of problem?

---

### Post by Zill on 2009-01-18
anigodin:  It might be worth reducing the MTU from the default 1500...

[http://ubuntuforums.org/showthread.php?t=718709&page=2]("http://ubuntuforums.org/showthread.php?t=718709&page=2")

[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/14122]("https://answers.launchpad.net/ubuntu/+source/network-manager/+question/14122")

---

### Post by anigodin on 2009-01-19
I'll try it assuming I'll be able to enter the router's config..

I typed it's address (192.168...) and nothing happened.

Thanks for the advice.

---

### Post by Zill on 2009-01-19
> **anigodin said:**
> I'll try it assuming I'll be able to enter the router's config..

If your Ubuntu installation is corrupted in some way so that you can't get to the router's config then I suggest you reboot with the Live CD.  This should then allow you to config the router if necessary.

However, I doubt if the MTU setting will prevent access to the router - maybe something else is corrupted. :-(

---

### Post by anigodin on 2009-01-19
Well, I finally menaged to log into the router and I found out the mtu was fine. the value was 1392. I changed it to 1492, to be on the safe side, but nothing happened.

I checked the network in ubuntu and on the wired connection (the one I use) I changed the configuration from static ip to dhcp and suddenly everything works..

I hope this solves the problem, though I dont unerstand why it worked fine so far and suddenly stopped working. anyway, it works and I hope it'll keep working.

Many thanks for the help.

---


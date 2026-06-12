---
title: "ssh stopped working all of a sudden"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by treymul on 2008-08-05
I installed ssh server on my desktop and have been able to ssh into it from my laptop for the past 2 months.  

Yesterday I had to reboot my desktop, and now I cannot ssh into it.  My laptop just gives me "ssh: connect to host xx.xx.xx.xx port xx: connection timed out". On my desktop, in the auth.log, I recieved some errors, "server listening on :: port xx.  error: bind to port xx on 0.0.0.0 failed.  Address already in use."  Can anyone help figure out what is going on?  

I have tried uncommenting the listenaddress :: and listenadress 0.0.0.0 lines in the sshd_config file per some other forums, this cleans up the errors in the auth.log of the desktop, but it does not fix the fact that I can't ssh into from my laptop.

---

### Post by spin2cool on 2008-08-05
Are you sure that the IP address is the same?  Often routers will assign a new/different IP address to your desktop after a reboot.  Check the router status page to see if it's the same.

---

### Post by ajopaul on 2008-08-05
from your desktop can you try ssh localhost ?

---

### Post by treymul on 2008-08-05
Yes to both, I have checked the router status page and the desktop ip is the same as before.  I can also run ssh localhost without any problems.

---

### Post by treymul on 2008-08-06
I figured it out.  I have a script that emails me my desktops ip everyday.  My comp was rebooted after the email was sent.  I updated my script to check the ip every hour and email me the new one if it changes.  Thanks for the help anyways.

---

### Post by ajopaul on 2008-08-07
you can use a domain name to solve this, checkout [www.dyndns.com](www.dyndns.com), there's also a program tat updates the domain name you selected to your current wan ip.

---

### Post by treymul on 2008-08-07
Thanks, I have seen that but don't want to go through the hassle or spend the money.

---

### Post by silverglade00 on 2008-08-07
It's a free service to just keep a domain name through here. There are other paid services that they provide, but for this purpose it's free. That's what I use to ssh in to my own machine. My cheapie Linsys router has support for it built in as well, so I just had to put in my dyndns username and password and it is all automatic from there. The only hassle involved is to click a link in a once-a-month email to keep my account active. Oh, and it took me a while to come up with a name I would remember.

---

### Post by y@w on 2008-08-07
Yeah.. I've used dynamic dns services for years and once they're up you don't have to worry about them. That's a lot simpler and less hassle than getting an email every day with your IP address. You've had to click an email once a month? I've been using both no-ip and dyndns and haven't had to do that, but my IP addresses change quite often so that's probably why.

---

### Post by treymul on 2008-08-11
You guys were right, set up a dyndns account, much easier than screwing with emails and crap, thanks.

---

### Post by silverglade00 on 2008-08-12
I have to click on the email each month. I think that's because my IP address has only changed twice in the last 5 years. Once because I moved.

---


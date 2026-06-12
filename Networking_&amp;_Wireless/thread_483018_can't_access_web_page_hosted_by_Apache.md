---
title: "can't access web page hosted by Apache"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by bbyte on 2007-06-24
I can get the site up on my laptop using Ubuntu 7.04 and Apache through a phone card using dynamic dns.  However on my satellite, Hughesnet, system at home using a static IP and port forwarding and DMZ on a Linksys WRVS4400N router I get the modem HN7000S config page when I request the site locally either with the name or the IP and externally just get page load error.  I have googled, searched the Ubuntu forums, called both router and ISP vendors but I am just not able to ask the right questions on the forums and the problem  might not be in the scope of the vendors.  I have tried isolating the problem but I am more confused now than ever.  I would really appreciate if there is someone here who could point me in the right direction.

---

### Post by p_quarles on 2007-06-24
If I understand you correctly, you're saying that you can access the site from within the local network, using the LAN IP, but cannot access it using the public IP? 

One thing you will need to do, if you haven't already, is make sure that your modem is configured to allow http traffic (port 80) through to the router. The router can then be set up to forward port 80 traffic to the appropriate machine. 

Using a separate gateway and router can be a pain -- chances are they both have their own firewalls built in, and they need to be synchronized before you can get any traffic through.

---

### Post by bbyte on 2007-06-24
I can't access the site either locally or remotely.  If I use localhost then I am able to get there of course.  The port.conf (Apache) is setup to listen on port 80.  The router is set to  port forwarding range and port 80 is set to be forwarded.  When I try to go on the site externally, I get a connection to the server was reset while trying to load the page error.

---

### Post by p_quarles on 2007-06-24
And what about the gateway? Is that built in to the router, or is it a separate one? Like I said, I had to tell my DSL modem to treat my router as a webserver before I could get this setup working.

The other thing could be IPtables. I know that if you install Ubuntu server edition using the LAMP option, it won't block port 80 by default. If you set up Apache on a desktop edition, though, that could be the problem.

EDIT: I should add, too, that I think IPtables might be the issue here, just because it's odd that you can't see the web site using the LAN IP address. That suggests to me that the firewall is stopping it.

---

### Post by bbyte on 2007-06-24
The IPtables suggestion sure is interesting as it is something that I haven't paid any attention to.  Heck, I had to do a quick google to see what you were talking about and it sure is something that I need to do.  I am at work right now and will be tied up for a few hours and probably won't get to this until the evening but I will post back after setting a rule in IPtable.  By the way, the router is setup as the gateway.  Thanks for the pointer!

---

### Post by bbyte on 2007-06-25
After a lot of searching and reasearch, I used a utility that wrote a IPTable text file that added rules for the web server and tried again with no success.  After sleeping on it I realized that I was working on an area that would also affect my laptop yet the laptop works.  I have Ubuntu desktop and Apache2 installed on both the desktop and the laptop.  The onle difference is how I get to the internet.  With the laptop I have to use the dynamic DNS approach with DDNS client running on the laptop through the Verizon PC phone card.  However, on the desktop I am able to use a static IP but I go through a Linksys WRVS4400N router and a HughesNet HN7000S modem.  

Once I setup the domain to be dynamic, I can access the site hosted by the laptop from any computer whether it is a system at work or at home.  But as soon as I set the domain for static and  use the home system to host the site I get the Hughes modem's config page instead of the host site.

I am now having a hard time thinking that it is something in the IPTable rules as both systems are running the same versions with the same configs.  Is there anything else that someone can point me to?

---

### Post by p_quarles on 2007-06-25
This is getting beyond my knowledge-level. One thing you could try, though, is making sure /etc/mysql/my.cnf (or the equivalent) is set correctly. The default line:

bind-address = localhost

should be changed to 

bind-address = [internal IP address]

---

### Post by bbyte on 2007-06-25
That didn't help either.  I will keep working on this and when I get a solution I will share it on this posting.

---

### Post by p_quarles on 2007-06-25
I just reread the entire thread, and noticed something that doesn't quite make sense to me. You said the router was the gateway, but then you said you're using both a Linksys router and a satellite modem. 

If the modem (that's what I meant by gateway) doesn't let traffic through, then the result you're getting makes sense. The laptop is connecting through Verizon's WiFi network, and therefore not going through the router or the gateway. Your desktop is going through both. This, in turn, would mean that outside systems would have direct access to your laptop through Verizon's network, but they would have to go through two firewalls to get to your desktop.

I could be barking up the wrong tree, but I thought I'd bring this up in case it helps.

---

### Post by bbyte on 2007-06-26
I am making progress but more of a one step ahead two step backwards kind of way.  Come to find out that Apache wasn't configured correctly to host an external site.  Although, and I don't know enough to explain this, the laptop will work with the same setup but I have them both configured so that when I give the stop or start commands I don't generate any errors or warnings but still no cigar.

Tonight I am going to connect directly to the modem so that I can better isolate the problem.

I sure do appreciate all your help.

---

### Post by bbyte on 2007-06-26
Ugh!! Not what I was hoping for.  Connecting straight to the modem I am still getting hung up. I setup a static IP (same as domain)  xx.xx.xx.xb is ip and xx.xx.xx.xa is gateway and also domain ip.

When I put in [www.mysite.com](www.mysite.com) or xx.xx.xx.xa I get modem conf page.  Localhost or xx.xx.xx.xb takes me to the site.

That leaves me with 2 targets..modem or web server.  I am leaning more to the server so I will keep looking at the apache configs.

---

### Post by p_quarles on 2007-06-26
I just looked at my Apache config files, to see if I could identify anything there. I didn't see anything relevant in apache2.conf, and httpd.conf is blank. The only thing I could find that might affect retrieval is ports.conf. Mine has a single line:```
Listen 80
```

I could post my apache2.conf contents, too, if you'd like to compare. It's mostly default, though, and it has a lot of comments. But, it might help you at least eliminate the config file as the problem.

One other thought: you might try installing Webmin on the box that's running Apache. If you're not an expert, it's a helpful interface that gives you a lot of clues as to options that you might not have known were there.

---

### Post by bbyte on 2007-06-27
You are right about Webmin and it does give lots of areas to look at.  I now can put in the site as mysite.com and go to the default page.  However, if I put in [www.mysite.com](www.mysite.com), no joy.  Still not able to do anything external.  

Checked the laptop this morning and it is still able to host dynamically.  There was a slight difference in the hosts conf but I changed that and still no fix for the home system.  

If I get a chance, I will post my default page tonight and maybe something will pop out.

---

### Post by bbyte on 2007-07-08
I am passing on this problem for several reasons.  One, there are just too many moving targets and I can't get a handle on what the problem is.  Two, my ISP will cause me problems if i do get it going. And three, I do have it running on my laptop so that will have to do until I have more ISP options.

---


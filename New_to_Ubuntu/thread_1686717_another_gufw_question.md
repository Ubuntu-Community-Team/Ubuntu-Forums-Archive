---
title: "another gufw question"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by werty2010 on 2011-02-12
i set gufw like this:  -all incoming to deny
                               -all outgoing to allow

before this i did some tests,setting incoming/outgoing to deny and thed adding a few exception(like http) but i couldn't connect anywhere
am i doing something wrong?
could some explain me in simple words how does it work?

---

### Post by Frogs Hair on 2011-02-12
This may help.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)  

[http://www.cs.wcupa.edu/~rkline/Ubuntu/firewall.html](http://www.cs.wcupa.edu/~rkline/Ubuntu/firewall.html)

---

### Post by werty2010 on 2011-02-12
thanks but isnt gufw a frontend for ufw?
do i still need to modify ufw "manually" ?

---

### Post by sffvba[e0rt on 2011-02-12
> **werty2010 said:**
> thanks but isnt gufw a frontend for ufw?
do i still need to modify ufw "manually" ?

Yes, GUFW is a GUI for UFW so any changes made in GUFW is actually made in UFW... so no need to do everything twice... choose what works best for you GUI or CLI and your good to go...


404

---

### Post by werty2010 on 2011-02-12
ok 
are these settings good enough ?-->  -all incoming to deny/all outgoing to allow
could you recommend me some modifications like adding some rules..?
I'm a casual user surfing,downloading,emailing,studing.

---

### Post by sffvba[e0rt on 2011-02-12
> **werty2010 said:**
> ok 
are these settings good enough ?-->  -all incoming to deny/all outgoing to allow
could you recommend me some modifications like adding some rules..?
I'm a casual user surfing,downloading,emailing,studing.

To be completely honest I normally enable the UFW and leave it as is... the last time I changed anything from the default was when I was playing around with SSH and remote desktop between two of my systems...

Test all of your applications you normally use... IM, torrents etc. and if they all work I guess your good to go...



404

(Enabling all for outgoing does seem a tad less than ideal though... but I am not an expert so cannot say it is or isn't :))

---

### Post by jjackson1984 on 2011-02-12
Ok my firewall configuration using GUFW is:

     - Deny all incoming
     - Deny all outgoing
     - Deny ssh      #the default configuration allows this as incoming so disable it
     - Deny www    #the default configuration allows this as incoming so disable it
     - Allow out http
     - Allow out https
     - Allow out pop3
     - Allow out pop3s
- Allow out smtp

Then edit, as root, "/etc/ufw/before.rules" and change :

# ok icmp codes
-A ufw6-before-input -p icmpv6 --icmpv6-type destination-unreachable -j ACCEPT
-A ufw6-before-input -p icmpv6 --icmpv6-type packet-too-big -j ACCEPT
-A ufw6-before-input -p icmpv6 --icmpv6-type time-exceeded -j ACCEPT
-A ufw6-before-input -p icmpv6 --icmpv6-type parameter-problem -j ACCEPT
-A ufw6-before-input -p icmpv6 --icmpv6-type echo-request -j ACCEPT

to:

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

This will give you stealth on the internet.  In-so-far as your computer appears to not be present.

If you need "GUFW" the type "sudo apt-get install gufw" , without the quotes, in a terminal.  Then yahoo "GRC Security" url:"https://www.grc.com/securitynow.htm" to test your firewall configuration.

Disclaimer: This is the configuration I use.  I neither imply nor express that this will work, or is the best, for anyone else.

---

### Post by werty2010 on 2011-02-12
> **jjackson1984 said:**
> Ok my firewall configuration using GUFW is:

     - Deny all incoming
     - Deny all outgoing
     - Deny ssh      #the default configuration allows this as incoming so disable it
     - Deny www    #the default configuration allows this as incoming so disable it
     - Allow out http
     - Allow out https
     - Allow out pop3
     - Allow out pop3s
- Allow out smtp

Then edit, as root, "/etc/ufw/before.rules" and change :

# ok icmp codes
-A ufw6-before-input -p icmpv6 --icmpv6-type destination-unreachable -j ACCEPT
-A ufw6-before-input -p icmpv6 --icmpv6-type packet-too-big -j ACCEPT
-A ufw6-before-input -p icmpv6 --icmpv6-type time-exceeded -j ACCEPT
-A ufw6-before-input -p icmpv6 --icmpv6-type parameter-problem -j ACCEPT
-A ufw6-before-input -p icmpv6 --icmpv6-type echo-request -j ACCEPT

to:

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

This will give you stealth on the internet.  In-so-far as your computer appears to not be present.

If you need "GUFW" the type "sudo apt-get install gufw" , without the quotes, in a terminal.  Then yahoo "GRC Security" url:"https://www.grc.com/securitynow.htm" to test your firewall configuration.

Disclaimer: This is the configuration I use.  I neither imply nor express that this will work, or is the best, for anyone else.

thank you

i tried to configure gufw by dening all incomiing/outgoing and setting the exceptions listed above(i couldnt find the https/pop3s/www/ssh on the gufw rules-newbe) but the moment i set deny all outgoing, no matter the later rules, internet traffic seems to be instantly locked and nothing 'moves'
any ideas?

as for the 2nd part ill try it a bit later because i have to get some sleep..

---

### Post by sffvba[e0rt on 2011-02-12
> **jjackson1984 said:**
> If you need "GUFW" the type "sudo apt-get install gufw" , without the quotes, in a terminal.  Then yahoo "GRC Security" url:"https://www.grc.com/securitynow.htm" to test your firewall configuration.

@ [www.grc.com](www.grc.com) follow the Shields UP links to test your system... my system passed all of the tests with flying colours on the default UFW settings :p


404

---

### Post by jjackson1984 on 2011-02-12
> **werty2010 said:**
> thank you

i tried to configure gufw by dening all incomiing/outgoing and setting the exceptions listed above(i couldnt find the https/pop3s/www/ssh on the gufw rules-newbe) but the moment i set deny all outgoing, no matter the later rules, internet traffic seems to be instantly locked and nothing 'moves'
any ideas?

as for the 2nd part ill try it a bit later because i have to get some sleep..

***********************

Ok, My mistake.... I believe these are: allow out anywhere, 80, 443, 110, 995, 25
deny in 80, 22 anywhere.  

Yes if you deny outgoing and incoming, then you have locked your door.  Then allow out the above ports.  Now this will allow your web browser and email to access the outside world.  Nothing else until you allow it by adding permissions.

---

### Post by jjackson1984 on 2011-02-12
> **not found said:**
> @ [www.grc.com]("http://www.grc.com") follow the Shields UP links to test your system... my system passed all of the tests with flying colours on the default UFW settings :p


404


Congradulations, mine didn't until I made these changes.

---

### Post by werty2010 on 2011-02-13
> **jjackson1984 said:**
> ***********************

Ok, My mistake.... I believe these are: allow out anywhere, 80, 443, 110, 995, 25
deny in 80, 22 anywhere.  

Yes if you deny outgoing and incoming, then you have locked your door.  Then allow out the above ports.  Now this will allow your web browser and email to access the outside world.  Nothing else until you allow it by adding permissions.

tried it, still the same situation:nothing moves.... 
although i tried the 'shields up' site and i also passed..

---

### Post by sffvba[e0rt on 2011-02-13
> **werty2010 said:**
> tried it, still the same situation:nothing moves.... 
although i tried the 'shields up' site and i also passed..

I cannot see the reason for all this extra settings... the default seems as much as any reasonable person needs...

Good luck getting it sorted out...



404

---

### Post by werty2010 on 2011-02-19
some help anyone
no matter what changes/exception i've made when i set outgoing to deny everything stops moving

---

### Post by werty2010 on 2011-02-19
another weird thing on a test:
i set the gufw to allow all incoming/outgoing and then ran grc-shields up to see the results: whatever the settings the results saying that im stealth.
why? ok maybe because of the router but im not sure...

---

### Post by JKyleOKC on 2011-02-19
Yes, the GRC site tests your router, not your machine. Since you're using the router and it tests okay, you don't really need to enable ufw at all!

---

### Post by werty2010 on 2011-02-19
could someone please help set up gufw or realize if its not working properly,step by step?

---

### Post by sffvba[e0rt on 2011-02-20
> **werty2010 said:**
> could someone please help set up gufw or realize if its not working properly,step by step?

It seems clear that non of the answers here seem to be satisfactory to you so I would suggest starting a new thread here [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338) and maybe a security expert can give you a more satisfactory answer...



404

---

### Post by 3rdalbum on 2011-02-20
I'm wondering why you're bothering to configure your firewall at all.

From the information posted here, your router is already acting as a firewall. Setting up a personal firewall is just: a) Double the work to add exceptions and b) going to stop traffic within your own network.

Just set it to "accept" everything. A default Ubuntu system does not listen to any incoming ports anyway (no programs listen) so there's no threat from not running a firewall. But, of course, your router is already acting as a firewall anyway.

---

### Post by werty2010 on 2011-02-20
> **3rdalbum said:**
> I'm wondering why you're bothering to configure your firewall at all.

From the information posted here, your router is already acting as a firewall. Setting up a personal firewall is just: a) Double the work to add exceptions and b) going to stop traffic within your own network.

Just set it to "accept" everything. A default Ubuntu system does not listen to any incoming ports anyway (no programs listen) so there's no threat from not running a firewall. But, of course, your router is already acting as a firewall anyway.


im kind of concerned because i use very often public hotspots with my laptop

---


---
title: "DNS Servers"
date: 2005-09-09
forum: Networking &amp; Wireless
---

### Post by orev on 2005-09-09
ubuntu networking (or modem/router) keeps adding the modems ip address into my DNS settings, which seems to prevent my access of the internet.  It also keeps removing one of my DNS server ip addresses.  everytime I boot I must go into the network setting, and change the DNS server settings (remove modem ip and add DNS ip)

Any suggestions?

Modem/router is an ActionTec GT701-WG (Qwest DSL modem/wireless router)

I've been looking into the modem setup, but haven't figured it out yet...


UPDATE:  After reading all of the other posts on this issue, I am taking my issue to ActionTec.

Thanks forum.

---

### Post by sgenchev on 2005-09-09
One way to do it without reconfiguring DHCP server is to disable resolv.conf rewrite. dhclient3 runs script /etc/dhcp3/dhclient-script after obtaining a lease. One of the things script does is modification to resolv.conf. You could simply comment out this part of code:
 - open /etc/dhcp3/dhclient-script in your favorite editor (as root)
 
 - find 2 occurences of "make_resolv_conf" and comment them out. WARNING!!! the first "make_resolv_conf() {" in the beginning of the file is the actual procedure definition. Leave it alone. There are 2 calls to this procedure on lines 194 and  243. 
 Add # in front of them so they read  "# make_resolv_conf"
 - save the file

 That should do what you want...

---

### Post by mlomker on 2005-09-09
Thanks to sgenchev for that information...I was looking for that to solve the same problem about a week ago but didn't figure it out.  I discovered that rebooting my router and changing the DHCP lease period to the maximum setting help sort my issue out.  If the ISP is sending out bogus DNS entries then calling them is the best bet.

If you comment out the code, like sgenchev suggested, it'll stop DHCP updates of resolv.conf altogether---might not be cool if you have a laptop and need to plug into a corporate network with internal DNS servers as well (like me).  It wouldn't matter if you just use the box at home--for that matter you might as well do a static entry in /etc/network/interfaces in that case.

---

### Post by orev on 2005-09-14
[QUOTE=sgenchev]One way to do it without reconfiguring DHCP server is to disable resolv.conf rewrite. dhclient3 runs script /etc/dhcp3/dhclient-script after obtaining a lease. One of the things script does is modification to resolv.conf. You could simply comment out this part of code:
 - open /etc/dhcp3/dhclient-script in your favorite editor (as root)
 
 - find 2 occurences of "make_resolv_conf" and comment them out. WARNING!!! the first "make_resolv_conf() {" in the beginning of the file is the actual procedure definition. Leave it alone. There are 2 calls to this procedure on lines 194 and  243. 
 Add # in front of them so they read  "# make_resolv_conf"
 - save the file

 That should do what you want...[/QUOTE]


Worked flawlessly.  Thank you.

I tried calling the ISP first, but they said it was a modem problem, ActionTec said it was an ISP problem.....and here I am.

There is alot of posts on the ActionTec modem/router - maybe this should be somewhere easy to find?

---

### Post by lovestopsfear on 2005-11-02
[QUOTE=sgenchev]One way to do it without reconfiguring DHCP server is to disable resolv.conf rewrite. dhclient3 runs script /etc/dhcp3/dhclient-script after obtaining a lease. One of the things script does is modification to resolv.conf. You could simply comment out this part of code:
 - open /etc/dhcp3/dhclient-script in your favorite editor (as root)
 
 - find 2 occurences of "make_resolv_conf" and comment them out. WARNING!!! the first "make_resolv_conf() {" in the beginning of the file is the actual procedure definition. Leave it alone. There are 2 calls to this procedure on lines 194 and  243. 
 Add # in front of them so they read  "# make_resolv_conf"
 - save the file

 That should do what you want...[/QUOTE]

this worked with Hoary for me, but not with Breezy Badger. if i change the script you wrote about, the interface won't activate (it activate okay in Hoary). my internet only works for about 10 minutes before the script overwrites the DNS i enter. is there a way to get the interface to activate or set the script up to rewrite the DNS after a very long period?

i have a Qwest DSL Actiontec. 

thanks!

---

### Post by lovestopsfear on 2005-11-04
Ok, I've figured it out.  I just commented out the single line that overwrites resolv.conf in /etc/dhcp3/dhclient-script:
#        mv $new_resolv_conf /etc/resolv.conf

---

### Post by mlomker on 2005-11-04
[QUOTE=lovestopsfear]Ok, I've figured it out.  I just commented out the single line that overwrites resolv.conf in /etc/dhcp3/dhclient-script:
#        mv $new_resolv_conf /etc/resolv.conf[/QUOTE]

That'll work but it isn't so great if you move between networks (work to home with a laptop, for example).  It's a lot easier to just install the **resolvconf** package and use that to over-ride the DNS server entries provided by DHCP.

---

### Post by roland_mai on 2005-11-20
Guys, thanks so much...

I have a Blitzz Router that sucks with the dns handling in linux, but works fine in windows.
I set the dns locally from the dns provided by the ISP and all the hard times that I have had so far have ended.... :D 

Thanks again,

Roland

---


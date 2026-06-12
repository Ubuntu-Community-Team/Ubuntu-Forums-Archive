---
title: "Login/Password for highspeed internet?"
date: 2004-12-22
forum: Networking &amp; Wireless
---

### Post by saad on 2004-12-22
Hi there,

I just installed Ubuntu and its one of the best distros I've tried so far!  I'm having a network problem, which I've broken down in two parts below:

1) My network card - eth0 - is set as detecting IP, etc, via DHCP.  When I click to activate it, the system hangs for about one or two minutes and then doesn't do anything.  I can't get it to activate. Read more here:

[http://ubuntuforums.org/showthread.php?t=2226](http://ubuntuforums.org/showthread.php?t=2226)

I think this issue is directly related to the problem below.

2) I'm using Bell Canada ADSL, which requires a login and password.  I don't see any place where I can type in a login and password.  The DHCP is probably not working because there is no place I can type in my login and password, so my OS can't get the info from Bell.  

If anyone can help, I'll be greatly appreciative.

Thanks!
Saad

---

### Post by Averatec5400 on 2004-12-22
[QUOTE=saad]Hi there,

I just installed Ubuntu and its one of the best distros I've tried so far!  I'm having a network problem, which I've broken down in two parts below:

1) My network card - eth0 - is set as detecting IP, etc, via DHCP.  When I click to activate it, the system hangs for about one or two minutes and then doesn't do anything.  I can't get it to activate. Read more here:

[http://ubuntuforums.org/showthread.php?t=2226](http://ubuntuforums.org/showthread.php?t=2226)

I think this issue is directly related to the problem below.

2) I'm using Bell Canada ADSL, which requires a login and password.  I don't see any place where I can type in a login and password.  The DHCP is probably not working because there is no place I can type in my login and password, so my OS can't get the info from Bell.  

If anyone can help, I'll be greatly appreciative.

Thanks!
Saad[/QUOTE]
 sounds like you need to use synaptic and install ppoe, hopefully it is on a CD, if not you might try putting it on a USB drive and then use dpkg -i ppoe.deb and see if you can then setup pppoe and get online from ubuntu.

---

### Post by saad on 2004-12-22
Hi Averatec5400,

Thanks for your feedback.  I found ppoeconfig.deb on the CD - I presume this is the file you are talking about.  It was installed on my PC by default when I installed Ubuntu, so I reinstalled it, just in case.   What do I do now?  When I'm under network settings, there is no place for a login and password.  

If I switch it to "Manual" from "Automatic - DHCP", it asks me for an IP Address and Gateway, which I don't have since I'm not using a static IP and I don't have a router.  

I know my problem will be solved once I can get Ubuntu to resolve the DHCP using my login and password.  Any idea where to input this?

Thanks!
Saad

---

### Post by Averatec5400 on 2004-12-23
[QUOTE=saad]Hi Averatec5400,

Thanks for your feedback.  I found ppoeconfig.deb on the CD - I presume this is the file you are talking about.  It was installed on my PC by default when I installed Ubuntu, so I reinstalled it, just in case.   What do I do now?  When I'm under network settings, there is no place for a login and password.  

If I switch it to "Manual" from "Automatic - DHCP", it asks me for an IP Address and Gateway, which I don't have since I'm not using a static IP and I don't have a router.  

I know my problem will be solved once I can get Ubuntu to resolve the DHCP using my login and password.  Any idea where to input this?

Thanks!
Saad[/QUOTE]
 I am showing just a package called ppoe. I have dhcp on my DSL here, so I am not exactly sure what needs to be done, maybe try using the modem/ppp package and selecting the network card as the device?

---

### Post by Averatec5400 on 2004-12-23
[QUOTE=Averatec5400]I am showing just a package called ppoe. I have dhcp on my DSL here, so I am not exactly sure what needs to be done, maybe try using the modem/ppp package and selecting the network card as the device?[/QUOTE]
 Oh think I see what to do but cant test it, open a terminal in gnome, type sudo pppoeconf (yes THREE p's) and it will step you through the process in the shell

---


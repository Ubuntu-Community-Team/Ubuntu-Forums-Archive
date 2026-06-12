---
title: "Help need sharing a dial-up connection"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by whein on 2007-04-05
Be gentle, relative newbie...  I have two computers at home running Edgy.  One has a modem that can dial out to my ISP.  Both computers are connected to each other through a Linksys switch/hub (I honestly forget which it is).  I can ping one from the other and vice versa, so I know that my hardware is working and that the static IPs I assigned each (192.168.0.1 and 192.168.0.2) are correct.  That's the good news...

I tried to install Firestarter onto computer A (with the modem) because it said that it could act as a proxy server and allow me to share my connection, exactly what I want.  Well, I think the firewall part is working ok, but computer B cannot see the internet at all.  I've run through the part of the Firestarter manual about sharing an internet connection, but something is still missing on one or both of the computers.

Can anyone out there guide me step by step through setting up computer A to act as a proxy for computer B?  I'm still finding my way around Linux so the more detail the better!  Thanks in advance!
-Will

---

### Post by Floppyjoe on 2007-04-05
I think you need to set up a DHCP server on the computer that connects to the internet so the other computer can get an IP address from it.

---

### Post by whein on 2007-04-05
Floppyjoe, can you be a little more detailed on how to do this?  I already have the dhcp package installed, but I do not know/understand enough to set it up properly, if I need to at all.  I was under the impression that DHCP, while nice and good for scalability of networks, was not necessary.  Is this not the case?  And if not, can someone explain a little more why?  I'm still pretty wet behind the ears when it comes to Linux, but willing to learn.  I just don't always know where to _find_ TFM so I can read it...  ;)
-Will

---

### Post by Floppyjoe on 2007-04-05
To be honest I don't know much about it.
Have a look at this thread it might give you some ideas.
[http://ubuntuforums.org/showthread.php?t=325301](http://ubuntuforums.org/showthread.php?t=325301)

---

### Post by whein on 2007-04-09
/bump
:(

Still stuck.  Any ideas?

I think the specific questions I need answered are:
1) What port(s) does Firestarter use for its proxy server?
2) If I have Firestarter on a computer with a static IP address of 192.168.0.1, is it correct to set Edgy to use 192.168.0.1/?? as the proxy?
3) If I set the preferences for Edgy networking to use the proxy, do I then need to set each individual program (firefox, apt-get, etc.) to use the proxy as well?  Will these automagically get redirected because Edgy itself knows about the proxy?
-Will

---

### Post by whein on 2007-04-13
/bump again...

What I have:
Two computers running Edgy on an AMD64 architecture.
Computer A has a dial-up connection to the internet.  I use Gnome-PPP to dial out, works great.  Computer A also has an ethernet connection set up as eth0 with a static IP of 192.168.0.1.

Computer B has an ethernet connection set up as eth0 with a static IP of 192.168.0.2.

Computer B is able to browse and copy form directories shared by Computer A using a samba share.  I still have to tweak things on the permission side, but I know that there is a valid link between the two.  Both computers can ping each other.

What I need:
I'd like to have Computer B able to browse the internet using the connection Computer A establishes when it connects with the modem.

What I've tried so far:
I tried installing Firestarter, since it claimed that it could share an internet connection.  The firewall part seemed to work, but not the sharing part.  I followed the HowTo at [http://www.fs-security.com/docs/connection-sharing.php]("http://www.fs-security.com/docs/connection-sharing.php") to no avail.  In all fairness I may have misunderstood how to configure the client side of things.

I tried messing with iptables.  *NOTE*  I am way over my head here and just followed instructions blindly.  I tried the instructions at [YoLinux.com]("http://www.yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html") (the section titled Example 1: Linux connected via PPP) but that didn't seem to do anything except break my internet connection and piss off Firestarter when I started it up later.  So I rebooted and luckily my internet connection works again.  But now I cannot select PPP0 as my internet connection in Firestarter (option does not even appear on the setup screen) and if I have the firewall turned on I cannot surf the internet.  If I stop the firewall (but Firestarter window is still open) I can browse the internet no problem.

I've tried to find the answer myself through Google, etc. but it is all way over my head as a networking noob.  The advice I've gotten so far is to try Squid or setup NAT or mess with iptables or configure masquerading, etc.  Great!  HOW?????  Is there a step by step tutorial (type this, click that) or someone who has actually done this on their own setup and can guide me?  The theory makes sense to me but the devil is always in the details.
-Will :confused:

---

### Post by whein on 2007-04-19
:)
A friend pointed me to this:
[http://newbiedoc.sourceforge.net/networking/homegateway.html]("http://newbiedoc.sourceforge.net/networking/homegateway.html")
worked like a champ!  I'm currently running off a Dapper LiveCD (broke my install, story in another thread) conencted via ethernet to the other computer that has Edgy and a modem dialed in to my ISP.  Sweet!

:)
-Will

---


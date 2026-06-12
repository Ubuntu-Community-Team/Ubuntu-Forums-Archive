---
title: "Connecting 6.06 with Speedtouch 330"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by arnold senior on 2007-05-18
I am DEFEATED AFTER UMPTEEN TRIES.   I am showing my syslog for anyone to say what it means.   I think I may have succeeded in making a connexion of some sort but Firefox isn't working or my mail programme. 
  WHAT CAN I DO NEXT?????May 18 11:44:45 ubuntu pppd[4761]: pppd 2.4.4b1 started by root, uid 0
May 18 11:44:45 ubuntu pppd[4761]: Using interface ppp0
May 18 11:44:45 ubuntu pppd[4761]: Connect: ppp0 <--> 0.38
May 18 11:44:50 ubuntu gconfd (arnold-4822): starting (version 2.14.0), pid 4822 user 'arnold'
May 18 11:44:50 ubuntu gconfd (arnold-4822): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 18 11:44:50 ubuntu gconfd (arnold-4822): Resolved address "xml:readwrite:/home/arnold/.gconf" to a writable configuration source at position 1
May 18 11:44:50 ubuntu gconfd (arnold-4822): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 18 11:44:50 ubuntu gconfd (arnold-4822): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 18 11:44:50 ubuntu gconfd (arnold-4822): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 18 11:44:58 ubuntu gconfd (arnold-4822): Resolved address "xml:readwrite:/home/arnold/.gconf" to a writable configuration source at position 0
May 18 11:45:15 ubuntu pppd[4761]: LCP: timeout sending Config-Requests 
May 18 11:45:15 ubuntu pppd[4761]: Connection terminated.
May 18 11:45:15 ubuntu pppd[4761]: Modem hangup
May 18 11:45:15 ubuntu pppd[4761]: Exit.
May 18 11:46:10 ubuntu gconfd (root-5041): starting (version 2.14.0), pid 5041 user 'root'
May 18 11:46:10 ubuntu gconfd (root-5041): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 18 11:46:10 ubuntu gconfd (root-5041): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 18 11:46:10 ubuntu gconfd (root-5041): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 18 11:46:10 ubuntu gconfd (root-5041): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 18 11:46:10 ubuntu gconfd (root-5041): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 18 11:48:38 ubuntu pppd[5130]: pppd 2.4.4b1 started by root, uid 0
May 18 11:48:41 ubuntu pppd[5130]: Exit.
May 18 11:48:41 ubuntu pppd[5133]: pppd 2.4.4b1 started by root, uid 0
May 18 11:48:43 ubuntu pppd[5133]: Exit.
May 18 11:48:43 ubuntu pppd[5138]: pppd 2.4.4b1 started by root, uid 0
May 18 11:48:45 ubuntu pppd[5138]: Exit.
May 18 11:48:45 ubuntu pppd[5141]: pppd 2.4.4b1 started by root, uid 0
May 18 11:48:47 ubuntu pppd[5141]: Exit.
May 18 11:49:40 ubuntu gconfd (root-5041): GConf server is not in use, shutting down.
May 18 11:49:40 ubuntu gconfd (root-5041): Exiting

---

### Post by Kobalt on 2007-05-18
Have you checked this out : [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch) ?

---

### Post by arnold senior on 2007-05-19
Thanks for taking an interest.   I have had a look again at what you suggest but it is for 6.10 and I'm using 6.06 with the ubuntu recommended configuration blue print so I cannot see any better option.   What I really need to know is what my syslog is trying to tell me so that I know how far I have got.   I'm still waiting for an authoritive word about that and somebody out there will be able to give it; meanwhile I am having a try with Mandrake even though I much prefer Ubuntu but it is no substitute for WinME unless I can connect to the web.
anyway thanks for being the only one so far to try to help this linux learner.

arnold s.

---

### Post by StevenHarper on 2007-05-20
I have made a Debian Package to manage USB ADSL Modems and there Configuration

I Support Speedtouch USB 330 Modems

My Page it at

[https://launchpad.net/usb-adsl-modem-manager]("https://launchpad.net/usb-adsl-modem-manager")

You can download the package at [http://www.squeezedonkey.com/svn/linux/trunk/releases/]("http://www.squeezedonkey.com/svn/linux/trunk/releases/")

And read about it at 
[http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page]("http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page")

Hope it makes your life easier

Steve

---

### Post by Docter on 2007-05-21
That deb sounds like your best option but if not: You can ignore the xml warnings. I suspect that your firmware isn't loading but would need your syslog from a reboot to know for sure.  What do the lights do on your modem when rebooting?

---

### Post by arnold senior on 2007-05-22
Thanks Steve.   I'll certainly try it.


arnold senior

---

### Post by arnold senior on 2007-05-22
Thanks for being interested.   I did ask about the lights but so far no one has replied.  If you care to look at it you will see that I have done my best to describe the light sequence and compared with the lights for WinME.  It is just a few down the page Seedtouch 330 from the one you have responded to.

arnold senior

---


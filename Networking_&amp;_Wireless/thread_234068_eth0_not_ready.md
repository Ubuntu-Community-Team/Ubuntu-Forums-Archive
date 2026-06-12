---
title: "eth0 not ready?"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by jf3player on 2006-08-10
Hello, I just installed Kubuntu a few days ago and so far the forums have been very helpful for setting up Samba and a few other minor things.  Right now though, I'm stuck on trying to get Firestarter to work.

eth1 is connected to the internet via cable modem and eth0 is connected to the internal network (just a crossover cable to a Windows 95 test system for the time being).  I'll be needing it to route for several computers coming up in about a week or so.  Anyway, after installing Firestarter and going through the wizard, it keeps failing to start the firewall and telling me "The device eth0 is not ready".  Somehow I get the feeling that I'm missing something simple here, but it's starting to get a bit annoying.  Help?

*More*
Well, to build on the problem, I gave eth0 (internal network) a static IP (192.168.0.1) and the default netmask (255.255.255.0).  Now when trying to run Firestarter, it tells me "An unknown error occured" (how incredibly helpful).

*Option 2*
My first attempt to get a router going was by using this guide 
[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)
But I got stuck there pretty quick when I found that I had no "Incoming Packets (INPUT)" option.

---

### Post by DotComFactory on 2006-08-11
That's the same problem I have when trying to share my wireless connection over the ethernet.  (See [http://ubuntuforums.org/showthread.php?t=233869]("http://ubuntuforums.org/showthread.php?t=233869").)  If I ever do have eth0 working in Firestarter, then ath0 (internal 802.11a/b/g) shows as not ready.

I consider myself computer-savvy, but learning Linux is like learning a new language in many aspects.  I'm sure this is an easy solution and that I'll say, "Of course!" when the answer is shown.

I'm watching this thread to see if any solutions pop up here . . .

-DotComFactory

---

### Post by jf3player on 2006-08-12
*Update*
Ok, so the "eth0 not ready" issue was solved by assigning a static IP to it.  And the dhcp3 server appears to be working now too as my test system has no trouble obtaining an IP address.  Now, when I run FireStarter, I still get a "Failed to start due to unknown error" but it starts anyway and the router only works with FireStarter running...

Alright, so half way through typing this I decided to remove FireStarter from the system and now the router seems to be working.  :???:

---


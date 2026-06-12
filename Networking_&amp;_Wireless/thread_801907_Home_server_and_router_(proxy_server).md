---
title: "Home server and router (proxy server?)"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by Dragonbite on 2008-05-21
I have a system I am trying to set up as a home server using Ubuntu Server.

I have Samba file sharing working (mostly), SSH, and LAMP.

I have have 2 NICs in it.

I want to set it up as a router

[computer]-|
[computer]-+-->[switch]-->eth0--[server]--eth1-->[DSLmodem]-->*internet*
[computer]-|

I want eth0 to..[LIST]
[*]Connect to the switch and thus the other computers
[*]Allow me to SSH into the server
[*]Allow Web and Samba traffic to pass through
[/LIST]
I want eth1 to..[LIST]
[*]Take internet traffic that comes in eth0 and pass it into the internet
[*]be as firewalled (secured) as possible from outside sources (I will not access this through the internet)
[*]All traffic is logged (prefferably is emailed or moved daily into another location and cleared out)
[*]utilizes parental controls
[/LIST]

I currently have Samba shares open so I don't want to connect it to the internet much more than I have to until I have a closed-down firewall between it and the internet.

I am hoping this is a fairly easy thing to set up. Even when I get a wireless router I still want the logging and parental controls if at all possible.

I am very new to networking, so any help is appreciated.
Thanks
~Drew

---

### Post by SpaceTeddy on 2008-05-21
if i understand you correctly, this [[COLOR="Blue"]guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874") should help you setting up ubuntu as a router. 
Please run through the steps, and if any question arise while going through it or something does not work, just ask.

hope it helps :)

---

### Post by Dragonbite on 2008-05-21
> **SpaceTeddy said:**
> if i understand you correctly, this [[COLOR="Blue"]guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874") should help you setting up ubuntu as a router. 
Please run through the steps, and if any question arise while going through it or something does not work, just ask.

hope it helps :)
That looks like a great place to start! Thanks!

From your experience, how secure is this setup? I just want to make sure my open Samba shares are not exposed to  the internet.

---

### Post by SpaceTeddy on 2008-05-21
this thing is not secure at all. For that, you will need to work on part "Configuring iptables (paket filter)" a lot more and acctually write/create a proper firewall for the machine. 

Some people say firestarter is good - i don't like it and do my stuff by myself. The aim of the guide was to make it work - not to make it secure (security requires understanding, and that is a lot harder to put in a howto than "run a bunch of commands")

if you are concerned about security, i can write down some basic rules that should help you :)

---

### Post by Dragonbite on 2008-05-23
That would be great! I'm probably going to try these settings this weekend, but I'll keep in mind they aren't totally secure so I may just set it up when i'm working on it until I feel comfortable.

---

### Post by mapes12 on 2008-05-23
Hi

I learnt a great deal from this tutorial:

[http://www.aboutdebian.com/](http://www.aboutdebian.com/)

It's based on Debian and so is Ubuntu.

There's days of stuff to help achieve your objective.

Hope this helps.

Mark

---


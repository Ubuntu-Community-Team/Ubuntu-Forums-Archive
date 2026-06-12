---
title: "PC to multitask as router?"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by Sastopher on 2008-04-18
Hi all!  New user here.

I recently converted my 'old' windows PC into an Ubuntu box.  I have 3 goals in mind:
1. Have a public computer in our living room usable for IM and web browsing.
2. A convenient means of playing digital movies or music on our entertainment system.
3. Replace our old linksys router.

Now, as I understand it, you typically don't want your router doing too much, but it's still a relatively fast computer and it won't be used too heavily aside from routing (and the occasional movie).  I'm wondering what the best way of setting up a home network/router around my ubuntu machine is; whether it be software that takes care of it for you, or the location of guides/other learning resources that might teach me how to set it up myself through scripts.  I'm looking for basic functionality, port forwarding, bandwidth throttling... that sort of stuff.

Right now, I'm fairly ignorant, but I've done some searching.  I've come across m0n0wall, which was highly touted by the series of users that recommended it, but when going through the documents it seems to run like an OS of sorts, and thus not what I want.  I've also come across webmin, which begs further review.

To state my question more succinctly: what is the best way to set up my computer as a router/firewall, while maintaining the basic functionality of a PC?

---

### Post by jetsam on 2008-04-18
Theres a howto [here]("http://ubuntuforums.org/showthread.php?t=713874") by SpaceTeddy and one [here]("http://ubuntuforums.org/showthread.php?t=111972") by Elias.

Now I'm going to try and convince you that you don't want to do this.  It isn't just for performance reasons that you don't want much running on a router-- it's primarily a security issue.  A gateway router by definition is exposed to the internet and having all the desktop services running leaves many attack vectors open to potential attackers.  

Second, putting the router and the desktop on the same machine will increase the complexity of your configuration.  You may have real trouble setting up your firewall correctly to, say, both run instant messaging and secure it at the same time.  

Third, there's performance.  Playing a movie, especially over the network, *is* heavy use.  

I think you'd be better off using your machine to do # 1 and # 2 on your list, and leave # 3 as a separate issue.  If the linksys isn't giving you trouble, you could just keep it around.  If it is, maybe replace it with a new router (or another dedicated machine if you like network configuration.)  

Just my 2 cents.  You're free, of course, to do as you want with your own set-up.

---


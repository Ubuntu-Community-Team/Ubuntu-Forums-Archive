---
title: "vpn config with PIA (private internet access)"
date: 2015-11-06
forum: Networking &amp; Wireless
---

### Post by dave205 on 2015-11-06
First thread I've started so I hope I'm doing this right and providing enough info. I searched and did not see where this is already covered. I look forward to learning a lot and sharing what I can to help others.

Just installed Ubuntu15.10 and still learning my way around. I use privateinternetaccess for my vpn.  I installed it and now I see the list of the many access points I can use in the network drop down at the top right of the desktop. I click one and it asks my pia password, I enter it and I'm on. All cool. The problem (really more of an inconvenience) is that I have to enter my pia passsword to _every one _of the access cities. Seems like I would be able to edit a conf file somewhere and have it in there. 

does anyone know of an edit I can make that will put my vpn password into each location?

when I use the pull down, upper right corner, select vpn connections>configurevpn, this is the screen I get to help give you an idea. 
[IMG]http://s23.postimg.org/4osh7rj1n/Screenshot_from_2015_11_06_22_36_34.png[/IMG]

---

### Post by dave205 on 2015-11-06
maybe this will help. Here's the Ubuntu install guide. Its been a couple days and I've worked on several systems since so while I'm not positive it worked as flawlessly as outlined, I believe it was close. (I think I might have been missing a few packages I had to add iirc.)


[https://www.privateinternetaccess.com/pages/client-support/ubuntu-openvpn](https://www.privateinternetaccess.com/pages/client-support/ubuntu-openvpn)

---

### Post by dave205 on 2015-11-07
well I found the config files!  "locate PIA" (imagine that ;) ) you can see here there are many. one for each location

[IMG]http://s23.postimg.org/lrcvkb67f/Screenshot_from_2015_11_06_23_07_57.png[/IMG]



each of those files contains the username but does not store the password. not even the locations I've used already.

---

### Post by PhilGil on 2015-11-07
Your passwords wouldn't be very secure if they were stored in plain text in a config file, would they? :)

They're in your user password store, which is probably called "Passwords and Keys". Open Passwords and Keys, select "Login" in the nav bar on the left, and look for entries like this: *VPN password secret for PIA - US Silicon Valley/org.freedesktop.NetworkManager.openvpn/vpn.* I'm not aware of any way to do bulk entry, but you could enter your passwords by hand there.

What I do is just wait until I use a particular server and then enter the password at login. It's kind of a hassle, but your system should remember the password so you won't have to enter it again for that server.

---

### Post by dave205 on 2015-11-07
> **PhilGil said:**
> Your passwords wouldn't be very secure if they were stored in plain text in a config file, would they? :)

They're in your user password store, which is probably called "Passwords and Keys". Open Passwords and Keys, select "Login" in the nav bar on the left, and look for entries like this: *VPN password secret for PIA - US Silicon Valley/org.freedesktop.NetworkManager.openvpn/vpn.* I'm not aware of any way to do bulk entry, but you could enter your passwords by hand there.

What I do is just wait until I use a particular server and then enter the password at login. It's kind of a hassle, but your system should remember the password so you won't have to enter it again for that server.


very true Phil. very true.... :) 

thanks for replying. I actually did not know about the "passwords and keys" application. that's a new one on me. I opened it up and sure enough, there were entries for the connections that I had already made. And yeah, it looks like I'll just need to enter the pwd (once) for each connection and after that it sticks.  Kind of weird how when I connect PIA on windows or on my android phone, then it just uses the password that I enter once for all connection cities.  I'll continue to tinker with it and report back if I find a way to set it up with only one pwd entry.

---


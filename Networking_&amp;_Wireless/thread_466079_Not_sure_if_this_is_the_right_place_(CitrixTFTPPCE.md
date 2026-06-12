---
title: "Not sure if this is the right place (Citrix/TFTP/PCE)"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by harner on 2007-06-06
The company I work for decided to purchase a Citrix Farm.  My job is to get the machines on our network on the Citrix farm.  We aren't in production with it yet, but the sooner I figure this out, the better.

For starters, how are you guys doing today?  This is my first post.  I was always a fan of openSUSE, but lately I've been installing Ubuntu server and making it a Kubuntu workstation (work, home, girlfriend's pc, and etcetera).  The test server I'm working with is a Dell workstation (Optiplex GX520) with Kubuntu 7.04.  This isn't a Dell support question, either.  The machine came with XP, originally.  I am using a Winterm to test my progress.

What I'm trying to do:
I want to configure a server (Kubuntu Dell box) in such a way that when a machine (winterm) boots on a network, it'll boot via PXE and load an image that is placed on the server.  

What I've done so far:
When I set up the server, I loaded a Ubuntu image on it, and I booted up the Winterm.  It seemed to work fine!  The only problem was, I need a Linux image to shoot the OS over to a Citrix client so our users think it's their actual desktop that they are working with.

Where I'm confused:
I loaded the 2XThinClientServer.  2X is basically Citrix's cheap rival.  The server package could be installed, but I have to take down the TFTP server and MySQL.  I can't load the image on the winterm if it can't boot to PXE.

What I'd like to know:
Is there a way for me to accomplish my goals?  I don't need to use the 2XThinClientServer.  Does anyone have a custom Ubuntu image they use?

THANKS!

---

### Post by harner on 2007-06-06
bump

Any suggestions?  Thanks.

---

### Post by harner on 2007-06-07
Someone here has to know...  I get views but no replies?

:KS

---


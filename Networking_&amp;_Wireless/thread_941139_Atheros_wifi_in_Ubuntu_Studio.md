---
title: "Atheros wifi in Ubuntu Studio"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by sidneylopsides on 2008-10-07
I'm new to Linux and not 100% on what I'm doing, so I'm hoping someone can help.

I've installed Ubuntu Studio on my Acer 5315. It has an Atheros wireless adapter, AR242x is what it shows as.
First I had 8.04 and wifi worked with madwifi.
With Studio it doesn't work.
I;ve tried madwifi, I downloaded stuff adn did the make, make install etc, all worked with no errors, but it doesn't show the wireless adapter anywhere. 
I've put that machine away due to frustration at the moment, but everything I've followed off forums has worked without error, but still doesn't do anything.
iwconfig shows the wired connection, but nothing else.
After trying a couple of days with madwifi, I've removed that to try ndiswrapper. 
The ndiswrapper driver does show as loaded, and I've blacklisted the ath_pci and ath_hal drivers. 
Everything I check shows the drivers loaded and working, but the interface doesn't appear in the network tools. 

sudo lshw -C network shows it there with ndiswrapper loaded.

I'm not sure what specific output info you need to help with this, so whatever you need please tell me and I'll post it.

---

### Post by sidneylopsides on 2008-10-08
No hints then?

---

### Post by jmbargar on 2008-10-08
Why are you compiling the madwifi source if you can install it easily using Synaptic? You can find it in System -> Administration -> Synaptic Package Manager. If you are not using a Gnome desktop, you can install madwifi typing in a terminal something like this:

> sudo apt-get install madwifi-tools

You will need a network connection to install it with this method. Synaptic will download the corresponding binary package from internet before installing.

Good luck!

---

### Post by sidneylopsides on 2008-10-08
I did a normal install on Hardy, and it was fine. When I tried it on Studio it didn't work.
I read around and it seemed that getting the source and making it for my kernel might work as it's a different one (realtime).
It makes ok, all the right stuff seeems to be installed, headers and stuff, and retricted modules. 
as trying that in various ways didn't work I went to ndiswrapper, that looks like it's working but doesn't show the device in networking.

---


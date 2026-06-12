---
title: "Internet connection refused to work after logging off."
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by Onion_Knight on 2007-04-11
Hello to all. Here is a bit of background to my problem. Before installing Xubuntu, the Live CD allowed internet access to my computer - which is connected via a Realtek RTL8139/810x NIC plugged via an ethernet cable to a wired modem - and yet, after installation, it stopped working. After attempting to use pppoeconf and failing, I configured my network settings from DHCP to static IP and, afterwards, was again able to browse the net, albeit slowly. Now, after logging out, the connection is off again. It might also be worth noting that the  computer is unsuccessful in pinging 209.85.129.104 (one of Google's IP addresses). 

There's also a problem with my screen resolution which is now stuck at 640x480 but that can wait. As of now, this is what I hope can be fixed first as it's a bit of a pain to keep logging in to Windows just to search the Internet for help. Thanks a lot! Using Linux for the first time and looking a bit at its innards is a bit of a revelation by the way. Linux is awesome!

---

### Post by Onion_Knight on 2007-04-12
Hello. I'm bumping this because it seems that logging off or shutting down was not the cause of my problem after all. I reinstalled Xubuntu and was able to connect to the internet using static IP, as before. I then tested my internet connection by logging off/restarting/shutting down my computer for a few times and I was still able to connect each time afterwards. It was only after I logged in to Windows (the same thing I did before, I remember) that the internet connection failed. I appreciate any help.

---

### Post by Floppyjoe on 2007-04-12
> **Onion_Knight said:**
> Hello. I'm bumping this because it seems that logging off or shutting down was not the cause of my problem after all. I reinstalled Xubuntu and was able to connect to the internet using static IP, as before. I then tested my internet connection by logging off/restarting/shutting down my computer for a few times and I was still able to connect each time afterwards. It was only after I logged in to Windows (the same thing I did before, I remember) that the internet connection failed. I appreciate any help.
When I see a post like this I am always tempted to say "Don't log in to Windows!!!:D " but I know that is not what you are looking to hear.
It seems like an odd problem. I hope you find the answer.

---

### Post by Onion_Knight on 2007-04-12
> **Floppyjoe said:**
> When I see a post like this I am always tempted to say "Don't log in to Windows!!!:D " but I know that is not what you are looking to hear.
It seems like an odd problem. I hope you find the answer.

Yeah. Ideally, I would want to use just one OS for everything (that being Linux of course :D) but I still need to use Windows from time to time (for the old games that I have mainly). Also, it's good to keep a few other OS's installed and to try to learn about them as I'm a CS student. That's really a mandatory thing :D.

---

### Post by Floppyjoe on 2007-04-12
> **Onion_Knight said:**
> Yeah. Ideally, I would want to use just one OS for everything (that being Linux of course :D) but I still need to use Windows from time to time (for the old games that I have mainly). Also, it's good to keep a few other OS's installed and to try to learn about them as I'm a CS student. That's really a mandatory thing :D.

There is a wonderful program called VMware Server that you can download for free and this will allow you to make virtual machines on your Linux Box. These virtual machines can be most any kind of Operating system. I don't know how well it works with Graphics intensive games but other applications seem to run very nicely in it. In my opinion it seems better than Wine(the linux windows emulation software) however I may be wrong there. Sorry to get off topic. The original topic was:

> Hello to all. Here is a bit of background to my problem. Before installing Xubuntu, the Live CD allowed internet access to my computer - which is connected via a Realtek RTL8139/810x NIC plugged via an ethernet cable to a wired modem - and yet, after installation, it stopped working. After attempting to use pppoeconf and failing, I configured my network settings from DHCP to static IP and, afterwards, was again able to browse the net, albeit slowly. Now, after logging out, the connection is off again. It might also be worth noting that the computer is unsuccessful in pinging 209.85.129.104 (one of Google's IP addresses).

There's also a problem with my screen resolution which is now stuck at 640x480 but that can wait. As of now, this is what I hope can be fixed first as it's a bit of a pain to keep logging in to Windows just to search the Internet for help. Thanks a lot! Using Linux for the first time and looking a bit at its innards is a bit of a revelation by the way. Linux is awesome!

---

### Post by handy on 2007-04-13
***@ Floppyjoe:***  Hi, I noticed ***the swindle*** in your signature...

You may find [***_this CSIRO site_***]("http://www.bml.csiro.au/SNnewsletters.htm") interesting, & if I may draw your attention to ***Update 64***, & the first document called:

***The biology of global warming and its profitable mitigation***

Profoundly interesting to my mind...

---

### Post by Onion_Knight on 2007-04-14
Man, it works!!!!!!!! I finally found the cause!!!!!!!! 

I was still reading about this problem when it struck me that maybe, the problem was because I never shut down Windows XP before I decide to boot Xubuntu but merely hibernate it. That may explain the error message from pppoeconf that another ppoe process may be controlling the modem or something like that. And so I shut WinXP down and booted Xubuntu and what do you know? The bars from the network monitor applet started rising as I tested a website!!! I'm still jumping up and down with excitement (nobody's at the house anyway so no problem :D). Maybe this solution can be recommended to a lot of those with network problems. I imagine most of them also have WinXP installed and use hibernation exclusively. 


I'm going to have a look at what you were saying Floppyjoe. Thanks a lot. And thanks to all too!

---


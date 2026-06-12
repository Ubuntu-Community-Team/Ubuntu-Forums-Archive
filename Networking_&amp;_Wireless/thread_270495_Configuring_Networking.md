---
title: "Configuring Networking"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by TomFumb on 2006-10-03
Hi, this is the kind of problem that I'm kind of embarassed to ask about, but I'll go ahead anyway. 

I just installed xubuntu on my shiny second-hand x22, and I want to start messing with the network settings. However, every time I try to find out how to do this on google, I get told to go to applications>system>network, or system>network, or some other variation. My big problem is that I have no *>*>network menu options. Do I need to install a network manager before I can access the network configuration (surely not)?, or do I need to do something magical to get the network options on a menu (I've been through all the functions I can add in xfce)? 
I wouldn't mind just knowing how to get to it through the command line, but so far no joy. 
Any help on this would be much appreciated, this is the kind of query that's quite difficult to answer on google or this forum, as the wording of my problem throws up so many results.

TomFumb

---

### Post by spd106 on 2006-10-03
If you want to start messing around properly then the best tools are at the terminal anyway. The gui is simple to use but not very powerful. To get you started look at **ifconfig** and **ip**.

---

### Post by kipeloff on 2006-10-03
'lspci | grep Ethernet', and/or 'dmesg | grep eth';
commands show if your Ethernet network device is identified.
I have found very nice basic guide to troubleshoot networking,
[http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)

---


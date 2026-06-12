---
title: "Upgraded to Intrepid, network connections crash"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by -|Veni_Vidi_Vici*- on 2008-11-05
I upgraded from 8.04 to 8.10 and now my network connections don't work. The default "Network manager" icon on my taskbar appears after bootup, but disappears quickly. I assume that this is due to the network manager crashing due to some unknown error. 

I am trying to connect to my university's wireless connection [as per the instructions on this page for UT [https://wiki.ubuntu.com/AustinTeam/Docs](https://wiki.ubuntu.com/AustinTeam/Docs)]. I have followed these instructions in the past with no problem. However, now I cannot choose the key type. The dropbox for it is missing from the configuration dialouge after upgrading to ibex. I would post a screenshot but I do not know how to bring back the network manager. But when I did manage to get the process running, the key type box wasn't there.

I can go to the taskbar, right click and add the "network monitor", which is different than the network manager. I cannot see my wireless connection with the network monitor. I can goto network configuration from system>preferences>network monitor, however, upon trying to change any of my settings for my access points, nothing happens. (by this I mean nothing happens when I click "edit" for a connection, which normally launches the network manager, which I can't seem to launch.

Sorry if I said too much. I dont know how to fix this. I appreciate the help, and let me know if you need any logs (and where to find them).

---

### Post by karlatsaic on 2008-11-05
Don't despair. Ubuntu 8.10 has a far superior Network Manager 0.7 which you'll like once you get it up. First remove the Network Monitor, as NM 0.7 shows all that (and way more) when you right click it. The problem is that the upgrade left some of your old Network Manager settings around.

Look at post #14 here:
[http://ubuntuforums.org/showthread.p...-applet&page=2]("http://ubuntuforums.org/showthread.php?t=964900&highlight=nm-applet&page=2")

I had the same problem and cleaning out /etc/network/interfaces per the post brought it back. Note that NetworkManager is now brought up with sudo /etc/init.d/NetworkManager restart . 

If you still have problems you could also reinstall Network Manager (or remove it completely and then reinstall, but remember to use a install iso CD as a synaptic source (System/Administration/Software Sources) as you won't be connected to the internet). Whatever you do, I would not recommend installing wicd as some others really like - it has no vpn for one and it gets you off the track of the gnome Network Manager which ubuntu wants to keep in the mainstream and will only improve as they go forward. I had the best luck with a clean install off the official iso cd once I decided to go forward. If you have a solid backup of all your user files and a record of all your extra installs, the clean install only takes an evening to get everything back in place and you can be sure there are no lingering issues with having remnants of 8.04 configuration lying around. I also found it useful to just boot off the live cd iso to test out the new NM 0.7 and my wireless prior to doing the full fresh install - note which driver is selected at that time (lshw -C network).

I also had problems with the wrong driver being selected - that will depend on your card, but you need to get your Network Manager (not Monitor) up and going normally first. If you're interested in what I encountered see [http://ubuntuforums.org/showthread.php?t=858714](http://ubuntuforums.org/showthread.php?t=858714) . Hopefully, your driver will be just fine.

---

### Post by Claudestephane on 2008-11-05
This ousnd very helpful. If only I had time right now, I would defer thanking you until I tried it. Thanks

Claude

> **karlatsaic said:**
> Don't despair. Ubuntu 8.10 has a far superior Network Manager 0.7 which you'll like once you get it up. First remove the Network Monitor, as NM 0.7 shows all that (and way more) when you right click it. The problem is that the upgrade left some of your old Network Manager settings around.

Look at post #14 here:
[http://ubuntuforums.org/showthread.p...-applet&page=2]("http://ubuntuforums.org/showthread.php?t=964900&highlight=nm-applet&page=2")

I had the same problem and cleaning out /etc/network/interfaces per the post brought it back. Note that NetworkManager is now brought up with sudo /etc/init.d/NetworkManager restart . 

If you still have problems you could also reinstall Network Manager (or remove it completely and then reinstall, but remember to use a install iso CD as a synaptic source (System/Administration/Software Sources) as you won't be connected to the internet). Whatever you do, I would not recommend installing wicd as some others really like - it has no vpn for one and it gets you off the track of the gnome Network Manager which ubuntu wants to keep in the mainstream and will only improve as they go forward. I had the best luck with a clean install off the official iso cd once I decided to go forward. If you have a solid backup of all your user files and a record of all your extra installs, the clean install only takes an evening to get everything back in place and you can be sure there are no lingering issues with having remnants of 8.04 configuration lying around. I also found it useful to just boot off the live cd iso to test out the new NM 0.7 and my wireless prior to doing the full fresh install - note which driver is selected at that time (lshw -C network).

I also had problems with the wrong driver being selected - that will depend on your card, but you need to get your Network Manager (not Monitor) up and going normally first. If you're interested in what I encountered see [http://ubuntuforums.org/showthread.php?t=858714](http://ubuntuforums.org/showthread.php?t=858714) . Hopefully, your driver will be just fine.

---

### Post by -|Veni_Vidi_Vici*- on 2008-11-05
Nope. That did nothing. Still have the same problem.

---

### Post by karlatsaic on 2008-11-06
Did you try booting off the live 8.10 CD and connecting wireless? That way it would be as if it were a clean install and you could discover if there is some fundamental conflict between your wifi card, the router you're trying to connect to, the driver being used, the linux kernel, or the Network Manager. When I have problems like this, I find it useful to send the section of your /var/log/syslog which clearly shows the sequence of the connection acquisition. If you really have a problem, it would be best to file a bug, including the output of lshw -C network.

---

### Post by Claudestephane on 2008-11-06
Thanks. It's a bit embarrassing to acknowledge that checking "allow roaming" allowed the status bar network manager icon to change and display all available signals. A work flow issue. Clearly one needs to select roaming to find signal, then enter login requirements if needed, allowing new wireless connection to be saved. :) 
BTW Ubuntu 8.10 has been very smooth in last 12 hours.

Claude

---


---
title: "Wired and Wireless at once"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by perrti-y02 on 2008-10-22
I have read a few other forums on how to do this and tried what i can, but I am unable to connect to both Wireless (for internet) and wired (file server is planned but can't yet implement)
Could someone tell me exactly what i need to to on both machines or point me to a tutorial that does it.

Many Thanks

---

### Post by perrti-y02 on 2008-10-23
bump

---

### Post by caleb12 on 2008-10-23
While I'm not exactly sure on this method; google can probably answer the areas I'm not clear on - the basic idea is that you need to setup NAT and/or IP Forwarding in order for the packets to be routed properly between interfaces. 

To be honest, I do it all the time. I user UFW as a firewall and all I do is plug and go... Wireless is always on the internet and I have a private LAN that I work with off the wired. 

In this situation, I am guessing that UFW sets up the rules for the packets to be properly routed between interfaces. Now, how to do this by editing config files and setting up IPTABLES manually... would take longer than it does to use UFW. 

Check out GUFW as well, it's a GUI for UFW. (Uncomplicated FireWall) it comes standard in Ubuntu.

---


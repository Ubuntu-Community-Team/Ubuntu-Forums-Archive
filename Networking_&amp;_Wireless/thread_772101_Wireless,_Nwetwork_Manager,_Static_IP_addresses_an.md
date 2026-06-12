---
title: "Wireless, Nwetwork Manager, Static IP addresses and backups"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Metz on 2008-04-28
Ok, 8.04 install went remarkably well....very pleased with the results.

I've got a couple of things I still need to sort.... namely DVD not burning properly on an external USB burner.....and setting up static IP address.

On the static IP front, I've managed to get my Intersil Prism card working for the first time since 6.04....which I'm very pleased about. However, I can't seem to get it to work if I assign a static IP. Everything in my house runs with a static IP on the network....3 servers, 4 laptops, and 3 mobile phones/PDAs. But this laptop doesn't seem to want to play that way if NetworkManager is running.

Is there a way around it ??

On the backup front, what I'd like to know is which configuration files I need to backup in order to guarentee that I can get back to my current state of working wireless if I screw things up trying to mack changes to add a static IP?

---

### Post by bdoe on 2008-04-28
I've never had much luck with Network Manager myself. Either it didn't like to play nice with static IP addresses, had issues with DHCP, or wouldn't remember WPA keys, or would conveniently forget how to connect to my wireless network. When Hardy's Network Manager proved to be no better, I dumped it and installed WICD instead. Now I have no more network problems.

Give WICD a try and see if that solves your problem.

---

### Post by Metz on 2008-04-29
Will do... thanks for that. 

Any idea which files I need to backup, just incase? ;) If nothing else...it is currently working, and as the laptop get used to work from home (Radmin running though Wine...Marv!! :):))... I kinda wanna make sure I can get back to a working state if I screw up....

---

### Post by bdoe on 2008-05-07
Well, that's the beauty of Linux - it's really hard to royally screw it up to the point where you can't recover it. The worst I've done was to mess up my xorg.conf file, which made Gnome unusable. But even then, the computer booted to a command-line interface where I was able to fix the file and get things working again.

---


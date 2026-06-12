---
title: "Sudden network failure"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by gh81 on 2007-08-09
Hello,

After successfully using the same network settings in Ubuntu for a couple of years, I turned the computer on this morning to find myself unable to browse the web, connect to anything via ssh or ping anything except for the ip address of my router (using ubuntu feisty). I am on a dual boot system with Windows XP, where the network works fine. I had not changed any settings and haven't noticed any updates recently to do with networking.

The network is a university network, which I connect to with a static IP address using gateways, dns server search orders etc as specified by the university. I have checked in gnome network settings and all of these settings are as they should be. I have checked /etc/network/interface, and the settings there are fine too.

The only relevant warning I could see from dmesg was to do with ipv6. Following advice I found in another forum I have tried disabling ipv6 by changing a line in /etc/modprobe.d/aliases but it made no difference.

I suspect that avahi-daemon did not load correctly, I saw some message about it on startup but it went by too quickly to read and I couldn't find it in dmesg (don't know where else to look). Tried starting it manually but it made no difference.

I hope someone can help me, I'm completely out of ideas!

---

### Post by gh81 on 2007-08-09
Problem is partially fixed: It seems that the subnet mask in my settings had changed itself from 255.255.255.0 to 255.255.0.0, I hadn't noticed when I posted this topic. I changed it back and can now connect to the network.

I'd still like to know why it randomly changed itself, if anyone has any suggestions.

---


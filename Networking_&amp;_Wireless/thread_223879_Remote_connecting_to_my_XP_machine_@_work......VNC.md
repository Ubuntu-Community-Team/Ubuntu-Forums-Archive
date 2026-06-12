---
title: "Remote connecting to my XP machine @ work......VNC and VPN!"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by mwob on 2006-07-27
Hi,

I want to remote-connect to my windows XP machine at work, from my home PC.

I have managed to set up a VPN connectiuon to my work, using PPPT, but I'm unsure what I need to do now. I installed "TightVNC" on my windows machine which should allow a VNC connection, but I don't know what to do next!

I opened "Terminal Services Client" in Ubuntu, and lo and behold theres a VNC option to connect - great! But when I select "VNC", it asks me for the path to a VNC file?! I have no idea what this means, what vnc file does it mean, do I need to create one? 

Thanks in advance :)

Matt

---

### Post by mwob on 2006-07-27
Anyone?

:(

---

### Post by apjone on 2006-07-27
do you have your sys admins permission to do this ? just try RDP!!

rdesktop -f mymachine

---

### Post by Threbus5 on 2006-12-23
Hmmm.

If remote desktop access has been granted on the windows machine - you should be able to use Ubuntu's terminal server client to connect using RDP Not vnc.

Under the "General" heading for terminal server client select the Internet IP address of your remote windows computer, choose a protocol of RDP, and enter your windows admin username and password - I also included the windows domain (Workgroup) and this just worked on my home LAN. If RDP fails, then try RDPv5.

However, as they say the "onliest things is..." you must be able to reach through the work network to your office machine. For example if it is connected to the Internet through a firewall or router you must have a path through that firewall (In order for the Ubuntu RDP to connect to my home LAN windows machine, I had to disable the windows firewall (in spite of the windows firewall setting that indicated it would allow remote desktop connections.)

Hope this helps.

---


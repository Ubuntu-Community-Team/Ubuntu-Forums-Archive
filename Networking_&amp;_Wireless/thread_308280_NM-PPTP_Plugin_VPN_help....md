---
title: "NM-PPTP Plugin VPN help..."
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by kufford on 2006-11-27
Ok... Here's the deal... I work IT for a state University and feel like an idiot as I can't figure out... I've setup network manager with the PPTP plugin and honestly feel that it should work. Here's the various data that may come in handy while troubleshooting. 

[http://www.wsu.edu/vpn/msVPN.html](http://www.wsu.edu/vpn/msVPN.html) - that is the link for the windows VPN support page that we can access. It's a pretty standard set up, follows all of the windows defaults. 

[http://www.wsu.edu/vpn/macVPN.html](http://www.wsu.edu/vpn/macVPN.html) - that is the mac documentation. Again, pretty straight forward. 

My laptop is a dell inspiron e1505 with a intel 3945 wireless card. It runs fine on my home network and is the ultimate ubuntu laptop IMO. However, I can't get it on the university VPN. I could in dapper using pptp-config but since that program is borked in edgy and this plug-in is so much neater - I'd prefer to use it.

I'm out of ideas... Please help. Note, that once I figure out the possible network settings its going to go on the linux documentation wiki for the school - hopefully starting some more support for *nix based systems on the network. I've contacted various individuals in the IT department, but none are familiar with the program and the various windows bureaucracy sends me in circles. Thanks so much...

---

### Post by ironphil on 2006-12-04
Is there any error message? That would help.

One possibility (for which there is no solution yet) is that the mtu is hard coded at 1496 in the plugin. Some vpn need a lower mtu and there is no way to decrease it yet. The dialog where you can set the mtu and mru in the plugin are in fact doing nothing!!! That is corrected in the next version of the plugin which is still not packaged for Edgy.
For pptpconfig, the author does not have access to an Edgy installation yet so there are no progress.

VPN (pptp) is screwed up big big time in Edgy... leaving a lot of users without any way to connect.

---


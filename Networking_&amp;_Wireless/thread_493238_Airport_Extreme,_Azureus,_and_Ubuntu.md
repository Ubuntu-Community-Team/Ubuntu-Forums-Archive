---
title: "Airport Extreme, Azureus, and Ubuntu"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by coreytn81 on 2007-07-05
Hello, new to the forums and Linux in general :)

I guess I'm going through a little culture shock being dropped from my easy, let-me-hold-your-hand OSX/Windows environments to the open ended Linux world.

I recently came across an article on how to setup a headless torrent rig using Ubuntu and Azureus: [http://nerdica.com/?p=30](http://nerdica.com/?p=30)

I don't have any qualms with keeping the GUI, especially since I'm new to all of this.

typos aside I thought it would make for a nice weekend project and give me some Linux exposure. Anyways, I have an old PC box, dumped windows and installed Ubuntu Feisty Fawn. I'm hard wired into a Airport Extreme (I have other machines, namely laptops that access the internet wirelessly through the airport which I would rather not disrupt). I have a few issues:

1. I would like to access my machine at home remotely (say, at work). I turned on the remote desktop feature within Ubuntu, and using Chicken of the VNC tried to access the box at work. I ran across the problem of getting a internal IP address (I think?) instead of an external address. I assume it's the Airport blocking that (via NAT? Internal Firewall?). I'm clueless as to how to get to the machine through the aiport.

2. Azureus reports NAT/Firewall issues when downloading, which I think comes back to the settings I have within the Airport Utility. I have tinkered with Port Forwarding within the Airport Utility and it still doesn't seem right.

(on a side note)3. I'm trying to use an external hard drive to store the torrent files to (a Seagate FreeAgent 250). When I do get downloads to work, I'll leave them running for awhile and come back to get nullpointer exception errors. I read somewhere that after 15 minutes or so the hard drive stops spinning and can cause errors.. I'm probably wrong about that.. I tried to troubleshoot it and ran across an article about upgrading Sun Java to 5.0 or 6.0 would alleviate this problem.

I'm completely new to all of this, so any direction would be great.

Thanks

---

### Post by coreytn81 on 2007-07-06
Update:
I plugged the Ubuntu machine directly into the cable (Comcast) modem and it works flawlessly. So it's definitely the Airport Extreme that is causing connection/firewall/NAT issues.

 I solved the Seagate FreeAgent issue by selecting the option within Azureus to send completed downloads to the portable drive. I did this by going into Azureus: Tools>Options selecting Files, and pulling down the submenu and selecting "Completion Moving" and turning on "Move Completed Files (After Download)" and under the "directory" field entering in the path to the FreeAgent.

---


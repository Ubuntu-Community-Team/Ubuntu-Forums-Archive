---
title: "Wireless adapter reset on startup"
date: 2017-01-26
forum: Networking &amp; Wireless
---

### Post by mrxenoverse on 2017-01-26
I've been having some hang-ups trying to get my Netgear A6210 wifi adapter to function properly. At this point it sort of works. Most of the time when I boot and log in, I have to run ```
sudo service network-manager restart
``` to get it to start working, otherwise the network settings tell me "Device not managed." That's all well and good, so now I'd like to script that command so I don't have to type it into the terminal and type my password every time I boot. So I've created this .sh file containing ```
#!/bin/bash
# network-manager restart script
sudo service network-manager restart
``` and saved it to /bin. Then I made a .conf file containing ```
start on startup
task
exec /bin/netrestart.sh
``` and saved that to /etc/init.

I'm quite inexperienced with Ubuntu and the idea of scripting in general. From what I've been looking up this should run my script as root before I log in, but it doesn't seem to be doing anything. I don't really know where to look to find out if the script is running at all. I have a feeling it's an issue with permissions.

This isn't really an urgent issue but it would clear up an annoyance with an OS I otherwise love. Any help is greatly appreciated.

EDIT: I don't know if this is relevant to my issue but here is the result of wirelessinfo, run before restarting network-manager: [ATTACH]273414[/ATTACH]

---


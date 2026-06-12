---
title: "quickswith and boot parameters"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by Del Pede on 2008-09-05
I've been using quickswitch for a while, to manage the network setup, for when i work outside the office. In the office i authenticate on my laptop through NIS, and my homedir is mounted via NFS. I therefor use a kinda static network setup, to get the wireless working. 

I've added some bootparameters to grub, so that when i boot i can manage which services to start up, since NIS really really kills the machine, when it doesn't connect to the NIS server. Also i logon to the office wireless during boot up, so i can mount the NFS shares before i log in. 

So i've added switchto -s to my rc.local to that it will switch to the profile i've selected through my boot parameters. The thing is though, that it never really selects the profile i select through my boot parameteres. It selects the last know working profile through /etc/switchto.last

I can't really see where the problem is, but it seems that quickswitch also opts for the last know working configuration, other than then the one in my boot parameters. cat /proc/cmdline shows that it does get parsed, but not picked up by switchto -s

I know this is a bit of a long shot, but i hope that someone out there might have a possible sollution

thanks in advance
Del Pede

---


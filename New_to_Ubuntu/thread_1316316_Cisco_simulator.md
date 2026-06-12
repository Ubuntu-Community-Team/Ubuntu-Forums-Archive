---
title: "Cisco simulator"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Malizia on 2009-11-05
I've been on Ubuntu for 2 hours now and my heads already spinning, so please be gentle with this newbie. ha

I want to install a Cisco simulator on my box, but not sure what to use and where to start. I'm running Ubuntu 7.04 Feisty. Anyone have a nice tutorial already set up for me.. please oh please...

---

### Post by kingbilly on 2009-11-05
Are you talking about emulating a router ios?  or packet tracer?  i know packet tracer works.

---

### Post by Malizia on 2009-11-05
router ios - but i'd appreciate the info on the packet tracer

---

### Post by lavinog on 2009-11-05
> **Malizia said:**
>  I'm running Ubuntu 7.04 Feisty. 
Why are you using 7.04?  Support for Feisty expired already, and I don't think the repository is still available.

---

### Post by kingbilly on 2009-11-05
Packet tracer runs quite well on linux natively. 

[http://cisco.netacad.net/cnams/resourcewindow/noncurr/downloadTools/app_files/PacketTracer52_i386_no_tutorials_installer-deb.bin]("http://cisco.netacad.net/cnams/resourcewindow/noncurr/downloadTools/app_files/PacketTracer52_i386_no_tutorials_installer-deb.bin")

Good luck on the router ios ):P

---

### Post by alphacrucis2 on 2009-11-05
[http://www.gns3.net/](http://www.gns3.net/)

The Windows version might work under Wine? I think you also have to get the actual ios from cisco. These are usually distributed as files that end in .bin


Edit. Looking further it appears that you can get a linux version of the actual router emulator here:

[http://www.ipflow.utc.fr/index.php/Cisco_7200_Simulator](http://www.ipflow.utc.fr/index.php/Cisco_7200_Simulator)

---

### Post by tommynz1975 on 2009-11-05
a google  under
google.com/linux

gave me this as my 1st hit
[B][URL="http://sourceforge.net/projects/pyios/"]*CISCO IOS Simulator* | Get *CISCO IOS Simulator* at SourceForge.net   
[/URL][/B]

**[http://sourceforge.net/projects/pyios/](http://sourceforge.net/projects/pyios/)**


Best of Luck and welcome to Ubuntu

---

### Post by The Cog on 2009-11-06
> **alphacrucis2 said:**
> [http://www.gns3.net/](http://www.gns3.net/)

The Windows version might work under Wine? I think you also have to get the actual ios from cisco. These are usually distributed as files that end in .bin

GNS3 is in the universe repositories for Karmic (don't know about earlier Ubuntu versions). Couldn't be easier!

---

### Post by Malizia on 2009-11-07
> **lavinog said:**
> Why are you using 7.04?  Support for Feisty expired already, and I don't think the repository is still available.

My buddy hooked me up with this machine last x-mas, feisty was the OS he installed. From what i've seen 8.10 seems like it is the best match for cisco simulators. I'm studying for a CCNA and need hands on experience. I've also been browsing ebay for cicso routers and study labs. Any ideas what version of ubuntu would be best for me?

---

### Post by CharlesA on 2009-11-07
> **Malizia said:**
> My buddy hooked me up with this machine last x-mas, feisty was the OS he installed. From what i've seen 8.10 seems like it is the best match for cisco simulators. I'm studying for a CCNA and need hands on experience. I've also been browsing ebay for cicso routers and study labs. Any ideas what version of ubuntu would be best for me?

Not sure which one would be best, but I'd say go with 8.04 since it's a LTS release. 7.04 isn't supported anymore.

---


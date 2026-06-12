---
title: "Wireless PCI Card lost after Suspend/Hibernate"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by SysTech on 2007-05-30
Hi, 

I'm on Feisty and my Linksys PCI card, WPC54G v2,  works fine on initial start up on my laptop but after a suspension or hibernate the card does not come back unless I reboot. 

Any suggestions? 

```
Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
 Subsystem: Linksys WPC54G Ver.2 802.11G PC Card
 
```

Thanks!

---

### Post by tommie74 on 2007-06-17
My computer with Xubuntu feisty had a problem with getting an ip-adress after waking from hibernation. I´ve solved this problem by changing /etc/default/acpi-support

Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

Hope this will work for you to,
Thomas.

---

### Post by jtp51 on 2007-06-19
Thank you. This solved the issue on a ThinkPad R50p as well.

---

### Post by Billi on 2007-06-25
This worked on my compaq armada E500 with an old linksys wpc11 ver4 card. The "gurus"and sysadmins  at my local LUG said getting  wireless working would be tough, and power managemament nearly impossible. Well Fiesty found and installed my wireless card by itself, and with a few more tweaks from you guys like this one, I'll have my laptop running better than some of the ms-powered notebooks of similar vintage. I keep telling all those slackware and gentoo worshipers that maybe, just maybe, it's time to try Ubuntu. Thanks for the help, and for continuing to make it better.

---

### Post by SysTech on 2007-08-04
This solved my problem as well. Thank you very much!!!!!!!!

---


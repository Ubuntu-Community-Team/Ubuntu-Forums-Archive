---
title: "Help with driver issues for old HP machine"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by zze86 on 2009-04-20
First off, thanks for taking the time to read my thread. I'm a complete Noob to Ubuntu but would consider myself an above average user in Windows. I've recently installed Ubuntu 8.10 Desktop on one of my P4 laptops and really liked the look and feel of it so I decided to try and get my HP Pavilion 6835, an old P3 generation Celeron PC, working for print server/NAS duties but I am having issues with Ubuntu 8.10 recognizing hardware on the PC. Current specs:

833mhz Celeron CPU (OEM installed)
512mb ram (upgrade)
30GB HDD (OEM installed)
230W PSU (upgrade)
PCI modem card (OEM installed)
PCI ethernet card (OEM installed)
PCI 5-slot USB 2.0 card (upgrade)

I loaded Ubuntu onto the PC but it fails to recognize the ethernet card or modem card, doesn't matter which edition desktop or server. Now that I think about it I haven't tried the USB 2.0 ports or the onboard sound so I don't know if either of those works either. onboard video seems to work and the onboard USB 1.1 ports are working. the modem is not a big deal but does anybody know what I can do to get the ethernet card working?

I looked for drivers from HP but none are available for a linux based install. I don't know the ethernet card manufacturer so I haven't gone to any other website looking for other drivers. 

Reading through some of the Ubuntu documentation though, specifically this page [https://help.ubuntu.com/community/i810](https://help.ubuntu.com/community/i810) it appears that the i810 chipset driver is not supported in these lastest releases. although the article seems to be talking more about monitor issues could this be the issue? Wouldn't it be the case that not having this chipset driver make the machine NOT work at all though?

Also, reading through the Ubuntu documentation it sounds like Ubuntu desktop and server are built on the same kernel and have many of the same features, it's just a matter of enabling it. I would much prefer the GUI of the desktop edition vs the command line of the server edition. Can I enable the server edition to use the desktop GUI or can I have the desktop version use the features of the server edition (RAID functions, print server)?

Thank you again.

-Chee

---

### Post by inobe on 2009-04-20
hi and welcome


go to applications> accessories> terminal.

type

```
lspci
```

hit enter and copy and paste the output on your next post.

i don't know how much help i can provide but am able to help you with searching for a solution.

edit: i see it may be difficult to copy over the information without an internet connection, i have all day !

note: an ubuntu system update tends to fix a lot of issues regarding undetected hardware, it would be best to found an alternative way to get that system online somehow.

---


---
title: "Need help (new to linux) - interface not found"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by rma88 on 2007-05-19
Hey all, I've been reading and doing the how to's with the wireless 3945, download the driver ipw3945, the source, install all those updates and what not trying to get the network manager to detect my wireless...but it still doesn't. Now I'm starting to wonder if it's because im getting the wrong drivers and stuff, how do I find out what driver or number I'm using ( i.e. 3945 ) - maybe I've been fixing a problem the wrong way the whole time :(. I just installed Ubuntu and could really, really use some help. I'm using a Dell XPS M1210 w/ the 802.11N wireless card if that help.
Any help is greatly appreciated, I'm at a standstill.


i just did an lshw and here is what it said ( if this helps ) :
---edited out above---
 *-network UNCLAIMED
     description : Network controller
     product: Broadcom Corporation
     vendor: Broadcom Corporation
     physical id : 0
     bus info : pci@0c:00.0
     version : 01
     width : 64 bits
     clock : 33MHz
     capabilities : bus_master_cap_list
     configutation:  latency=0           <--------------- i don't have a driver=ipw3945 here or w/e my driver is ( i don't know )
     resources: iomemory:ecf...etc
---edited out below---
hope that helps

one last thing, this might help - this is my wireless card as it appears on the sheet when i bought the computer:
Dell Wireless 1500,Minicard US,for XPS M1210

---

### Post by rma88 on 2007-05-19
okay, i think i'm making progress...i found the driver that i need for the wireless card, intalled it to C:\dell\drivers  in windows and then in ubuntu did the ndiswrapper -i [directory] - and it acted like it worked.

when i do ndisrapper -l it says:
autorun: invalid driver!
bcmwl5: driver installed
              device (14E4:4328) present

so the driver is isntalled...but autorun is having issues it looks like... hope that can help someone help me :\

---


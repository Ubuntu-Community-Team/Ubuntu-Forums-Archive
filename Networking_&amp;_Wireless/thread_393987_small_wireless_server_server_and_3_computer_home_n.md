---
title: "small wireless server server and 3 computer home network"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by elemosynary on 2007-03-26
I need to upgrade my home wireless network to use a wireless server for file storage and sharing instead of a primary desk top as the server.  Three comps are involved + a laptop.  I hope somebody can give me set up and equipment advice.  I now use a simple Linksys WRT54G setup, but I dont like the idea of energizing the primary comp to get  and share info for comps in other locations.  TIA

---

### Post by chili555 on 2007-03-26
Is this a mixed network? Linux and Windows and/or Mac? I may have more recommendations once I know.

I have an old Pentium III 733 Mhz running headless in the garage with wireless. It runs 24/7 (it also runs Folding@Home). At a minimum, you need a motherboard, processor and heatsink/fan, RAM, a video card, a big harddrive and a CD drive to install with. I keep an old CD drive in the closet to install with and then I remove it when I'm done.

Set the BIOS to halt on no errors and to restart if power is lost and resumes. Set it up with sshd running and with a static IP address so you can find it later. Shut it down with sudo telinit 0 and take it to wherever will be your server room, In my case, the garage next to the motor oil and rags.

If you have done your job right, it will magically start when you plug it in. You should then be able to ssh -l chili 192.168.1.101 (or whatever your details are) and get a prompt on your rusty old server.

---


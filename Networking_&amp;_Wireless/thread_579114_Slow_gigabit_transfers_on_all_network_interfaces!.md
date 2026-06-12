---
title: "Slow gigabit transfers on all network interfaces!"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by touser on 2007-10-18
Hello everyone, i am running the latest release of gutsy, previously feisty which had the exact same problem. On my system transferring over samba, nfs, or scp in both feisty and gutsy i am getting a maximum transfer rate of 9MB/s over my network. This is with both of my onboard gigabit nics (Nvidia CK804, Marvel 88E8001) and my pci nic (Intel pro/1000 mt) all cards are gigabit. When i reboot into windows i get 45MB/s+ transfer speeds over samba from the same server (server running debian etch) on all interfaces so this is an OS issue and not hardware. I have searched the forums and come up empty handed every time. Any help would be greatly appreciated as sub 100mbit speeds arent working very well on my main computer.

---

### Post by Mcavity on 2007-11-13
I have the same problem. Im looking for a fix myself.
i noticed things are much better when i swaped down to a 10/100 card. but thats not a solution.

---

### Post by AlanR8 on 2007-11-13
9 MPS would be good, most common is less than 2

---

### Post by Mcavity on 2007-11-13
yea i get about 3 if I'm sending a file to an xp and less than 1 if I'm pulling a file from an XP box. 

this might help you... but its not working for me.. [different nic that wont show up with ethtool]
I think my problem is related to that,
[http://www.busybuddha.org/blog/anil/entry/notes_on_gigabit_ethernet_ubuntu](http://www.busybuddha.org/blog/anil/entry/notes_on_gigabit_ethernet_ubuntu)

---

### Post by Mcavity on 2007-11-16
Well I think theres  aproblem with autonegotioation.
I switched to difrent gigabit chipset card. some of my problems cleared up but my transfer rate seems to be stuck at 100 base rather than 1000

---


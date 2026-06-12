---
title: "static ip (wired) worked fine at work, not at home can't use dhcp"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by JoePits on 2007-05-30
I installed ubuntu feisty on my dell e1505 (aka inspiron 6400) and was using it at work with the usual static ip settings we use on windows.  then i came home and plugged it into my switch and i can't get online.

all i changed was the system/administrator/network thing i changed from static ip to dhcp.  didnt touch anything else.

i dont remember what command i did but i read it on here in another thread and it said something like "no dhcp leases received"  is that a problem with road runner maybe?  i thought at first it was too many IP addresses for my RR account so i took out the other ones and tried putting my laptop directly to my cable modem, but it still didnt work.  

the network, sometimes says it connects, then it disconnects a few seconds later.  also in the network information the ip address is 0.0.0.0 (all the values are).

i need to get it on the wired lan so i can get the next-gen wireless driver set up and then use wireless.  none of the cd burners on my other computers work and the next-gen driver isn't on the dell cd, (i also dont think ndiswrapper came with my ubuntu install).

---

### Post by JoePits on 2007-05-30
ok i got the wired working by doing the blah networking restart thing after i unplugged the cable modem.  

but now i put the next-gen INF into windows wireless and it doesn't show up but it says i ts installed.  all it does it close right away when i open it now.  rebooted didnt help.  reinstalled windows wireless with synaptic still it closes upon starting.

---


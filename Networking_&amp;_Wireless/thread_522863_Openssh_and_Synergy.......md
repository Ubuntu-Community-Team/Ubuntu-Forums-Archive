---
title: "Openssh and Synergy......"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by effec on 2007-08-11
I'm trying to get synergy working via ssh to my windows machine. The windows machine is setup as the server right now with cygwin+openssh. I was able to start the ssh, login to ssh via the terminal from my ubuntu machine and even see my files, but i want to be sure synergy is running with ssh. Thing is, Synergyc on my ubuntu client automatically logs once the synergy server starts on the windows server pc.

So im not logging on with : 

ssh -f -N -L 24800:server-hostname:24800 server-hostname

it just automatically connects as it always has....

 How can i make sure its connecting  securely?

I dont see synergy in my startup programs nor did i setup auto start myself. I just downloaded it off of the package manager.

---


---
title: "Can't see network shares anymore"
date: 2005-06-06
forum: Networking &amp; Wireless
---

### Post by bleakcabal on 2005-06-06
Hi, I first installed Ubuntu yesterday. I could see and access the share folder of another Windows PC on my network.

Unfortuntly I broke my install while trying to make my ATI drivers work.

This morning I reinstalled again. I installed Samba from Synaptic so that I could Share a folder. 

Then I check at the network and I can't see the Windows PC share like I did yesterday !

Could installing Samba have broken this ?

---

### Post by netrattler on 2005-06-06
Have you tried accessing the network share by the ip address like this for an example 
smb://192.168.0.15/recordings. I'm also gussing that you already setup samba users with smbpasswd -a username. Post a copy of your /etc/samba/smb.conf file and I'll see if I can't find anything wrong with it.

Joe

---


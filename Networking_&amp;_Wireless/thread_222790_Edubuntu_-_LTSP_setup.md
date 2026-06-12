---
title: "Edubuntu - LTSP setup"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by OMRebel on 2006-07-25
I am setting up a Edubuntu server for a school lab at my hospital.  The server has two NIC's in it (ETH0, ETH1).  I want to use one for the lab network that the thin clients will be booting off of.  I want to use another to connect to the outside network for supplying Internet access to the clients.

Can someone tell me how to set this up?  Thanks.

---

### Post by OMRebel on 2006-07-25
I have been working for hours just trying to get LTSP to work.  I am using a server that I had K12 on, and it worked perfectly.  Edubuntu though...it's not loading the pxelinux.o  Saying not a valid image.  Has anyone actually got a setup like this to work?

---

### Post by OMRebel on 2006-07-25
Loading 192.168.0.1:/ltsp/pxelinux.0 ..error: not a valid image
Unable to load file

---

### Post by OMRebel on 2006-07-26
Anybody have any suggestions?

---

### Post by OMRebel on 2006-07-26
I got it solved.  For some reason, the boot ROM that I was using that worked with K12 wouldn't work for Edubuntu.  So, I regenerated a ROM according to the instructions at:
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe](https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe)

I was then able to start up the client just fine.

---

### Post by jediborger on 2006-08-26
I set up my server as per the wiki UbuntuLTSP and I got a boot rom from fom-o-matic cut it just sits at

Loading 192.168.0.1:/ltsp/pxelinux.0 . . . . . . . .

and does nothing more, can anyone help me with why it's doing this and what exactly is supposed to happen when you do a client boot.

---

### Post by jediborger on 2006-08-27
Well with some more tweaking I figured out the problem. First it was stalling becase Firestarter firewall was blocking it so I added a rule to allows connections from 192.168.0.250 (you can look under the events tab to view what it blocked) Once I got that done it booted but gdm x failed to start and I couldn't log in under the tty. I solved that by reloading the ssh keys by

sudo ltsp-update-sshkeys

My client now works flawlessly with the users I set up.

---


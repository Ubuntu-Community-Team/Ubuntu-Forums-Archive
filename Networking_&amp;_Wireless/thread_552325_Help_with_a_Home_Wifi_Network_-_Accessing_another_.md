---
title: "Help with a Home Wifi Network - Accessing another ubuntu PC"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by stepluvx on 2007-09-16
I set up a Ubuntu PC for my son shortly after 6.10 was released, his desktop uses a d-link wifi card to access our home network. All Ubuntu boxes in my house have been upgraded to 7.04 and even though danguardian is installed on his computer, it can only do so much. Anyway I've been reading up on SSH & VNC and I would like to be able to remotely look at what he is doing on his PC (emails, IM's, web surfing, etc.) periodically just to make sure he's not doing anything inappropriate.
Would SSH allow me to view his desktop & active windows remotely from in my network or is their something else that what I'm trying to do? Both machines are running Ubuntu Feisty & I of course have admin rights to all machines.

---

### Post by spd106 on 2007-09-18
This help docs page is quite thorough [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

You don't necessarily need to use ssh to connect as you will only be on a local network, it is more important to encrypt the connect when you are using it over the Internet or another other public network.

You can set up a simple remote desktop in the System -> Preferences -> Remote Desktop utility, it just doesn't have particularly advanced options compared to other applications.

---


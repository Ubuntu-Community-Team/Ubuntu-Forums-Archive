---
title: "wireless DHCP error?"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by thunkt on 2007-03-27
Hi all,

I just went out and bought myself a WRT54GL router to get my notebook up and going on my home network again, using a d-link dwl-650+ pcmcia card. 

For some reason, using network-manager, the notebook can see the network, but simply can't connect to it. I've disabled wireless encryption, so I know it's not a security problem. 

If I configure my wireless card manually, with a static ip, it can connect. The problem only seems to exist when attempting to receive a dynamic ip address from the router.

The router is assigning DHCP addresses to my two wired desktop pc's, it's only on the wireless link that I have an issue. 

Any help would be greatly appreciated.

---

### Post by thunkt on 2007-03-28
Is this an already beaten-to-death question? I apologise if I'm adding to what is already an obviously congested forum, but I've spent hours upon hours trawling google, ubuntu forums, dd-wrt forums, etc looking for an answer.

Thanks again.

---

### Post by Mr. C. on 2007-03-28
Do you have a wired connection as well?  If so, disable it in network manager.

MrC

---

### Post by thunkt on 2007-03-28
Sorry, I forgot to mention that in my post. I had disabled eth0 via 
#sudo ifconfig eth0 down

It still doesn't help with the problem. 

On further testing, I can use dhcp if I connect by manually editing my /etc/network/interfaces to include the essid name. So it probably isn't a dhcp problem after all. Furthermore, wifi radar seems to work, however, I was hoping to get network-manager going as it supports wpa, which I intend to use once everything is peachy.

As always, I really appreciate the help.

Cheers

---

### Post by Mr. C. on 2007-03-28
Ok, good.  So you have only one interface in use.

DHCP cannot occur until the card has associated with the A/P.

Have you reviewed: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)  ?

MrC

---

### Post by thunkt on 2007-03-28
That's interesting,

Thanks for the link. Forgive me if I'm wrong, about to head to work, and only had time for a cursory glance, but from what you mentioned, and this howto, it basically requires all my AP info in my /etc/network/interfaces file? 

I was hoping for something a little more adaptable for using hotspots in town etc.
I can get networking going via both DHCP and static IP, as long I tell /etc/network/interfaces my essid name. I was hoping only to do this as a plug, until I could find out how to get network-manager or wifi radar to automate the process for me whilst out and about.

Without telling my /etc/network/interface file the name of my essid, network-manager still manages to find the network, when I load it up, however, it can't connect to it.

Cheers

---


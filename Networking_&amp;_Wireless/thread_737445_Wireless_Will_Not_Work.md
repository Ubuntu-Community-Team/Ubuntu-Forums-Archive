---
title: "Wireless Will Not Work"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by apolloxi on 2008-03-27
For some reason, my wireless does not work at all. Ubuntu acknowledges my wireless card, but I cannot detect ANY wireless networks.

I'm using Ubuntu 7.04, and my wireless card is Broadcom ( BCM4318 ). I did the "sudo lshw -C network" command to see "network: 1 DISABLED."

I tried researching this problem, and it seems I either need to somehow activate it (which I don't know how do to, since I found nothing on it), install bcm43xx-fwcutter (which keeps failing on me when I try to download it from the Synaptic Package Manager), or use ndiswrapper (which sounds very complicated and scary, so I wanna look for easier solutions first).

Can anyone help me? Was any of my proposed solutions even close? How do I fix this?

---

### Post by kingqw on 2008-03-27
Hmm.....im sort of a newbie here, but would "ifup (Internet Name Here){such as "eth0"} " not bring it up?

---

### Post by apolloxi on 2008-03-27
What exactly should I put in "Internet Name Here"?

---

### Post by kingqw on 2008-03-27
when you go "IFconfig" it should come up with your wireless networks (or iwconfig)

so you take your wireless internet name (say, eth0) and go

"ifup eth0"

if its up already, it will say already configured, and if not, it should work (i think)

---

### Post by apolloxi on 2008-03-27
I tried "sudo ifup eth1" (eth0 is already configured...I guess that's my wireless).

It says "Ignoring unknown interface eth1=eth1"

Don't know what this means.

---

### Post by kingqw on 2008-03-27
Have you tried googling the error?

---

### Post by apolloxi on 2008-03-27
Just did.

Found this on a website:

> If the final logical interface name is the label of a logical interface definition in /etc/network/interfaces then the physical interface is brought up as that logical interface. Otherwise ifup prints a message that it is "Ignoring unknown interface" and exits.

Basically, I think this means that "eth1" is not in /etc/network/interfaces, and, because it isn't, ifup is ignoring it.

So, should I just add it in interfaces, manually? If I should, then how?

EDIT - NEWER UPDATE

Okay. So, for the hell of it, I tried adding eth1, typing in "iface eth1 inet dhcp," just so it would look like eth0.

This time, "sudo ifup eth1" actually executed, but all the packets sent to it fail, and is still disabled afterwards.

---

### Post by donmor on 2008-03-27
Would you know how to enable lo and also the eth0 and eth1.
All say the same.  'no wireless extensions'

Thanks
Don

---

### Post by apolloxi on 2008-03-28
Anyone?

---

### Post by heyho on 2008-03-28
Hi,

I too have had similar problems to yourself, ie a broadcom chipset in my wireless card.  Having initially managed to get it up and running using ndiswrapper, it worked ok unit I did a fresh install of xubuntu - it still worked - this time with fwcutter, however it always seems to want some attention every time it is used.

Have you searched the forum for issues with broadcom cards?  It must account for a good deal of the traffic here.

Being that at the moment, I am trying various linux flavours on this particular machine, and that the rest of my Family will lose faith if it never works properly, I did the decent thing and replaced the card with a fully suppored Comtrend Ralink based card - hey presto - an immediate wirless connection with no messing about.  Well worth the £10 spent.  You don't say what your hardware is, but it should be possible to replace your card.

[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)

Gives you a good idea of compatible cards.  It may seem a little defeatist, but it saves a load of hassle.

---


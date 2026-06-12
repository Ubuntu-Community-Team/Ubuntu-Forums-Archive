---
title: "[SOLVED] KNetworkManager manual config issue"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by Dexter Saint Jock on 2008-06-28
Been using Ubuntu on my desktop since January and I love it. I am curious about Kubuntu so I wiped my laptop and installed it.

It is an HP Pavilion 5330us with a Broadcom wireless chipset. Yeah!!!    Using fwcutter and the restricted driver manager I was able to get the wireless to recognize the local networks.

I would enter the key to my network but it would not accept it. I tried to manually configure the connection but this did not work either. Now I cannot get rid of the manual config icon or see a list of available networks.

My question is how do I go about returning KNetworkManager to default state where I can enter my key but choose different encryption type? I have not made any other changes to the clean install.

I'm trying to be as specific as possible but I am still pretty new to all of this and am not sure what info is needed to help.

By the way, you guys ROCK!!  :guitar:   The search function is my friend.  :lolflag:  But it has not helped me much in this case.


TIA

---

### Post by Dexter Saint Jock on 2008-06-29
I did manage to get online using the manual config but I did not manage view a list of available networks. I chose hexidecimal encoding for my wep key. Worked like a charm.

But it's kind-of a moot point...I am going to try a different distro. Gonna stick with Ubuntu on my desktop but will try something a little different on my laptop.


D

---

### Post by daemonfly on 2008-06-30
I have a older Dell with a problematic Broadcom card (BCM4306). Xubuntu's NetworkManager doesn't play nice with it frequently have to manually select/enable the networks I connect to, over & over.

Gonna try out WICD as it's supposedly known to work better with the problematic Broadcom cards. Can't do it right this moment, as I'm at work, but as soon as I get home, I'm gonna give it a shot. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It's not really the distro itself that is the issue, just a select piece of software that doesn't work well with these cards.

---


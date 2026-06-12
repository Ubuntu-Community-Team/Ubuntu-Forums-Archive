---
title: "Default firewall"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by gtemedtk1 on 2007-11-13
I saw this on Distrowatch and thought it would be a good thing to include just in case someone can or would want to address it:

"It still concerns me when distributions, such as Ubuntu, still ship without a firewall or even a security framework such as SELinux, or AppArmor installed by default."     mailto:simonedice-at-gmail-dot-com (author)

I hope this is added to Hardy Heron when it is released next year.

Gordon Eldridge

---

### Post by erginemr on 2007-11-13
Hello,

If you are looking for a good firewall, you can install "firestarter" with:
sudo aptitude install firestarter

It is a front end to IPTables, the firewall already available under Ubuntu but not active by default. It is a "run once and forget" type of program.

If you already know about it, but posted just to draw the attention of people to the general need for a default firewall under Ubuntu distros, then please do not heed my post.

(P.S. Ubuntu developers were planning to add AppArmor into Gutsy Gibbon. But I don't know neither if hhey have included in it, not what exactly it is for.)

---

### Post by az on 2007-11-13
You don't need a firewall on a desktop.


In Ubuntu, the default installation does not include anything that listens to the network.  If you are going to install anything that does, you would "'open those ports" anyway.

---

### Post by ahman_ra on 2007-11-13
i am a paranoid freak, so i disagree with that one.  firewall on a desktop that is by itself, hence, not on a network, may get by without a firewall, as long as there is a router with a firewall playing goalie on the path to the internet.

if there are 2 or more desktops in a network, i find "double bagging" it to be a good thing as one can become infected, but the other able to dodge it, if your lucky.

---

### Post by az on 2007-11-13
> **ahman_ra said:**
> i am a paranoid freak, so i disagree with that one.  firewall on a desktop that is by itself, hence, not on a network, may get by without a firewall, as long as there is a router with a firewall playing goalie on the path to the internet.

if there are 2 or more desktops in a network, i find "double bagging" it to be a good thing as one can become infected, but the other able to dodge it, if your lucky.

No.  You can be connected to the net 24/7 with no firewall.  If there is nothing listening to the network, there is nothing listening to the network - regardless of whether there is a firewall or not.  And whenever you need your computer to talk to the net, you are going to open up your firewall anyway.  There simply is no use on  a desktop for that.

---


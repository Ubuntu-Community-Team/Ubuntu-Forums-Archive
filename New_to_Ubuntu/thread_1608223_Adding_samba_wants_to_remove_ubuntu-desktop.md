---
title: "Adding samba wants to remove ubuntu-desktop"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by oregonbob on 2010-10-28
If I go into Synaptic and just try to add Samba, it tells me it wants to REMOVE the entire ubuntu-desktop! I knew something was wrong with package management. What is going on?

Actually I picked "samba" and "samba4-clients" packages, but regardless samba4-clients shoudn't remove entire Gnome desktop! I canceled and went back in, selected only "samba" and it installed without removing gnome. This was on a fresh new install of 10.04.

---

### Post by coffeecat on 2010-10-28
The meta-package ubuntu-desktop is not the entire gnome desktop - it is just that, a metapackage. If you remove it you remove nothing of gnome, but it's not a good idea to remove it because it is needed to keep the Ubuntu version of the gnome desktop up-to-date.

I guess the reason that samba4-clients wanted to take out ubuntu-desktop is that, being the next generation, it is incompatible with some aspects of the version of gnome you are running.

So there is nothing wrong with package management. Quite the reverse!

**Edit:** I'm posting from what passes for Natty Narwhal at the moment. That is a Maverick upgraded with the Natty repositories in sources.list. Marking samba4-clients for installation didn't prompt to have ubuntu-desktop removed, only smbclient, which makes sense. So this is most probably a gnome version incompatibility thing.

---

### Post by oregonbob on 2010-10-28
But I was watching closely this time due to this happening to me on two other desktops within the past month. Other users reported similar. I guess I'll build a virtual machine and test it on that. On those others, it removed gnome, X, all networking and much more. It seems to have a dependency-removal problem. It sure has me spooked. I am not an Ubuntu noob. I've been using Ubuntu since 7.1 around three years ago. I've added many packages on different machines and never observed that behavior.

---

### Post by coffeecat on 2010-10-28
I'll have to log off in a moment - late here - but one question. I'll read your answer tomorrow. When it said it wanted to remove ubuntu-desktop, was it just ubuntu-desktop or ubuntu-desktop with a load of other stuff? Taking out X and networking on your other machines does sound drastic. A bit ironic too - samba taking out networking. :?

I guess it just isn't compatible with Lucid's GUI. The only reason I can think of for it being in Lucid's repo is for people who want to try it with a GUI-less server. I don't know. It's late here and I'm beginning to ramble.

---


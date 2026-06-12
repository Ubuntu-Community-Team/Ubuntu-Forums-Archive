---
title: "Difficulty of Networking In All OSes(including legacy versions)??"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by 13k on 2010-08-21
Hello, i don't know alot of computer stuff, or if this is the most appropriate place to ask but... Say for instance, me, my friend, whoever you want it to be... wants to get a job networking... Is SETTING UP a NETWORK in (lets say) Ubuntu different to set up than Fedora(or any other distro)?? ... Or is it different to set up a network compared to Windows, Macs? ~~And 1 last thing... Is setting up a network different to set up from the legacy editions to the latest versions of Windows??

---

### Post by earthpigg on 2010-08-21
fedora vs ubuntu vs _______: no, same stuff. package names may be different and the package manager will be a bit different, but that is very trivial. there may be different versions of a given piece of software. for example, ubuntu 10.04 came out in the 4th month of 2010. maybe the latest release of fedora came out last week. the latest version of fedora might then contain a newer version of a piece of given software. 

but, in general:
ifconfig is ifconfig, and nm-applet is nm-applet. a package manager is a package manager, and cups (common unix printing system) is cups. 

there are all sorts of hybrid LANs out there with several different distributions, all networked together and living happily. until recently, wikipedia's server infrastructure was like that.

I'm of the opinion that the apt vs rpm vs pacman vs ____ debates are splitting hairs -- they all work amazingly well, and once you can use one it only takes a few minutes to learn another. there's even a chart somewhere out there that does a great job of "translating" the command line arguments and whatnot.

I've read Arch Linux networking documentation and applied it to Ubuntu, and I peruse Red Hat & Debian documentation on a regular basis to learn stuff I only intend to apply on Ubuntu. The official Ubuntu wiki is pretty crummy, but that's because there is no need for it to be great so long as we can all read documentation for other distributions & easily apply it.

> Or is it different to set up a network compared to Windows, ***Macs***?

OS X networking stuff is closer to the same family as *BSD or other more traditional Unix distributions. any Linux distribution you can name uses GNU tools for networking, OS X uses BSD tools for networking. Distant cousins, but still the same family. Windows is the pink elephant here, really, as it's networking tools are an entirely alien species.

> Is setting up a network different to set up from the legacy editions to the latest versions of Windows??

yes. microsoft intentionally limits what features are in which versions of windows so they can push their 'professional' editions. so, a given feature may be in all versions of win7, but only in xp pro.

i've never really tried to do any sort of hybrid win/lin network, but my understanding is that Linux servers can serve windows clients much better than the other way around.

---

### Post by 13k on 2010-08-21
> **earthpigg said:**
> fedora vs ubuntu vs _______: no, same stuff. package names may be different and the package manager will be a bit different, but that is very trivial. there may be different versions of a given piece of software. for example, ubuntu 10.04 came out in the 4th month of 2010. maybe the latest release of fedora came out last week. the latest version of fedora might then contain a newer version of a piece of given software. 

but, in general:
ifconfig is ifconfig, and nm-applet is nm-applet. a package manager is a package manager, and cups (common unix printing system) is cups. 

there are all sorts of hybrid LANs out there with several different distributions, all networked together and living happily. until recently, wikipedia's server infrastructure was like that.

I'm of the opinion that the apt vs rpm vs pacman vs ____ debates are splitting hairs -- they all work amazingly well, and once you can use one it only takes a few minutes to learn another. there's even a chart somewhere out there that does a great job of &quot;translating&quot; the command line arguments and whatnot.

I've read Arch Linux networking documentation and applied it to Ubuntu, and I peruse Red Hat & Debian documentation on a regular basis to learn stuff I only intend to apply on Ubuntu. The official Ubuntu wiki is pretty crummy, but that's because there is no need for it to be great so long as we can all read documentation for other distributions & easily apply it.



OS X networking stuff is closer to the same family as *BSD or other more traditional Unix distributions. any Linux distribution you can name uses GNU tools for networking, OS X uses BSD tools for networking. Distant cousins, but still the same family. Windows is the pink elephant here, really, as it's networking tools are an entirely alien species.



yes. microsoft intentionally limits what features are in which versions of windows so they can push their 'professional' editions. so, a given feature may be in all versions of win7, but only in xp pro.

i've never really tried to do any sort of hybrid win/lin network, but my understanding is that Linux servers can serve windows clients much better than the other way around.

 I read all of it, very well detailed :P and i thank you for that... =( and telling by all this info, i'm so screwed if i get this sort of job -.-

---

### Post by earthpigg on 2010-08-21
> **13k said:**
> I read all of it, very well detailed :P and i thank you for that... =( and telling by all this info, i'm so screwed if i get this sort of job -.-

why do you say that? linux networking is probably some of the best documented stuff on the planet.

---

### Post by matchett808 on 2010-08-21
Networking is networking, client/server, token ring ad hoc , wep etc is os-independant, learning the neuances of each os would be the caveat...

tl;dr: yeah what the other guy said basicly

---

### Post by 13k on 2010-08-22
> **earthpigg said:**
> why do you say that? linux networking is probably some of the best documented stuff on the planet.

 if you don't know where or how to access the documents = me getting screwed all over, and getting fired faster than you can say, GOOD FIGHT.

---

### Post by earthpigg on 2010-08-22
> **13k said:**
> if you don't know where or how to access the documents = me getting screwed all over, and getting fired faster than you can say, GOOD FIGHT.

google for everything.

---

### Post by cariboo on 2010-08-22
As the others have stated, networking is networking, it doesn't matter what OS you are using. A good place to start is [The Linux Documentation Project]("http://tldp.org/"). Have a look at the networking howto.

---


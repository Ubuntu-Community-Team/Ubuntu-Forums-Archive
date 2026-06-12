---
title: "Real Netgear MA521 (rtl8180) problems"
date: 2005-11-24
forum: Networking &amp; Wireless
---

### Post by kukerdan on 2005-11-24
Hi, im a linux newbie, and yes i've read many posts about getting this to work on ubuntu, but none of them seem to take my issue into account

im trying to install this onto a laptop in which the wireless card is the only newwork connection present, aka i cant have linux download packages or any of that other neat stuff

I have this computer that i can use to burn CD's and transfer them  back and forth

i assume ubuntu doesnt come with the stuff it needs to compile anything
because after trying to make install    on ndiswrpper, it tells me theres no kernal source, and upon further inspection i found that directory isnt even there

(/lib/modlues/2.6.../build


aany help? how can i get this working

---

### Post by cwaldbieser on 2005-11-25
[QUOTE=kukerdan]Hi, im a linux newbie, and yes i've read many posts about getting this to work on ubuntu, but none of them seem to take my issue into account

im trying to install this onto a laptop in which the wireless card is the only newwork connection present, aka i cant have linux download packages or any of that other neat stuff

I have this computer that i can use to burn CD's and transfer them  back and forth

i assume ubuntu doesnt come with the stuff it needs to compile anything
because after trying to make install    on ndiswrpper, it tells me theres no kernal source, and upon further inspection i found that directory isnt even there

(/lib/modlues/2.6.../build


aany help? how can i get this working[/QUOTE]

Yeah, it can be a chore to build your network drivers when you can't connect to the Internet.

The way I did it was to look up what packages I needed to get and then manually download the .deb files.  They can be installed with dpkg.

The following site will help you look up the packages and dependencies you need.  This kind of exercise really makes you appreciate apt-get and synaptic!

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

If you need more help, let us know.

---


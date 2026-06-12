---
title: "Fatal Error installing modprobe for netgear wg511"
date: 2005-05-15
forum: Networking &amp; Wireless
---

### Post by kozmo on 2005-05-15
I folowed the instruction in the wiki Setup [SetupNdisHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto) 

I get no errors, but when I run **ndiswrapper -l** it displays:
netwg11 invalid drivers!
or
wg511v2 invalid drivers!

And wireless lan does not display under Admin.

Anyone know how to get these to play with Ubuntu???

---

### Post by Staesys on 2005-05-16
Do you have the .inf file for your card? Usually that command is something like this:

**ndiswrapper -i bcmw5.inf** 

...and should be run as root in the same directory as the .inf file.

---

### Post by kozmo on 2005-05-16
Finally got it working!!! Wireless Netgear WG511 is up and running on my laptop!!!

Don't know what I did wrong.

But I re-installed Ubuntu 5.0.4 Hoarty

Then I followed the instructions in the Official Wiki (a 2nd time) [NdiswrapperHowTo](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

Viola! I'm up and running! :)

---

### Post by CAPTAIN RON FL on 2005-05-17
Which card do you have. 

I am having troubles with  mine . I have a Netgear WG511 and have been trying to get this to work on my Toshiba laptop for a while now. 

Aloha, Ron

---

### Post by mrguytx on 2005-06-29
Try uninstalling ndiswrapper and getting the latest v1.2 of ndiswrapper.
That fixed my WG511 issue. Took me hours and hours of failure before I noticed there was a newer version than the one apt-get installs.

---


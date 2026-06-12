---
title: "trouble installing D-Link WDA 1320 Please Help"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by lugnut_9754 on 2007-06-11
Hi. I recently bought a D-Link WDA 1320 and I've been having problems installing it. I'm new at linux but most of the time can get things to work fine. I am using Ubuntu Feisty. How can I install this? I tries using wine to install using the disk the network card came with but it doesn't work. Is there a something I can type in the terminal to get it to work? I've looked at other posts for this card and people seem to have no problems when they install it when they first install ubuntu but I don't really want to re-install ubuntu. Please Help. Thanks.

---

### Post by kevdog on 2007-06-11
Ive never helped anyone with this card, but I can try.  Please post the results of:

lspci
lspci -n

Then hopefully I can help you.  Do you have another computer along the USB stick so you can download some files or a working internet wired connection on the machine.

---

### Post by lugnut_9754 on 2007-06-11
unfortunetly i have no other computers or a wired connection as i am renting a room in a house that has wireless. right now I am at my university using their internet to try to find solutions so i could not post the things you asked me to. thanks for trying to help though.

---

### Post by kevdog on 2007-06-11
Ive done some more researching.  I hope you are not too new with computers.  You need to install the madwifi driver package.  You will definitely need however a working internet connection somewhere to download some files.

Here is the link:
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

---


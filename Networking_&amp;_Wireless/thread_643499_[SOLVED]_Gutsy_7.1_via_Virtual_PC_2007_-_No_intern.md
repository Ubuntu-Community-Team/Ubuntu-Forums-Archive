---
title: "[SOLVED] Gutsy 7.1 via Virtual PC 2007 - No internet"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by cadlewv on 2007-12-17
Hello. I have just installed Gutsy and cannot connect to the internet. I have gone into the Network settings, but 'wireless' is not an option, only wired and modem.  I am using a Netgear WG111v2 wireless USB adapter.  I don't -think- it's in the device manager, but can't really tell since it all seems Greek to me.

I was trying to get on the internet to solve my mouse problem (not working).

I apologize for probably asking a silly question. Thanks ahead for your help.

P.S.  I originally posted this in the Newby forum.  I thought that I was supposed to start there for all of my needs, until I found the network/wireless forum.  Apologies.
__________________

---

### Post by csat on 2007-12-17
You might find some interesting topics here:

[http://ubuntuforums.org/showthread.php?t=632651](http://ubuntuforums.org/showthread.php?t=632651)

---

### Post by cadlewv on 2007-12-17
Thanks for the link.

Ok.  I've gotten all the way down to where he tells me to link my MAC address to wlan0 by entering the command: sudo mousepad /etc/iftab.

When I do that, it returns a response of:

'sudo: mousepad: command not found'

I'm sure most people will know the answer to this, just not me.  A little more help?

Thank you.

---

### Post by cadlewv on 2007-12-18
Ok, I've got internet access via ethernet card (not wireless).

I still need to find out how to install mousepad.  With an internet connection, I thought I could get it via:  sudo apt-get install mousepad  but it keeps telling me it can't find it.

Also, how can I get my mouse (usb) to work?  Again, this is via Virtual PC 2007.

---

### Post by cadlewv on 2007-12-18
Ok, I've got mousepad installed, but I still can't get my wireless adapter to be recognized.

Any suggestions?

---

### Post by cadlewv on 2007-12-18
Not exactly solved.  I just removed it from Virtual PC and loaded Gutsy to a second partition on my hard drive.  Everything works fine for now.

---


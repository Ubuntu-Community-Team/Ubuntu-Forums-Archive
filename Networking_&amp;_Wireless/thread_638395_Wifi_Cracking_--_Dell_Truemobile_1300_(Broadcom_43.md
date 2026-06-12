---
title: "Wifi Cracking -- Dell Truemobile 1300 (Broadcom 4306)"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by sirgogo on 2007-12-12
Hello all:

My ubuntu laptop (Dell Inspiron 1000) has an external Dell Truemobile 1300 (Broadcom 4306... I believe) card. The card DOES work and I am able to connect to the internet through wireless networks. And I wanted to say, first off, that I am "nub" at wifi stuff, so please bear with me and provide me with specific commands to type in. :)

My question is concerning the wifi cracking ability of Ubuntu. I have searched through many, many, many sites for a simple run through of what to do with no avail. Either the site will be explicitly for an older version of Ubuntu, whereafter some commands in the terminal won't work, or the site won't tell me what to type into the terminal, as I am not familiar with these commands.
Clarifying my question: How do I crack wifi (WEP or WPA) using my Ubuntu laptop?

Also, what are the basic list of commands that control wifi?

I recently found that the following connects you to a network:
```
sudo iwconfig <device name> essid <network name>
```
```
sudo iwconfig <device name> key <wepkey>
```.

I've gotten quite a bit of jumbled info, so I'm not sure what all the other commands are, or what they can do, so I would really appreciate some help.

Thanks a lot guys.

---

### Post by NullHead on 2007-12-12
Usually I use network manager ...```
nm-applet
```and use that to connect to all of my networks. I have a laptop and a desktop with a broadcom card ... so if you have any driver issues please ask away ;)

---

### Post by NullHead on 2007-12-12
wait wait ... "***crack***"??? as in "*hack*"??? I didn't catch that the first time around. Hmm I don't know about hacking but you might just ask for a password if thats what you're wanting to do.:lolflag:

---

### Post by sirgogo on 2007-12-12
Hey,

Yeah, well the network manager works fine for me with all the drivers and everything. My question was concerning cracking (hacking... haha) the wifi. I can connect to my home wifi, but I wanted to know how to do it. Thanks.

---

### Post by NullHead on 2007-12-12
What do you mean by cracking? like cracking the password to the network? or hacking the password to gain access to the internet through the router?

---

### Post by sirgogo on 2007-12-12
Yeah. Cracking the password to the network so that I can use the internet. Isn't that the same as hacking the router to use the internet?

Both would be good, preferabbly the later if they are different.

---

### Post by NullHead on 2007-12-12
:lolflag: as near as I can tell I think they're the same it's just I want to be clear on what other people might call something. I'll list some tools that I know of but I'm not sure if they will do what you want. there is wireshark, etherape, aircrack-ng and airsnort .. I think the last two are what you want, but I've never hacked a wireless router before ;)

---

### Post by kevdog on 2007-12-12
See my signature about how to connect from the command line.  I dont know anything about  the cracking of passwords, etc.

---

### Post by K.Mandla on 2007-12-12
Temporarily closed for staff review.

Please remember that discussions involving breaking security measures may or may not fall outside the acceptable borders for forum discussion.

---


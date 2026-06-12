---
title: "I want networking and shared printing to work..."
date: 2005-05-16
forum: Networking &amp; Wireless
---

### Post by fordfan753 on 2005-05-16
OK, here's the problem, and yes, I realise there are probably a million and one guides out there, I'm not posting because I'm too lazy to look since I spent all today doing just that, I'm posting because I am hideously confused and a n00b at linux networking. Anyways, I recently finished my new computer :D, and I hooked it up to a simple switch based network to share internet, files, and a printer with an older Compaq. My compuer (amdinside) is the bigger, faster one with all the good files and a printer, I want to be able to access a few folders and the printer on the old computer (compaq650). Both computers are dual booted between Hoary and Win2k. I have file and print sharing working fine with both computers under Win2k, I got it all to work fine with compaq650 running windows, and amdinside running linux, but I'm stuck trying to get anything to work between the two when they're both using linux. They both have samba, and various other things I installed (and can't remember the names of). If i open Places > Network Servers on amdinside i see two things
1. AMDINSIDE (that's a good sign...I think)
2. Windows Network > home (my workgroup) > AMDINSIDE
But when I do it on the Compaq I only get
1. Windows Network
I'm thinking that this could be part of the problem, so, someone smart, please...what's the easiest way to add a server to Nautilus? If I type smb://amdinside into Nautilus I see my shared files, I just need to permanently add it as a server for all users.

OK, next, I'm not sure if I have to configure cups, I've looked at various "tutorials", and, well, I'm not a rocket scientist, I'm not a 1337 linux geek, I go to high school, and I'm Australian. (seeing the problem now? :P) I first tried linux around the middle of last year (mandrake 10.1 community), Ubuntu is my second distro, I used Warty for a while, and downloaded Hoary the day it came out, but I'm not a pro, so any replies will have to be relatively easy to understand, and please, don't flame me, I know I'm a bit of a n00b.

If I type smbclient -L amdinside into the compaq, then, I see a lot of info, and something about the printer connected to it. The printer is a Canon S200SPx, not great, but it prints. It's connected to amdinside via usb. It's using the S200 driver, so Ubuntu recognises it as S200, prints fine though, that's not the problem. The problem is that I can see the printer using the above command, but I have no idea how to properly set it up so I can print to it.

If you need more info just ask, if I don't reply I may be sleeping, emails are greatly appreciated. Any help, any at all, even if it doesn't solve the problem, is greatly appreciated, thanks in advance everyone, 
Darren

---

### Post by fordfan753 on 2005-05-17
Come on people please, someone must have some idea how to set up print sharing and be able to tell me in a n00b friendly way.

---

### Post by Xerampelinae on 2005-05-17
[QUOTE=fordfan753]Come on people please, someone must have some idea how to set up print sharing and be able to tell me in a n00b friendly way.[/QUOTE]
 On the machine with the printer connected

sudo /usr/share/cups/enable_browsing 1

Then on the other machines without printers, go to the printer control panel thing, and from a menu select enable network printers or something like that... sorry for the vagueness..

---

### Post by fordfan753 on 2005-05-17
Tried just then and it didn't seem to work the remote computer just can't see any printers...I don't know if the printer uses CUPS or something else, but I assume it does....how would I find out?

---

### Post by laue on 2005-05-18
[QUOTE=Xerampelinae]On the machine with the printer connected

sudo /usr/share/cups/enable_browsing 1

Then on the other machines without printers, go to the printer control panel thing, and from a menu select enable network printers or something like that... sorry for the vagueness..[/QUOTE]

THANK YOU A BUNCH Xerampelinae!!! Wacky ubuntu setting though  :-|

---

### Post by chaplanger on 2007-01-09
WOW!  This solution is so simple and yet works so effectively -- just one cavaet -- don't forget to turn on "Share Printers" in the Global Settings of System>Admin>Printing!

---

